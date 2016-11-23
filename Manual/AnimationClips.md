<!-- Unity Manual > Animation > Animation Clips -->
<!-- Unity 手册 > 动画 > 动画剪辑 -->

<!-- # Animation Clips -->
# 动画剪辑

<!-- Animation Clips are one of the core elements to Unity’s animation system. Unity supports importing animation from external sources, and offers the ability to create animation clips from scratch within the editor using the Animation window. -->
动画剪辑是 Unity 动画系统的核心元素。Unity 不仅支持从外部源导入动画，而且支持在编辑器的动画视图中创建和编辑动画剪辑。

<!-- ## Animation from External Sources -->
## 从外部源导入动画

<!-- Animation clips imported from external sources could include: -->
从外部源导入的动画剪辑可能包括：

<!-- 
* Humanoid animations captured at a motion capture studio
* Animations created from scratch by an artist in an external 3D application (such as 3DS Max or Maya)
* Animation sets from 3rd-party libraries (eg, from Unity’s asset store)
* Multiple clips cut and sliced from a single imported timeline.
 -->
* 动作捕捉工作室捕捉的人形动画
* 设计师通过外部 3D 程序（例如 3D Max 或 Maya）创建的动画
* 第三方的动画集合库（例如来自于 Unity Asset store）
* 导入的单个时间线等分切割为多个动画剪辑

![An example of an imported animation clip, viewed in Unitys inspector window](https://docs.unity3d.com/uploads/Main/AnimationClipInspector.png)
<!-- > An example of an imported animation clip, viewed in Unity’s inspector window  -->
> 一段导入的动画剪辑在 Unity 检视视图中的示例

<!-- ## Animation Created and Edited Within Unity -->
## 在 Unity 中创建和编辑动画

<!-- Unity’s Animation Window also allows you to create and edit animation clips. These clips can animate: -->

Unity 的动画视图允许创建和编辑动画剪辑。这些剪辑支持的动画包括：

<!-- 
* The position, rotation and scale of GameObjects
* Component properties such as material colour, the intensity of a light, the volume of a sound
* Properties within your own scripts including float, int, Vector and boolean variables
* The timing of calling functions within your own scripts
 -->
* 游戏对象的位置，旋转和尺寸。
* 组件属性，例如，材质颜色、光照强度、声音音量。
* 脚本属性，包括浮点型、整型、矢量和布尔变量。
* 脚本调用的方法的时机。

![An example of Unitys Animation window being used to animate parameters of a component - in this case, the intensity and range of a point light](https://docs.unity3d.com/uploads/Main/AnimationViewSimpleParameters.png)
<!-- > An example of Unity’s Animation window being used to animate parameters of a component - in this case, the intensity and range of a point light -->
> Unity 动画视图中，一个组件动画参数的示例。在这个示例中，是一个点光源的光照强度和光照范围。
