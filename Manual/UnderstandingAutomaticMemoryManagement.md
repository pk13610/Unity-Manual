<!-- > 原文：[Understanding Automatic Memory Management](http://docs.unity3d.com/Manual/UnderstandingAutomaticMemoryManagement.html) -->

<!-- Unity Manual > Scripting > Scripting Overview > Understanding Automatic Memory Management -->
<!-- Unity 手册 <i class="fa fa-angle-right"/> 脚本 <i class="fa fa-angle-right"/> 脚本概述 <i class="fa fa-angle-right"/> 理解自动内存管理 -->

<!-- # Understanding Automatic Memory Management -->
# 理解自动内存管理

<!-- When an object, string or array is created, the memory required to store it is allocated from a central pool called the **heap**. When the item is no longer in use, the memory it once occupied can be reclaimed and used for something else. In the past, it was typically up to the programmer to allocate and release these blocks of heap memory explicitly with the appropriate function calls. Nowadays, runtime systems like Unity’s Mono engine manage memory for you automatically. Automatic memory management requires less coding effort than explicit allocation/release and greatly reduces the potential for memory leakage (the situation where memory is allocated but never subsequently released). -->
当创建一个对象、字符串或数组时，会从名为 **堆** 的中央池中分配一块内存，用来所存储创建的值。当这些值不再被使用时，被占用的内存可以被回收，并用于存储其他的值。在过去，是由程序员显示地调用相应的函数分配和释放堆内存。如今，像 Unity Mono 引擎这样的运行时系统，可以自动地管理内容。相比显示地分配和释放内存，自动内存管理需要的编码工作更少，并且大大降低了发生内存泄露的可能性（例如，分配内存后一直不释放的情况）。

<!-- ## Value and Reference Types -->
## 值和引用类型

<!-- When a function is called, the values of its parameters are copied to an area of memory reserved for that specific call. Data types that occupy only a few bytes can be copied very quickly and easily. However, it is common for objects, strings and arrays to be much larger and it would be very inefficient if these types of data were copied on a regular basis. Fortunately, this is not necessary; the actual storage space for a large item is allocated from the heap and a small “pointer” value is used to remember its location. From then on, only the pointer need be copied during parameter passing. As long as the runtime system can locate the item identified by the pointer, a single copy of the data can be used as often as necessary. -->
当调用一个函数时，参数值被复制到一块专门用于本次调用的内存区。对于数据类型，它们只占用很少的字节，可以非常迅速和容易地复制。但是，常见的对象、字符串和数组则大得多，如果频繁地复制这些类型的数据，是非常低效的。幸运的是，没必要这么做；大型值的实际存储空间从堆分配，然后用一个小巧的『指针』值记录下它的存储位置。这样，在传递参数的过程中，只有这个指针被复制。既然运行时系统可以通过这个指针定位到实际的值，那么，在必要时可以使用它的副本。

<!-- Types that are stored directly and copied during parameter passing are called value types. These include integers, floats, booleans and Unity’s struct types (eg, Color and Vector3). Types that are allocated on the heap and then accessed via a pointer are called reference types, since the value stored in the variable merely “refers” to the real data. Examples of reference types include objects, strings and arrays. -->
在传递参数的过程中，直接存储和复制的类型称为『值类型』，包括整型、浮点型、布尔型和 Unity 的结构类型（例如 Color、Vector3）。在堆中存储、然后用一个指针访问的类型成为『引用类型』，因为存储在变量中的值只是『指向』了真实值。引用类型的例子包括对象、字符串和数组。

<!-- ## Allocation and Garbage Collection -->
## 分配和垃圾回收

<!-- The memory manager keeps track of areas in the heap that it knows to be unused. When a new block of memory is requested (say when an object is instantiated), the manager chooses an unused area from which to allocate the block and then removes the allocated memory from the known unused space. Subsequent requests are handled the same way until there is no free area large enough to allocate the required block size. It is highly unlikely at this point that all the memory allocated from the heap is still in use. A reference item on the heap can only be accessed as long as there are still reference variables that can locate it. If all references to a memory block are gone (ie, the reference variables have been reassigned or they are local variables that are now out of scope) then the memory it occupies can safely be reallocated. -->
内存管理器会一直跟踪堆的状态，知道哪些区域是闲置的。当请求一块新的内存区域时（意味着一个新对象被创建），管理器从闲置区域中选择一块，并从闲置区域中移除它。后续的请求被执行同样的处理，直到闲置区域不足以满足请求的尺寸。所有堆内存都被使用的可能性极小。堆上的引用类型只能通过引用变量访问，如果对某块内存区域的引用全都消失了（例如，引用变量被重新赋值，或者它们只是局部变量并且离开了作用域），那么这块内存区域可以被安全地重新分配。

<!-- To determine which heap blocks are no longer in use, the memory manager searches through all currently active reference variables and marks the blocks they refer to as “live”. At the end of the search, any space between the live blocks is considered empty by the memory manager and can be used for subsequent allocations. For obvious reasons, the process of locating and freeing up unused memory is known as garbage collection (or GC for short). -->
为了确定哪些区域不再被使用，内存管理器会遍历当前所有有效的引用变量，并把他们所引用的区域标记为『活动』。遍历结束后，未被标记为『活动』的区域都被内存管理器认为是闲置的，可以用于后续的分配。定位和释放内存的过程被直观地称为垃圾回收（简写为 GC）。

<!-- ## Optimization -->
## 优化

<!-- Garbage collection is automatic and invisible to the programmer but the collection process actually requires significant CPU time behind the scenes. When used correctly, automatic memory management will generally equal or beat manual allocation for overall performance. However, it is important for the programmer to avoid mistakes that will trigger the collector more often than necessary and introduce pauses in execution. -->
垃圾回收运行在后台，因此对于程序员来说是自动的、不可见的，但实际上，回收过程需要耗费相当的 CPU 时间。如果使用得当，自动内存管理的整体性能通常与手动分配相当或者更好。然后，程序员要注意避免频繁地触发不必要的回收，从而导致执行过程暂停。

<!-- There are some infamous algorithms that can be GC nightmares even though they seem innocent at first sight. Repeated string concatenation is a classic example: -->
有一些臭名昭著的算法堪称是 GC 噩梦，即使它们初看似乎没什么问题。一个典型的例子是字符串重复拼接：

```
//C# script example
using UnityEngine;
using System.Collections;

public class ExampleScript : MonoBehaviour {
    void ConcatExample(int[] intArray) {
        string line = intArray[0].ToString();
        
        for (i = 1; i < intArray.Length; i++) {
            line += ", " + intArray[i].ToString();
        }
        
        return line;
    }
}


//JS script example
function ConcatExample(intArray: int[]) {
    var line = intArray[0].ToString();
    
    for (i = 1; i < intArray.Length; i++) {
        line += ", " + intArray[i].ToString();
    }
    
    return line;
}
```

<!-- The key detail here is that the new pieces don’t get added to the string in place, one by one. What actually happens is that each time around the loop, the previous contents of the line variable become dead - a whole new string is allocated to contain the original piece plus the new part at the end. Since the string gets longer with increasing values of i, the amount of heap space being consumed also increases and so it is easy to use up hundreds of bytes of free heap space each time this function is called. If you need to concatenate many strings together then a much better option is the Mono library’s [System.Text.StringBuilder](http://msdn.microsoft.com/en-gb/library/system.text.stringbuilder.aspx) class. -->

这里的关键细节是，新片段并没有被添加到已有的字符串之后。事情的真相是，每执行一次循环，变量 line 的旧内容被丢弃，一个全新的字符串被创建，用来包含旧内容和新增部分。随着变量 i 的增加，字符串变得越来越长，消耗的堆空间也随之增长；每当这个函数被调用，就会用掉成百上千个字节的闲置堆空间。如果你需要拼接许多字符串，更好的选择是使用 Mono 库的 [System.Text.StringBuilder](http://msdn.microsoft.com/en-gb/library/system.text.stringbuilder.aspx) 类。

<!-- However, even repeated concatenation won’t cause too much trouble unless it is called frequently, and in Unity that usually implies the frame update. Something like: -->
不过，字符串反复拼接并不会造成太大的麻烦，除非你频繁地调用，而在 Unity 中，字符串拼接通常是为了帧更新，就像这样：

```
//C# script example
using UnityEngine;
using System.Collections;

public class ExampleScript : MonoBehaviour {
    public GUIText scoreBoard;
    public int score;
    
    void Update() {
        string scoreText = "Score: " + score.ToString();
        scoreBoard.text = scoreText;
    }
}


//JS script example
var scoreBoard: GUIText;
var score: int;

function Update() {
    var scoreText: String = "Score: " + score.ToString();
    scoreBoard.text = scoreText;
}
```

<!-- …will allocate new strings each time Update is called and generate a constant trickle of new garbage. Most of that can be saved by updating the text only when the score changes: -->
每次 Update 被调用，将分配一个新字符串，以恒定地速率产生新垃圾。通常我们可以这样优化这种情况：只有当比分更新时，才更新文本。

```
//C# script example
using UnityEngine;
using System.Collections;

public class ExampleScript : MonoBehaviour {
    public GUIText scoreBoard;
    public string scoreText;
    public int score;
    public int oldScore;
    
    void Update() {
        if (score != oldScore) {
            scoreText = "Score: " + score.ToString();
            scoreBoard.text = scoreText;
            oldScore = score;
        }
    }
}


//JS script example
var scoreBoard: GUIText;
var scoreText: String;
var score: int;
var oldScore: int;

function Update() {
    if (score != oldScore) {
        scoreText = "Score: " + score.ToString();
        scoreBoard.text = scoreText;
        oldScore = score;
    }
}
```

<!-- Another potential problem occurs when a function returns an array value: -->
当函数返回数组时，会引发另外一个潜在问题：

```c#
//C# script example
using UnityEngine;
using System.Collections;

public class ExampleScript : MonoBehaviour {
    float[] RandomList(int numElements) {
        var result = new float[numElements];
        
        for (int i = 0; i < numElements; i++) {
            result[i] = Random.value;
        }
        
        return result;
    }
}
```

```js
//JS script example
function RandomList(numElements: int) {
    var result = new float[numElements];
    
    for (i = 0; i < numElements; i++) {
        result[i] = Random.value;
    }
    
    return result;
}
```

<!-- This type of function is very elegant and convenient when creating a new array filled with values. However, if it is called repeatedly then fresh memory will be allocated each time. Since arrays can be very large, the free heap space could get used up rapidly, resulting in frequent garbage collections. One way to avoid this problem is to make use of the fact that an array is a reference type. An array passed into a function as a parameter can be modified within that function and the results will remain after the function returns. A function like the one above can often be replaced with something like: -->
这种函数创建了一个填满值的数组，看起来非常优雅和方便。但是，如果反复调用它，那么每次都会分配新的内存。因为数组可能非常大，所以闲置堆空间可能很快被用完，进而导致频繁的垃圾回收。避免这个问题的方式是，利用数组是引用类型这一事实。把数组作为参数传入函数，在函数内部修改这个数组，当函数返回后，数组中的值依然有效。上面的函数可以替换为下面这个：

```
//C# script example
using UnityEngine;
using System.Collections;

public class ExampleScript : MonoBehaviour {
    void RandomList(float[] arrayToFill) {
        for (int i = 0; i < arrayToFill.Length; i++) {
            arrayToFill[i] = Random.value;
        }
    }
}


//JS script example
function RandomList(arrayToFill: float[]) {
    for (i = 0; i < arrayToFill.Length; i++) {
        arrayToFill[i] = Random.value;
    }
}
```

<!-- This simply replaces the existing contents of the array with new values. Although this requires the initial allocation of the array to be done in the calling code (which looks slightly inelegant), the function will not generate any new garbage when it is called. -->
在上面的代码中，用新值替换了数组中的已有内容。尽管这种方式需要在调用函数的代码中完成数组的初始化分配（看起来不怎么优雅），但是这个函数被调用时将不再产生任何新的垃圾。

<!-- ## Requesting a Collection -->
## 请求一个集合

<!-- As mentioned above, it is best to avoid allocations as far as possible. However, given that they can’t be completely eliminated, there are two main strategies you can use to minimise their intrusion into gameplay:- -->

如上所述，最好是尽可能地避免分配。但是，鉴于不可能完全消除分配的事实，有两种主要策略可以最小化分配对游戏的影响：

<!-- ### Small heap with fast and frequent garbage collection -->
### 快节奏地分配小堆 + 频繁地内存回收

<!-- This strategy is often best for games that have long periods of gameplay where a smooth framerate is the main concern. A game like this will typically allocate small blocks frequently but these blocks will be in use only briefly. The typical heap size when using this strategy on iOS is about 200KB and garbage collection will take about 5ms on an iPhone 3G. If the heap increases to 1MB, the collection will take about 7ms. It can therefore be advantageous sometimes to request a garbage collection at a regular frame interval. This will generally make collections happen more often than strictly necessary but they will be processed quickly and with minimal effect on gameplay: -->
这一策略对于需要平稳帧率、长时间运行的游戏非常有效。这类游戏通常会频繁地分配小块内存，并且只是短暂地使用这些小块内存。在 iOS 上使用这种策略时，典型的堆大小是 200KB 左右，以 iPhone 3G 为例，内存回收大约耗时 5ms；如果堆大小增加到 1MB，内存回收将耗时约 7ms。因此这种策略是有效的，最理想的情况是，有时内存回收会发生在常规帧之间。尽管这种策略会导致更频繁的内存回收，但是回收非常快，最小化了对游戏的影响：

```
if (Time.frameCount % 30 == 0)
{
   System.GC.Collect();
}
```

<!-- However, you should use this technique with caution and check the profiler statistics to make sure that it is really reducing collection time for your game. -->
不过，你应该谨慎地使用这项技术，检查性能统计数据，以确保真的降低了内存回收时间。

<!-- ### Large heap with slow but infrequent garbage collection -->
### 慢节奏地分配大堆 + 不频繁地内存回收

<!-- This strategy works best for games where allocations (and therefore collections) are relatively infrequent and can be handled during pauses in gameplay. It is useful for the heap to be as large as possible without being so large as to get your app killed by the OS due to low system memory. However, the Mono runtime avoids expanding the heap automatically if at all possible. You can expand the heap manually by preallocating some placeholder space during startup (ie, you instantiate a “useless” object that is allocated purely for its effect on the memory manager): -->

这种策略对于分配和回收相对不频繁、可以在游戏暂停期间处理的游戏非常有效。在分配尽可能大的堆后，有些操作系统会因为系统内存不足而杀死应用，这种策略对于不会杀死应用的操作系统非常有用。不过，Mono 在运行时会尽可能不自动去扩展堆大小。你可以在启动时通过预分配占位空间的方式，手动扩展堆大小（例如，初始化一个纯粹是为了分配内存空间的无用对象）：

```c#
//C# script example
using UnityEngine;
using System.Collections;

public class ExampleScript : MonoBehaviour {
    void Start() {
        var tmp = new System.Object[1024];
        
        // make allocations in smaller blocks to avoid them to be treated in a special way, which is designed for large blocks
        for (int i = 0; i < 1024; i++)
            tmp[i] = new byte[1024];
        
        // release reference
        tmp = null;
    }
}
```

```js
//JS script example
function Start() {
    var tmp = new System.Object[1024];

    // make allocations in smaller blocks to avoid them to be treated in a special way, which is designed for large blocks
        for (var i : int = 0; i < 1024; i++)
        tmp[i] = new byte[1024];

    // release reference
        tmp = null;
}
```

<!-- A sufficiently large heap should not get completely filled up between those pauses in gameplay that would accommodate a collection. When such a pause occurs, you can request a collection explicitly: -->
在游戏暂停之间，这个足够大的堆不应该被完全填满，因为会导致内存回收。当游戏暂停时，你可以明确地请求一次内存回收：

```
System.GC.Collect();
```

<!-- Again, you should take care when using this strategy and pay attention to the profiler statistics rather than just assuming it is having the desired effect. -->
同样，你应该小心地使用这种策略，关注性能分析，而不仅仅是假设它有预期的效果。

<!-- ## Reusable Object Pools -->
## 可复用的对象池

<!-- There are many cases where you can avoid generating garbage simply by reducing the number of objects that get created and destroyed. There are certain types of objects in games, such as projectiles, which may be encountered over and over again even though only a small number will ever be in play at once. In cases like this, it is often possible to reuse objects rather than destroy old ones and replace them with new ones. -->
在很多情况下，你可以简单地通过减少需要创建和销毁的对象数量来避免产生垃圾。游戏中某些类型的对象，例如射弹，它们可能在会反复出现，但是每次只会出现少数几个。在这种情况下，复用对象通常是可行的，而不是先销毁旧对象，然后创建新对象替换它们。

<!-- ## Further Information -->

## 补充信息

<!-- Memory management is a subtle and complex subject to which a great deal of academic effort has been devoted. If you are interested in learning more about it then [memorymanagement.org](http://www.memorymanagement.org/) is an excellent resource, listing many publications and online articles. Further information about object pooling can be found on the [Wikipedia page](http://en.wikipedia.org/wiki/Object_pool_pattern) and also at [Sourcemaking.com](http://sourcemaking.com/design_patterns/object_pool). -->
内存管理是一个精细而复杂的课题，已经投入了大量学术上的努力。如果你有兴趣了解更多内容，[memorymanagement.org](http://www.memorymanagement.org/) 是一个很好的资源，上面列出了许多出版物和网络文章。关于对象池的更多信息，你可以在 [Wikipedia page](http://en.wikipedia.org/wiki/Object_pool_pattern) 和 [Sourcemaking.com](http://sourcemaking.com/design_patterns/object_pool) 上找到。
