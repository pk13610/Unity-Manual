<!-- Unity Manual > Scripting > Scripting Overview > Controlling GameObjects Using Components -->

<!-- # Controlling GameObjects Using Components -->
# 使用组件控制游戏对象

<!-- In the Unity editor, you make changes to Component properties using the Inspector. So, for example, changes to the position values of the Transform Component will result in a change to the GameObject’s position. Similarly, you can change the color of a Renderer’s material or the mass of a Rigidbody with a corresponding effect on the appearance or behavior of the GameObject. For the most part, scripting is also about modifying Component properties to manipulate GameObjects. The difference, though, is that a script can vary a property’s value gradually over time or in response to input from the user. By changing, creating and destroying objects at the right time, any kind of gameplay can be implemented. -->

在 Unity 编辑器中，你可以使用检视视图修改组件的属性。例如，改变游戏对象的变换组件的位置值，将会导致游戏对象的位置发生变化。类似地，修改渲染器材质的颜色或刚体的质量，将会对象的外观或行为产生相应的影响。大多数情况下，脚本也可以修改组件属性，从而操纵游戏对象。不同的是，脚本可以随时间改变属性的值，或响应用户的输入。通过在正确的时间修改、创建和销毁对象，可以实现任何类型的游戏。

<!-- ## Accessing Components -->
## 访问组件

<!-- The simplest and most common case is where a script needs access to other Components attached to the same GameObject. As mentioned in the Introduction section, a Component is actually an instance of a class so the first step is to get a reference to the Component instance you want to work with. This is done with the [GetComponent](https://docs.unity3d.com/ScriptReference/Component.GetComponent.html) function. Typically, you want to assign the Component object to a variable, which is done in C# using the following syntax: -->

最简单也最常见的情况是，脚本需要访问游戏对象上绑定的其他组件。正如简介部分所述，组件实际上是某个类的实例，所以第一步是拿到要访问的组件实例的引用。这一步通过 [GetComponent] 函数完成。通常，你需要把组件实例分配给一个变量。在 C# 中使用下面的语法完成：

[GetComponent]: https://docs.unity3d.com/ScriptReference/Component.GetComponent.html

```c#
void Start () {
    Rigidbody rb = GetComponent<Rigidbody>();
}
```

<!-- In UnityScript, the syntax is subtly different: -->

在 UnityScript 中，语法稍有不同：

```js
function Start () {
    var rb = GetComponent.<Rigidbody>();
}
```

<!-- Once you have a reference to a Component instance, you can set the values of its properties much as you would in the Inspector: -->

一旦有了组件实例的引用，就可以像在检视视图 Inspector 中一样，设置它的属性值：

```c#
void Start () {
    Rigidbody rb = GetComponent<Rigidbody>();
    
    // Change the mass of the object's Rigidbody.
    rb.mass = 10f;
}
```

<!-- An extra feature that is not available in the Inspector is the possibility of calling functions on Component instances: -->

一个额外特性是，脚本可以调用组件实例的函数，这在检视视图中是不可能的：

```c#
void Start () {
    Rigidbody rb = GetComponent<Rigidbody>();
    
    // Add a force to the Rigidbody.
    rb.AddForce(Vector3.up * 10f);
}
```

<!-- Note also that there is no reason why you can’t have more than one custom script attached to the same object. If you need to access one script from another, you can use GetComponent as usual and just use the name of the script class (or the filename) to specify the Component type you want. -->

还需要注意到，同一个游戏对象没有理由不能绑定多个自定义脚本。如果需要从一个脚本访问另一个脚本，可以像平常一样使用 GetComponent，只需要用脚本类的名字（或文件名）指定所需的组件类型。

<!-- If you attempt to retrieve a Component that hasn’t actually been added to the GameObject then GetComponent will return null; you will get a null reference error at runtime if you try to change any values on a null object. -->

如果尝试检索一个实际上尚未添加到游戏对象的组件，GetComponent 函数将返回 null；如果尝试在一个 null 对象上改变任意值，会在运行时抛出一个空指针错误。

<!-- ## Accessing Other Objects -->
## 访问其他对象

<!-- Although they sometimes operate in isolation, it is common for scripts to keep track of other objects. For example, a pursuing enemy might need to know the position of the player. Unity provides a number of different ways to retrieve other objects, each appropriate to certain situations. -->

尽管脚本有时是孤立地运行，但是脚本跟踪其他对象的状态也很常见。例如，一个追击的敌人可能需要知道被追击玩家的位置。Unity 提供了许多不同的方式来检索其他对象，每种方式对应特定的情况。

<!-- ### Linking Objects with Variables -->
### 用变量连接对象

<!-- The most straightforward way to find a related GameObject is to add a public GameObject variable to the script: -->

查找关联对象的最直接方式是，为脚本添加一个公共的游戏对象变量：

```c#
public class Enemy : MonoBehaviour {
    public GameObject player;
    
    // Other variables and functions...
}
```

<!-- This variable will be visible in the Inspector like any other: -->

这个变量将像其他变量一样显示在检视视图 Inspector 中。

![](https://docs.unity3d.com/uploads/Main/GameObjectPublicVar.png)

<!-- You can now drag an object from the scene or Hierarchy panel onto this variable to assign it. The GetComponent function and Component access variables are available for this object as with any other, so you can use code like the following: -->

现在，可以从场景视图或层级视图拖动一个对象到这个变量上进行分配。然后，就可以访问这个对象的 GetComponent 函数和组件变量。因此，你可以使用下面的代码：

```c#
public class Enemy : MonoBehaviour {
    public GameObject player;
    
    void Start() {
        // Start the enemy ten units behind the player character.
        transform.position = player.transform.position - Vector3.forward * 10f;
    }
}
```

<!-- Additionally, if declare a public variable of a Component type in your script, you can drag any GameObject that has that Component attached onto it. This will access the Component directly rather than the GameObject itself. -->

另外，如果在脚本中声明了某个组件类型的公共变量，你可以拖动绑定了该组件的任意对象到该变量上。这时将直接访问组件，而不是游戏对象。

```c#
public Transform playerTransform;
```

<!-- Linking objects together with variables is most useful when you are dealing with individual objects that have permanent connections. You can use an array variable to link several objects of the same type, but the connections must still be made in the Unity editor rather than at runtime. It is often convenient to locate objects at runtime and Unity provides two basic ways to do this, as described below. -->

当处理永久链接的独立对象时，用变量连接对象是最合适的方式。你可以用一个数组变量来连接多个同类型的对象，但是这种连接必须在 Unity 编辑器中建立，而不是在运行时。不过，在运行时定位对象也很方便，Unity 提供了两种基本方式来实现这点。

<!-- ### Finding Child Objects -->
### 查找子对象

<!-- Sometimes, a game scene will make use of a number of objects of the same type, such as enemies, waypoints and obstacles. These may need to be tracked by a particular script that supervises or reacts to them (eg, all waypoints may need to be available to a pathfinding script). Using variables to link these objects is a possibility but it will make the design process tedious if each new waypoint has to be dragged to a variable on a script. Likewise, if a waypoint is deleted then it is a nuisance to have to remove the variable reference to the missing object. In cases like this, it is often better to manage a set of objects by making them all children of one parent object. The child objects can be retreived using the parent’s Transform Component (since all GameObjects implicitly have a Transform): -->

有时，一个游戏场景将使用多个相同类型的对象，例如敌人、路径和障碍物。可能需要一个特定脚本来跟踪、监督它们，或者还需要对它们进行响应（例如，用一个寻路脚本维护所有的路径）。虽然使用变量连接这些对象是一种可行的方式，但是如果每个新行路径都需要拖拽到某个脚本的变量上，将使设计过程变得非常乏味。同样，如果一个路径被删除，那么移除变量对无效对象的引用就会变成麻烦。在这样的情况下，通常最好是把它们都作为子对象放到一个父对象中，用一个对象集合来管理它们。子对象可以通过父对象的变换组件 Transform 来检索（因为所有游戏对象都隐含一个变换组件）：

```c#
using UnityEngine;

public class WaypointManager : MonoBehaviour {
    public Transform[] waypoints;
    
    void Start() {
        waypoints = new Transform[transform.childCount];
        int i = 0;
        
        foreach (Transform t in transform) {
            waypoints[i++] = t;
        }
    }
}
```

<!-- You can also locate a specific child object by name using the Transform.Find function: -->

你还可以使用 Transform.Find 函数查找特定名称的子对象：

```c#
transform.Find("Gun");
```

<!-- This can be useful when an object has a child that can be added and removed during gameplay. A weapon that can be picked up and put down is a good example of this. -->

在游戏过程中，如果父对象的子对象可以被添加和删除，这种方式可能很有用。一个很好的例子是，一把武器可以被捡起和放下。

<!-- ### Finding Objects by Name or Tag -->
### 按照名称或标签查找对象

<!-- It is always possible to locate GameObjects anywhere in the scene hierarchy as long as you have some information to identify them. Individual objects can be retrieved by name using the [GameObject.Find](https://docs.unity3d.com/ScriptReference/GameObject.Find.html) function: -->

只要场景中的游戏对象具有某些标识信息，那么，总是可以定位任意位置的游戏对象。可以用 [GameObject.Find] 函数按照名称检索单个对象：

[GameObject.Find]: https://docs.unity3d.com/ScriptReference/GameObject.Find.html

```c#
GameObject player;

void Start() {
    player = GameObject.Find("MainHeroCharacter");
}
```

<!-- An object or a collection of objects can also be located by their tag using the GameObject.FindWithTag and GameObject.FindGameObjectsWithTag functions:- -->

也可以使用 GameObject.FindWithTag 和 GameObject.FindGameObjectsWithTag 函数按照标签来定位对象或对象集合：


```c#
GameObject player;
GameObject[] enemies;

void Start() {
    player = GameObject.FindWithTag("Player");
    enemies = GameObject.FindGameObjectsWithTag("Enemy");
}
```
