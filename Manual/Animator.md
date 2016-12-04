<!-- Unity Manual > Animation > Animator Controllers > The Animator Controller Asset -->

<!-- # The Animator Controller Asset -->
# 动画控制器资源

<!-- When you have an animation clips ready to use, you need to use an **Animator Controller** to bring them together. An Animator Controller asset is created within Unity and allows you to maintain a set of animations for a character or object. -->

准备好动画剪辑后，你还需要使用 **动画控制 Animator Controller** 把它们整合在一起。动画控制器资源由 Unity 创建，允许为一个角色或对象维护一组动画。


![An Animator Controller Asset in the Project Folder](https://docs.unity3d.com/uploads/Main/AnimatorAssetIcon.png)
<!-- > An Animator Controller Asset in the Project Folder -->
> 项目视图中的动画控制器资源。


<!-- Animator Controller assets are created from the Assets menu, or from the Create menu in the Project window. -->

可以从 Assets 菜单或项目视图的 Create 菜单创建动画控制器。

<!-- In most situations, it is normal to have multiple animations and switch between them when certain game conditions occur. For example, you could switch from a walk animation to a jump whenever the spacebar is pressed. However even if you just have a single animation clip you still need to place it into an animator controller to use it on a Game Object. -->

最常见的情况是，拥有多个动画剪辑，并在特定游戏条件发生时，在它们之间切换。例如，每当按下空格键时，可以从行走动画切换为跳跃动画。即使是只有一个动画剪辑，想要在游戏对象上使用它，也需要把它放入一个动画控制器中。

<!-- The controller manages the various animation states and the transitions between them using a so-called **State Machine**, which could be thought of as a kind of flow-chart, or a simple program written in a visual programming language within Unity. More information about state machines can be found [here](https://docs.unity3d.com/Manual/AnimationStateMachines.html). The structure of the Animator Controller can be created, viewed and modified in the [Animator Window](https://docs.unity3d.com/Manual/AnimatorWindow.html). -->

动画控制器使用所谓的 **状态机 State Machine** 来管理各种动画和它们之间的切换。可以把状态机认为是一种流程图，或者是一段在 Unity 中用可视化编程语言编写的简单程序。有关状态机的更多信息可以在 [这里](https://docs.unity3d.com/Manual/AnimationStateMachines.html) 找到。可以在 [动画控制器视图](https://docs.unity3d.com/Manual/AnimatorWindow.html) 中创建、产看和修改动画控制器的结构。


![A simple Animator Controller](https://docs.unity3d.com/uploads/Main/MecanimAnimatorControllerWindow.png)
<!-- > A simple Animator Controller -->
> 一个简单的动画控制器

<!-- The animator controller is finally applied to an object by attaching an **Animator** component that references them. See the reference manual pages about the [Animator](https://docs.unity3d.com/Manual/class-Animator.html) component and [Animator Controller](https://docs.unity3d.com/Manual/class-AnimatorController.html) for further details about their use. -->

最终，动画控制器通过 **动画组件** 来应用到游戏对象上，动画组件引用了动画控制器。更多详细信息请参阅 [动画组件] 和 [动画控制器] 的参考手册。

[动画组件]: https://docs.unity3d.com/Manual/class-Animator.html
[动画控制器]: https://docs.unity3d.com/Manual/class-AnimatorController.html
