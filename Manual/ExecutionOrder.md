<!-- Unity Manual > Scripting > Scripting Overview > Execution Order of Event Functions -->

Unity 手册 > 脚本 > 脚本概述 > 事件执行顺序

<!-- # Execution Order of Event Functions -->
# 事件函数执行顺序

<!-- In Unity scripting, there are a number of event functions that get executed in a predetermined order as a script executes. This execution order is described below: -->
在 Unity 脚本中，有大量的事件函数以特定的顺序被执行。执行顺序描述如下：

<!-- ## Editor -->
## 编辑器

<!-- * **Reset:** Reset is called to initialize the script’s properties when it is first attached to the object and also when the Reset command is used. -->

* **Reset**

    当第一次把脚本绑定到对象上，或者使用了 Reset 命令时，该事件被触发，用以初始化脚本的属性。

<!-- ## First Scene Load -->
## 加载第一个场景

<!-- These functions get called when a scene starts (once for each object in the scene). -->
当某个场景开始时，下面的事件被触发（场景中的每个对象都会执行一次）：

<!-- * **Awake:** This function is always called before any Start functions and also just after a prefab is instantiated. (If a GameObject is inactive during start up Awake is not called until it is made active.)
* **OnEnable:** (only called if the Object is active): This function is called just after the object is enabled. This happens when a MonoBehaviour instance is created, such as when a level is loaded or a GameObject with the script component is instantiated.
* **OnLevelWasLoaded:** This function is executed to inform the game that a new level has been loaded. -->

* **Awake**

    该函数总是在所有 Start 函数之前被调用，并且只会在某个 prefab 被实例化之后才会被调用。（如果一个 GameObject 在启动时是非激活状态，那么 Awake 函数不会被调用，直到这个 GameObject 处于激活状态。）

* **OnEnable**
    
    （只有对象处于激活状态才会被调用）该函数在对象处于可用状态之后被调用。当一个 MonoBehaviour 实例被创建时，就会调用该函数。例如关卡加载完成、某个带有脚本组件的 GameObject 被实例化后。

* **OnLevelWasLoaded**

    该函数在某个新关卡加载完成后被执行，用来向游戏通知新关卡已经被载入。

<!-- Note that for objects added to the scene, the Awake and OnEnable functions for all scripts will be called before Start, Update, etc are called for any of them. Naturally, this cannot be enforced when an object is instantiated during gameplay. -->
请注意，对于场景 scene 中已有对象上附加的脚本组件，函数 Awake 和 OnEnable 将在所有 Start、Update 等函数之前被调用。当然，如果某个对象是游戏运行时实例化的，那么不遵循这条原则。

<!--## Before the first frame update-->
## 第一帧更新之前

<!--* **Start:** Start is called before the first frame update only if the script instance is enabled.-->

* **Start**

    该函数在第一帧更新之前被调用，前提是该脚本实例必须是可用的。

<!--For objects added to the scene, the Start function will be called on all scripts before Update, etc are called for any of them. Naturally, this cannot be enforced when an object is instantiated during gameplay.-->

对于场景 scene 中已有对象上附加的脚本组件，函数 Start 在 Update 等函数之前被调用。当然，如果某个对象是游戏运行时实例化的，那么不遵循这条原则。

<!-- ## In between frames -->
## 帧间

<!-- * **OnApplicationPause:** This is called at the end of the frame where the pause is detected, effectively between the normal frame updates. One extra frame will be issued after OnApplicationPause is called to allow the game to show graphics that indicate the paused state. -->

* **OnApplicationPause**

    如果游戏处于暂停状态，该函数在某一个帧的末尾被调用，也就是说，是在正常帧（更新）之间被调用。当 OnApplicationPause 被调用后，一个特殊的帧被创建，这样游戏可以显示暂停状态的图形。

<!-- ## Update Order -->
## 帧更新顺序

<!-- When you’re keeping track of game logic and interactions, animations, camera positions, etc., there are a few different events you can use. The common pattern is to perform most tasks inside the Update function, but there are also other functions you can use. -->
当你跟踪游戏的逻辑、交互、动画、摄像机位置等时，也有几个事件可供使用。通常我们是在 Update 函数中执行大部分任务，但也可以使用其他的函数。

<!-- * **FixedUpdate:** FixedUpdate is often called more frequently than Update. It can be called multiple times per frame, if the frame rate is low and it may not be called between frames at all if the frame rate is high. All physics calculations and updates occur immediately after FixedUpdate. When applying movement calculations inside FixedUpdate, you do not need to multiply your values by Time.deltaTime. This is because FixedUpdate is called on a reliable timer, independent of the frame rate.
* **Update:** Update is called once per frame. It is the main workhorse function for frame updates.
**LateUpdate:** LateUpdate is called once per frame, after Update has finished. Any calculations that are performed in Update will have completed when LateUpdate begins. A common use for LateUpdate would be a following third-person camera. If you make your character move and turn inside Update, you can perform all camera movement and rotation calculations in LateUpdate. This will ensure that the character has moved completely before the camera tracks its position. -->

* **FixedUpdate**

    通常，FixedUpdate 比 Update 调用的更频繁。如果帧率很低，可以在每一帧上多次调用 FixedUpdate；如果帧率很高，FixedUpdate 更本不会被调用。调用 FixedUpdate 之后，所有的物理计划和更新会立即生效，如果在 FixedUpdate 中执行位移计算，你就不需要基于 Time.deltaTime 来计算。因为 FixedUpdate 基于一个可靠的计时器，与帧率无关。

* **Update**

    每帧调用一次 Update。对于帧更新来说，Update 是主要的任务承载函数。

* **LateUpdate**

    LateUpdate 在 Update 完成之后被调用，每帧调用一次。当 LateUpdate 开始执行时，Update 中执行的所以计算都已完成。如果你在 Update 中移动和旋转角色，那么你可以在 LateUpdate 中移动和旋转摄像机。这样，在摄像机跟随角色的位置之前，可以确保角色的移动已经完成。

<!-- ## Rendering -->
## 渲染

<!-- * **OnPreCull:** Called before the camera culls the scene. Culling determines which objects are visible to the camera. OnPreCull is called just before culling takes place.
* **OnBecameVisible/OnBecameInvisible:** Called when an object becomes visible/invisible to any camera.
* **OnWillRenderObject:** Called once for each camera if the object is visible.
* **OnPreRender:** Called before the camera starts rendering the scene.
* **OnRenderObject:** Called after all regular scene rendering is done. You can use [GL](http://docs.unity3d.com/ScriptReference/GL.html) class or [Graphics.DrawMeshNow](http://docs.unity3d.com/ScriptReference/Graphics.DrawMeshNow.html) to draw custom geometry at this point.
* **OnPostRender:** Called after a camera finishes rendering the scene.
* **OnRenderImage:** Called after scene rendering is complete to allow postprocessing of the image, see [ImageEffects](http://docs.unity3d.com/Manual/comp-ImageEffects.html).
* **OnGUI:** Called multiple times per frame in response to GUI events. The Layout and Repaint events are processed first, followed by a Layout and keyboard/mouse event for each input event.
* **OnDrawGizmos** Used for drawing Gizmos in the scene view for visualisation purposes. -->

* **OnPreCull**

    在摄像机对场景进行 Culling 之前被调用。Culling 确定了哪些对象对于摄像机是可见的。
    
    > 译注 [Unity中的优化技术](http://blog.csdn.net/candycat1992/article/details/42127811)

* **OnBecameVisible/OnBecameInvisible**

    当某个对象对于任意摄像机变为可见活不可见时被调用。

* **OnWillRenderObject**

    为每个摄像戏调用一次，如果该对象是可见的。

* **OnPreRender**

    在摄像机开始渲染场景之前被调用。
    
* **OnRenderObject**

    在常规场景渲染完成之后被调用。此时，你可以使用类 [GL](http://docs.unity3d.com/ScriptReference/GL.html) 或 [Graphics.DrawMeshNow](http://docs.unity3d.com/ScriptReference/Graphics.DrawMeshNow.html) 绘制自定义的几何体。

* **OnPostRender**

    当某个摄像机完成渲染场景之后被调用。

* **OnRenderImage** 

    在场景渲染完成之后被调用，用于图像后处理，请查看 [ImageEffects](http://docs.unity3d.com/Manual/comp-ImageEffects.html)。

* **OnGUI**

    用于响应 GUI 事件，每一帧会多次调用。首先处理 Layout 和 Repaint 事件，然后是 Layout，以及每次用户输入触发的 keyboard/mouse 事件。
    
* **OnDrawGizmos**

    用于在场景视图中绘制 Gizmos，使之可视化。

<!-- ## Coroutines -->
## 协同程序

<!-- Normal coroutine updates are run after the Update function returns. A coroutine is a function that can suspend its execution (yield) until the given YieldInstruction finishes. Different uses of Coroutines: -->
通常，协同更新在函数 Update 返回后运行。一个协同程序是一个可以暂停暂行过程的函数，当给定的 YieldInstruction 完成时继续执行。协同程序的不同用法如下：

<!-- * **yield** The coroutine will continue after all Update functions have been called on the next frame.
* **yield WaitForSeconds** Continue after a specified time delay, after all Update functions have been called for the frame
* **yield WaitForFixedUpdate** Continue after all FixedUpdate has been called on all scripts
* **yield WWW** Continue after a WWW download has completed.
* **yield StartCoroutine** Chains the coroutine, and will wait for the MyFunc coroutine to complete first. -->

* **yield**

    下一帧中的所有 Update 函数被调用后，协同程序将继续执行。

* **yield WaitForSeconds**

    当前帧的所有 Update 函数被调用后，并且延迟给定的时间，协同程序将继续执行。

* **yield WaitForFixedUpdate**

    所有脚本的 FixedUpdate 函数被调用后，协同程序将继续执行。

* **yield WWW**

    网络下载完成后，协同程序将继续执行。

* **yield StartCoroutine**

    将协同程序串联起来，等待 MyFunc 执行完成后，继续链式执行。

<!-- ## When the Object is Destroyed -->
## 当对象被销毁时

<!-- * **OnDestroy:** This function is called after all frame updates for the last frame of the object’s existence (the object might be destroyed in response to Object.Destroy or at the closure of a scene). -->

* **OnDestroy**

    在对象存在的最后一帧，当所有帧更新都完成后，该函数被调用（该对象可能因为调用了 Object.Destroy 而被销毁，也可能随着场景的关闭而销毁）。


<!-- ## When Quitting -->
## 当退出时

<!-- These functions get called on all the active objects in your scene: -->
这些函数会在场景中的所有激活对象上调用。

<!-- * **OnApplicationQuit:** This function is called on all game objects before the application is quit. In the editor it is called when the user stops playmode.
* **OnDisable:** This function is called when the behaviour becomes disabled or inactive. -->

* **OnApplicationQuit**

    在应用程序退出前，在所有游戏对象调用该方法。如果是在编辑器中，那么当用户停止游戏模式时，该函数被调用。

* **OnDisable**

    当游戏对象的行为变为禁用或不活动时，该函数被调用。


<!-- ## Script Lifecycle Flowchart -->
## 脚本生命周期流程图

<!-- The following diagram summarises the ordering and repetition of event functions during a script’s lifetime. -->
下图总结了脚本生命周期中事件函数的执行顺序和重复周期。

![](http://docs.unity3d.com/540/Documentation/uploads/Main/monobehaviour_flowchart.svg)