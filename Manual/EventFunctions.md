<!-- # Event Functions -->
# 事件函数

<!-- A script in Unity is not like the traditional idea of a program where the code runs continuously in a loop until it completes its task. Instead, Unity passes control to a script intermittently by calling certain functions that are declared within it. Once a function has finished executing, control is passed back to Unity. These functions are known as event functions since they are activated by Unity in response to events that occur during gameplay. Unity uses a naming scheme to identify which function to call for a particular event. For example, you will already have seen the Update function (called before a frame update occurs) and the Start function (called just before the object’s first frame update). Many more event functions are available in Unity; the full list can be found in the script reference page for the MonoBehaviour class along with details of their usage. The following are some of the most common and important events. -->

传统编程的思路是，在一个循环结构中连续运行代码，直到完成任务。Unity 中的脚本则不同，Unity 通过间歇地调用脚本中声明的特定函数来控制脚本。一旦某个函数执行完成，控制权被交会 Unity。这些函数被成为事件函数，因为 Unity 通过激活它们来响应游戏过程中发生的各种事件。Unity 使用一套命名方案来唯一标识特定事件对应（调用）的函数。例如，你已经看到的 Update 函数（每桢更新之前被调用）和 Start 函数（游戏对象的第一桢更新前被调用）。Unity 提供了许多事件函数，可以在 MonoBehaviour 类的脚本参考页找到完整列表和用法的详细信息。下面是一些最常用和最重要的事件。

<!-- ## Regular Update Events -->
## 定期更新事件

<!-- A game is rather like an animation where the animation frames are generated on the fly. A key concept in games programming is that of making changes to position, state and behavior of objects in the game just before each frame is rendered. The [Update] function is the main place for this kind of code in Unity. Update is called before the frame is rendered and also before animations are calculated. -->

一个游戏更像一段动画，因为动画桢是实时生成的。游戏编程中的一个关键概念是，在每一桢渲染之前，更改游戏中对象的位置、状态和行为。在 Unity 中，[Update] 函数是放置这类代码的主要地方。Update 在桢渲染和动画计算之前被调用。

[Update]: https://docs.unity3d.com/ScriptReference/MonoBehaviour.Update.html

```cs
void Update() {
    float distance = speed * Time.deltaTime * Input.GetAxis("Horizontal");
    transform.Translate(Vector3.right * distance);
}
```

<!-- The physics engine also updates in discrete time steps in a similar way to the frame rendering. A separate event function called FixedUpdate is called just before each physics update. Since the physics updates and frame updates do not occur with the same frequency, you will get more accurate results from physics code if you place it in the FixedUpdate function rather than Update. -->

物理引擎也以离散的时间步长进行更新，类似于桢渲染。每次物理更新之前，函数 [FixedUpdate] 被调用。因为物理更新和桢更新以不同的频率发生，所以，如果你把物理代码放入 FixedUpdate 而不是 Update，可以获得更准确的结果。

[FixedUpdate]: https://docs.unity3d.com/ScriptReference/MonoBehaviour.FixedUpdate.html

```cs
void FixedUpdate() {
    Vector3 force = transform.forward * driveForce * Input.GetAxis("Vertical");
    rigidbody.AddForce(force);
}
```

<!-- It is also useful sometimes to be able to make additional changes at a point after the Update and FixedUpdate functions have been called for all objects in the scene and after all animations have been calculated. An example is where a camera should remain trained on a target object; the adjustment to the camera’s orientation must be made after the target object has moved. Another example is where the script code should override the effect of an animation (say, to make the character’s head look towards a target object in the scene). The [LateUpdate] function can be used for these kinds of situations. -->

当场景中所有对象的 Update 和 FixedUpdate 函数调用完，并且所有动画计算完成之后，执行一些额外的更改可能会很有用。一个例子是摄像机跟踪某个目标对象时，对摄像机方位的调整必须发生在目标对象移动之后。另一个例子是脚本代码想要覆盖动画效果（例如，让角色头部面向场景中的某个目标）。[LateUpdate] 函数可以用于这类情况。

> 译注：既然 Update 和 FixedUpdate 的执行频率不同，那么怎么保证 LateUpdate 的顺序呢？看了 [事件函数执行顺序] 里的流程图还是不确定。

[LateUpdate]: https://docs.unity3d.com/ScriptReference/MonoBehaviour.LateUpdate.html

```cs
void LateUpdate() {
    Camera.main.transform.LookAt(target.transform);
}
```

<!-- ## Initialization Events -->
## 初始化事件

<!-- It is often useful to be able to call initialization code in advance of any updates that occur during gameplay. The [Start] function is called before the first frame or physics update on an object. The [Awake] function is called for each object in the scene at the time when the scene loads. Note that although the various objects’ Start and Awake functions are called in arbitrary order, all the Awakes will have finished before the first Start is called. This means that code in a Start function can make use of other initializations previously carried out in the Awake phase. -->

在游戏期间发生任何更新之前，能够调用初始化代码通常很有用。在对象的第一桢或第一次物理更新之前，[Start] 函数被调用。在场景加载时，为场景中的每个对象调用 [Awake] 函数。请注意，尽管各种对象的 Start 和 Awake 函数以任意顺序被调用，但是在第一个 Start 函数被调用之前，所有的 Awake 函数都应该已经完成。这意味着，Start 函数中的代码可以使用之前 Awake 阶段执行的初始化（赋值）。

[Start]: https://docs.unity3d.com/ScriptReference/MonoBehaviour.Start.html
[Awake]: https://docs.unity3d.com/ScriptReference/MonoBehaviour.Awake.html

<!-- ## GUI events -->
## GUI 事件

<!-- Unity has a system for rendering GUI controls over the main action in the scene and responding to clicks on these controls. This code is handled somewhat differently from the normal frame update and so it should be placed in the [OnGUI] function, which will be called periodically. -->

Unity 提供了一套 GUI 控件渲染系统，用于控制场景中的主要操作和响应对控件的点击。这种代码与正常的桢更新有些不同，因为应该放入 [OnGUI] 函数，该函数会被周期性调用。


[OnGUI]: https://docs.unity3d.com/ScriptReference/MonoBehaviour.OnGUI.html

```cs
void OnGUI() {
    GUI.Label(labelRect, "Game Over");
}
```

<!-- You can also detect mouse events that occur over a GameObject as it appears in the scene. This can be used for targeting weapons or displaying information about the character currently under the mouse pointer. A set of OnMouseXXX event functions (eg, [OnMouseOver], [OnMouseDown]) is available to allow a script to react to user actions with the mouse. For example, if the mouse button is pressed while the pointer is over a particular object then an OnMouseDown function in that object’s script will be called if it exists. -->

你还可以检测场景中显示的游戏对象上发生的鼠标事件。这可以用于武器瞄准，或显示当前鼠标指针所指角色的信息。脚本使用一组 OnMouseXXX 事件函数（例如 [OnMouseOver]、[OnMouseDown]）响应用户鼠标的行为。例如，如果按下鼠标按钮，并且指针位于一个特定对象之上时，那么该对象上脚本的 OnMouseDown 函数将被调用（如果存在的话）。

[OnMouseOver]: https://docs.unity3d.com/ScriptReference/MonoBehaviour.OnMouseOver.html
[OnMouseDown]: https://docs.unity3d.com/ScriptReference/MonoBehaviour.OnMouseOver.html

<!-- ## Physics events -->
## 物理事件

<!-- The physics engine will report collisions against an object by calling event functions on that object’s script. The [OnCollisionEnter], [OnCollisionStay] and [OnCollisionExit] functions will be called as contact is made, held and broken. The corresponding [OnTriggerEnter], [OnTriggerStay] and [OnTriggerExit] functions will be called when the object’s collider is configured as a Trigger (ie, a collider that simply detects when something enters it rather than reacting physically). These functions may be called several times in succession if more than one contact is detected during the physics update and so a parameter is passed to the function giving details of the collision (position, identity of the incoming object, etc). -->

物理引擎将通过调用脚本的事件函数，来报告与对象的碰撞。当建立、保持和断开连接时（碰撞时两个物体连接在一起），[OnCollisionEnter]、[OnCollisionStay] 和 [OnCollisionExit] 函数将被调用。如果对象的碰撞器被配置为触发器（例如，简单地检测某个对象是否进入了碰撞器，而不是响应物理行为），相应的 [OnTriggerEnter]、[OnTriggerStay] 和 [OnTriggerExit] 函数将被调用。在物理更新期间，如果检测到多个连接，那么这些函数可能会连续多次被调用，因此，会传给函数一个含有碰撞信息的参数（位置、相关对象的标识等）。

[OnCollisionEnter]: https://docs.unity3d.com/ScriptReference/MonoBehaviour.OnCollisionEnter.html
[OnCollisionStay]: https://docs.unity3d.com/ScriptReference/MonoBehaviour.OnCollisionStay.html
[OnCollisionExit]: https://docs.unity3d.com/ScriptReference/MonoBehaviour.OnCollisionExit.html
[OnTriggerEnter]: https://docs.unity3d.com/ScriptReference/MonoBehaviour.OnTriggerEnter.html
[OnTriggerStay]: https://docs.unity3d.com/ScriptReference/MonoBehaviour.OnTriggerStay.html
[OnTriggerExit]: https://docs.unity3d.com/ScriptReference/MonoBehaviour.OnTriggerExit.html

```cs
void OnCollisionEnter(otherObj: Collision) {
    if (otherObj.tag == "Arrow") {
        ApplyDamage(10);
    }
}
```