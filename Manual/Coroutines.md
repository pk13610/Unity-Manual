<!-- # Coroutines -->
# 协同程序

<!-- When you call a function, it runs to completion before returning. This effectively means that any action taking place in a function must happen within a single frame update; a function call can’t be used to contain a procedural animation or a sequence of events over time. As an example, consider the task of gradually reducing an object’s alpha (opacity) value until it becomes completely invisible. -->

当调用一个函数时，在它返回之前，会一直运行到完成。这意味着该函数中的任何动作都必须在一帧内完成；函数调用不能包含过程动画或一段时间内的事件序列。例如有这样一个任务，逐渐降低一个对象的 `alpha`（不透明度）值，直到它完全不可见。

```cs
void Fade() {
    for (float f = 1f; f >= 0; f -= 0.1f) {
        Color c = renderer.material.color;
        c.a = f;
        renderer.material.color = c;
    }
}
```

<!-- As it stands, the Fade function will not have the effect you might expect. In order for the fading to be visible, the alpha must be reduced over a sequence of frames to show the intermediate values being rendered. However, the function will execute in its entirety within a single frame update. The intermediate values will never be seen and the object will disappear instantly. -->

实际情况是，函数 Fade 不会实现你期望的效果。为了使渐变过程可见，`alpha` 必须随着桢序列降低，以渲染显示中间值。但是，该函数将在一帧内完整地执行。你将永远不会看到中间值，对象会立即消失。

<!-- It is possible to handle situations like this by adding code to the Update function that executes the fade on a frame-by-frame basis. However, it is often more convenient to use a coroutine for this kind of task. -->

可以把代码添加到 `Update` 函数中，逐桢地执行淡出，来处理这种情况。不过，更方便的方式是使用协程（协同程序）执行这种任务。

<!-- A coroutine is like a function that has the ability to pause execution and return control to Unity but then to continue where it left off on the following frame. In C#, a coroutine is declared like this: -->

协程就像一个函数，它能够暂停执行并将控制权返回给 Unity，但是在下一桢时，可以在暂停的位置继续执行。在 C# 中，可以像这样声明协程：

```cs
IEnumerator Fade() {
    for (float f = 1f; f >= 0; f -= 0.1f) {
        Color c = renderer.material.color;
        c.a = f;
        renderer.material.color = c;
        yield return null;
    }
}
```

<!-- It is essentially a function declared with a return type of IEnumerator and with the yield return statement included somewhere in the body. The yield return line is the point at which execution will pause and be resumed the following frame. To set a coroutine running, you need to use the [StartCoroutine] function: -->

协程本质上是一个返回类型被声明为 `IEnumerator` 的函数，并且在函数体的某处包含 `yield return` 语句。执行过程在 `yield return` 行暂停，并在下一桢恢复执行。要让协程运行起来，需要使用 [StartCoroutine] 函数：

[StartCoroutine]: https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html

```cs
void Update() {
    if (Input.GetKeyDown("f")) {
        StartCoroutine("Fade");
    }
}
```

<!-- In UnityScript, things are slightly simpler. Any function that includes the yield statement is understood to be a coroutine and the IEnumerator return type need not be explicitly declared: -->

在 UnityScript 中，事情稍微简单一些。任何含有 `yield` 语句的函数都被认为是一个协程，不需要显示声明返回类型 `IEnumerator：`

```js
function Fade() {
    for (var f = 1.0; f >= 0; f -= 0.1) {
        var c = renderer.material.color;
        c.a = f;
        renderer.material.color = c;
        yield;
    }
}
```

<!-- Also, a coroutine can be started in UnityScript by calling it as if it were a normal function: -->

此外，在 UnityScript 中，可以通过直接调用协程来启动它，就像它是一个普通的函数一样：

```js
function Update() {
    if (Input.GetKeyDown("f")) {
        Fade();
    }
}
```

<!-- You will notice that the loop counter in the Fade function maintains its correct value over the lifetime of the coroutine. In fact any variable or parameter will be correctly preserved between yields. -->

你将会注意到，在协程的生命周期内，`Fade` 函数中的循环计数器一直保持正确的值。实际上，`yield` 之间的任何变量或属性都将正确地保留。

<!-- By default, a coroutine is resumed on the frame after it yields but it is also possible to introduce a time delay using WaitForSeconds: -->

默认情况下，协程在 `yield` 之后的桢中恢复，不过也可以使用 `WaitForSeconds` 延迟恢复：

```cs
IEnumerator Fade() {
    for (float f = 1f; f >= 0; f -= 0.1f) {
        Color c = renderer.material.color;
        c.a = f;
        renderer.material.color = c;
        yield return new WaitForSeconds(.1f);
    }
}
```

<!-- and in UnityScript: -->
在 UnityScript 中：

```js
function Fade() {
    for (var f = 1.0; f >= 0; f -= 0.1) {
        var c = renderer.material.color;
        c.a = f;
        renderer.material.color = c;
        yield WaitForSeconds(0.1);
    }
}
```

<!-- This can be used as a way to spread an effect over a period time but it is also a useful optimization. Many tasks in a game need to be carried out periodically and the most obvious way to do this is to include them in the Update function. However, this function will typically be called many times per second. When a task doesn’t need to be repeated quite so frequently, you can put it in a coroutine to get an update regularly but not every single frame. An example of this might be an alarm that warns the player if an enemy is nearby. The code might look something like this: -->

协程可以把某些效果分散在一段时间内，也可以有效地优化性能。游戏中的许多任务需要定期执行，最明显的方式是将它们包含在 `Update` 函数中执行。但是 `Update` 函数通常每秒调用多次。当任务不需要如此频繁地重复时，你可以把它放入协程定期更新，而不是每桢都更新。一个例子是在敌人靠近玩家时触发警告。代码看起来可能像这样：

```cs
function ProximityCheck() {
    for (int i = 0; i < enemies.Length; i++) {
        if (Vector3.Distance(transform.position, enemies[i].transform.position) < dangerDistance) {
                return true;
        }
    }
    
    return false;
}
```

<!-- If there are a lot of enemies then calling this function every frame might introduce a significant overhead. However, you could use a coroutine to call it every tenth of a second: -->

如果有很多敌人，每桢都调用该函数可能会带来很大的开销。不过，你可以使用协程每秒调用该函数 10 次：

```cs
IEnumerator DoCheck() {
    for(;;) {
        ProximityCheck;
        yield return new WaitForSeconds(.1f);
    }
}
```

<!-- This would greatly reduce the number of checks carried out without any noticeable effect on gameplay. -->

这将大大减少执行检测的次数，而且不会对游戏性产生任何显著影响。
