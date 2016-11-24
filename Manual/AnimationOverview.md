<!-- > [Animation System Overview](https://docs.unity3d.com/Manual/AnimationOverview.html) -->

<!-- Unity Manual > Animation > Animation System Overview -->
<!-- Unity 手册 > 动画 > 动画系统预览 -->

<!-- # Animation System  -->
# 动画系统概览

<!-- Unity has a rich and sophisticated animation system (sometimes referred to as ‘Mecanim’). It provides: -->
Unity 拥有丰富和复杂的动画系统（有时称为 Mecanim），提供了以下功能：

<!-- 
* Easy workflow and setup of animations for all elements of Unity including objects, characters, and properties.
* Support for imported animation clips and animation created within Unity
* Humanoid animation retargeting - the ability to apply animations from one character model onto another.
* Simplified workflow for aligning animation clips.
* Convenient preview of animation clips, transitions and interactions between them. This allows animators to work more independently of programmers, prototype and preview their animations before gameplay code is hooked in.
* Management of complex interactions between animations with a visual programming tool.
* Animating different body parts with different logic.
* Layering and masking features
 -->
* 为 Unity 中的对象、角色、道具等元素提供易用的动画工作流程和设置。
* 支持导入动画片断和用 Unity 创建的动画。
* 人形动画重定位 — 这一能力允许把一个角色模型的动画应用到另一个角色。
* 为调整动画剪辑提供简化了的工作流程。
* 为动画剪辑、转换、交互提供方便的预览。使得动画可以更独立于程序和原型运行，在嵌入代码之前，就可以预览动画。
* 用可视化的编程工具管理动画之间的负责交互。
* 可以为不同的身体部位添加不同的动画逻辑。
* 层和遮罩功能。

![Typical view of an Animation State Machine in the Animator window](https://docs.unity3d.com/uploads/Main/MecanimShowcase.png)
<!-- > Typical view of an Animation State Machine in the Animator window -->

> 动画视图中的动画状态机

<!-- ## Animation workflow -->
## 动画工作流程

<!-- Unity’s animation system is based on the concept of Animation Clips, which contain information about how certain objects should change their position, rotation, or other properties over time. Each clip can be thought of as a single linear recording. Animation clips from external sources are created by artists or animators with 3rd party tools such as Max or Maya, or come from motion capture studios or other sources. -->
Unity 动画系统基于动画剪辑概念，包含了指定对象随着时间推移应该如何改变位置、旋转或其他属性的性息。每个剪辑可以认为是一段线性记录。外部导入的动画剪辑由第三方艺术或动画工具创建，例如 Max 和 Maya，或者来源于动作捕捉设置，或者其他来源。

<!-- Animation Clips are then organised into a structured flowchart-like system called an Animator Controller. The Animator Controller acts as a “State Machine” which keeps track of which clip should currently be playing, and when the animations should change or blend together. -->
动画剪辑 Animation Clip 被组织成类似流程图的系统，称为动画控制器 Animator Controller。动画控制器的行为像一台状态机，记录了当前应该播放的动画剪辑，以及什么时候应该切换或混合动画剪辑。

<!-- A very simple Animator Controller might only contain one or two clips, for example to control a powerup spinning and bouncing, or to animate a door opening and closing at the correct time. A more advanced Animator Controller might contain dozens of humanoid animations for all the main character’s actions, and might blend between multiple clips at the same time to provide a fluid motion as the player moves around the scene. -->
一个非常简单的动画控制器可能只包含一个或两个动画剪辑，例如控制一段旋转或弹跳动画，或者是在合适的时间打开或关闭一扇门。更高级的动画控制器可能包含许多人形动画，涵盖了主要角色的动作，并且当玩家在场景内移动时，可能同时混合多个动画剪辑来提供流畅的动作。

<!-- Unity’s Animation system also has numerous special features for handling humanoid characters which give you the ability to retarget humanoid animation from any source (Eg. motion capture, the asset store, or some other third-party animation library) to your own character model, as well as adjusting muscle definitions. These special features are enabled by Unity’s Avatar system, where humanoid characters are mapped to a common internal format. -->
Unity 动画系统还为人形角色提供了一些特殊功能，使你可以重构任意来源的人形动画（例如，动作捕捉，资源商店，或其他第三方动画库）到你的角色模型上，并且可以调整肌肉定义。这些特殊功能由 Unity 的 Avatar 系统提供，可以把人形角色映射到一种通用的内部格式。

<!-- Each of these pieces - the Animation Clips, the Animator Controller, and the Avatar, are brought together on a GameObject via the Animator Component. This component has a reference to an Animator Controller, and (if required) the Avatar for this model. The Animator Controller, in turn, contains the references to the Animation Clips it uses. -->
每个元素 — 动画剪辑、动画控制器、Avatar — 通过动画组件 Animator 组件合并到一个游戏对象上。这个组件引用了动画控制器和（如果需要）Avatar 系统，动画控制器又包含了对动画剪辑的引用。

![Diagram showing how the various parts of the animation system connect together](https://docs.unity3d.com/550/Documentation/uploads/Main/MecanimHowItFitsTogether.png)
<!-- > Diagram showing how the various parts of the animation system connect together -->
> 动画系统的各部分是如何连接在一起的

<!-- The above diagram shows the following: -->
上面的图形展示了：

<!-- 
1. Animation clips are imported from an external source or created within Unity. In this example, they are imported motion captured humanoid animations.
2. The animation clips are placed and arranged in an Animator Controller. This shows a view of an Animator Controller in the Animator window. The States (which may represent animations or nested sub-state machines) appear as nodes connected by lines. This Animator Controller exists as an asset in the Project window.
3. The rigged character model (in this case, the astronaut “Astrella”) has a specific configuration of bones which are mapped to Unity’s common Avatar format. This mapping is stored as an Avatar asset as part of the imported character model, and also appears in the Project window as shown.
4. When animating the character model, it has an Animator component attached. In the Inspector view shown above, you can see the [Animator Component]() which has both the [Animator Controller]() and the [Avatar]() assigned. The animator uses these together to animate the model. The Avatar reference is only necessary when animating a humanoid character. For other types of animation, only an Animator Controller is required.
 -->
1. 动画剪辑或者从外部资源导入，或者在 Unity 中创建。在这个例子中，是从动作捕捉导入的人形动画。
2. 动画剪辑被放入动画控制器。上图显示了动画视图中的动画控制器。这些状态（表示动画或嵌套的子状态机）以节点的形式展现，用线条连接。动画控制器作为一个资源显示在项目视图中。
3. 被控制的角色模型（在这里是宇航员 Astrella）拥有特殊的骨骼配置，被映射到 Unity 的通用 Avatar 格式。映射以 Avatar 资源的形式存储在角色模型下，做为被导入角色模型的一部分，显示在项目视图中。
4. 当赋予角色模型动画时，一个动画组件被添加。在上面的检视视图中，你可以看到动画组件被指定了动画控制器和 Avatar。动画组件同时使用两者来使模型动起来。只有人形角色才需要引用 Avatar。对于其他类型的动画，只需要一个动画控制器。

<!-- Unity’s animation system (Known as “Mecanim”) comes with a lot of concepts and terminology. If at any point, you need to find out what something means, go to our [Animation Glossary](https://docs.unity3d.com/550/Documentation/Manual/AnimationGlossary.html). -->
Unity 动画系统（称为 Mecanim）含有大量的概念和术语。在任何时候，如何你需要查找某个东西的含义，请访问 [动画术语](https://docs.unity3d.com/550/Documentation/Manual/AnimationGlossary.html)。

<!-- ## Legacy animation system -->
## 传统动画系统

<!-- While Mecanim is recommended for use in most situations, Unity has retained its legacy animation system which existed before Unity 4. You may need to use when working with older content created before Unity 4. For information on the Legacy animation system, see [this section](file:///Applications/Unity/Unity.app/Contents/Documentation/en/Manual/Animations.html) -->
尽管在大多数情况下推荐使用 Mecanim，但是 Unity 还保留了 Unity 4 之前的传统动画系统。如果使用 Unity 4 之前创建的老内容时，你可能需要用到它。有关传统动画系统的更多信息请查看 [这章](file:///Applications/Unity/Unity.app/Contents/Documentation/en/Manual/Animations.html)。

<!-- Unity intends to phase out the Legacy animation system over time for all cases by merging the workflows into Mecanim. -->
Unity 打算把传统动画系统的工作流程合并到 Mecanim，来逐步淘汰传统动画系统。
