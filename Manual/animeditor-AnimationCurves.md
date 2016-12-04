<!-- Unity Manual > Animation > Animation Clips > Animation Window Guide > Using Animation Curves -->

<!-- # Using Animation Curves -->
# 使用动画曲线

<!-- ## The Property List -->
## 属性列表

<!-- In an **Animation Clip**, any animatable property can have an **Animation Curve**, which means that the Animation Clip controls how that property changes over time. In the property list area of the **Animation View** (on the left), all the currently animated properties are listed. With the Animation View in Dope Sheet mode, the animated values for each property appear only as linear tracks, however in Curves mode you are able to see the the changing values of properties visualised as lines on graph. Whichever mode you use to view, the curves still exist - the Dope Sheet mode just gives you a simplified view of the data showing only when the keyframes occur. -->
在一段 **动画剪辑** 中，任意动画属性都可以拥有 **动画曲线**，也就是说，动画剪辑控制着属性如何随时间变化。在 **动画视图**（左侧）的属性列表区域，罗列出了当前所有参与动画的属性。当动画视图处于关键帧清单模式，每个属性的值是一个条直线轨道，但是在曲线模式下，正在改变的属性值被可视化为曲线图形。无论你用哪种模式查看，曲线一直存在 — 关键桢清单模式只是简单的关键帧数据预览。

<!-- In **Curves** mode, the **Animation Curves** have colored curve indicators, each colour representing the values for one of the currently selected properties in the property list. For information on how to add curves to an animation property, see the section on [Using the Animation View](https://docs.unity3d.com/550/Documentation/Manual/animeditor-UsingAnimationEditor.html). -->
在 **曲线模式** 下，**动画曲线** 带有颜色标记，每种颜色代表一个当前选中属性的值。关于如何为动画属性添加曲线，请阅读 [Using the Animation View](https://docs.unity3d.com/550/Documentation/Manual/animeditor-UsingAnimationEditor.html) 一章。

![Animation Curves with the color indicators visible. In this example, the green indicator matches the Y position curve of a bouncing cube animation](https://docs.unity3d.com/550/Documentation/uploads/Main/AnimationEditorBouncingCube.gif)
<!-- > Animation Curves with the color indicators visible. In this example, the green indicator matches the Y position curve of a bouncing cube animation -->
> 动画曲线带有可视化的颜色标记。在这个例子中，绿色线条表示弹跳立方体的 Y 轴动画。

<!-- ### Understanding Curves, Keys and Keyframes -->
### 理解曲线、关键点、关键帧

<!-- An **Animation Curve** has multiple **keys** which are control points that the curve passes through. These are visualized in the **Curve Editor** as small diamond shapes on the curves. A frame in which one or more of the shown curves have a **key** is called a **keyframe**. -->
一条 **动画曲线** 含有（穿过）多个 **关键点**。在 **曲线编辑器** 中，关键点显示为曲线上的小菱形。含有一个或多个**关键点**的桢称为 **关键帧**。

<!-- If a property has a **key** in the currently previewed frame, the curve indicator will have a diamond shape, and the property list will also have diamond shapes next to the value. -->
如果某个属性在当前预览的桢上有一个 **关键点**，对应的曲线上也会有一个小菱形，在属性列表中也会有一个小菱形紧跟在值后面。

![The Rotation.y property has a key at the currently previewed frame.](https://docs.unity3d.com/550/Documentation/uploads/Main/AnimationWindowCurveKeyframe.png)
<!-- > The **Rotation.y** property has a **key** at the currently previewed frame. -->
> **属性 Rotation.y** 在当前预览桢上有一个**关键点**。

<!-- The **Curve Editor** will only show curves for the properties that are selected. If multiple properties are selected in the property list, the curves will be shown overlaid together. -->
**曲线编辑器** 只会显示当前选中属性的曲线。如果在属性列表中选中了多个属性，曲线将叠加显示。

![When multiple properties are selected, their curves are shown overlaid together in the Curves Editor](https://docs.unity3d.com/550/Documentation/uploads/Main/AnimationWindowMultipleCurves.png)
<!-- > When multiple properties are selected, their curves are shown overlaid together in the Curves Editor -->
> 当多个属性被选中时，它们的曲线叠加显示在曲线编辑器中。

<!-- ## Adding and Moving Keyframes -->
## 添加和移动关键帧

![](https://docs.unity3d.com/550/Documentation/uploads/Main/AnimationEditorAddKeyframeButton.png)

<!-- You can add a **keyframe** at the currently previewed frame by clicking the **Keyframe button**. -->
通过点击 **关键帧按钮**，你可以在当前预览的桢上添加一个 **关键帧**。

<!-- A **keyframe** can be added at the currently previewed frame by clicking the **Keyframe button**. This will add a keyframe to all currently selected curves. Alternatively you can add a keyframe to a single curve at any given frame by double-clicking the curve where the new **keyframe** should be. It is also possible to add a **keyframe** by right-clicking the **Keyframe Line** and select **Add Keyframe** from the context menu. Once placed, **keyframes** can be dragged around with the mouse. It is also possible to select multiple **keyframes** to drag at once. **Keyframes** can be deleted by selecting them and pressing **Delete**, or by right-clicking on them and selecting **Delete Keyframe** from the context menu. -->

通过点击 **关键帧按钮**，你可以在当前预览的桢上添加一个 **关键帧**。这一操作将会为当前所有选中的曲线添加关键帧。或者，通过在想要新增 **关键帧** 的位置双击曲线，你可以为单条曲线添加关键帧。也可以右键点击 **关键帧线**，在上下文菜单中选择 **添加关键帧**，来添加 **关键帧**。一旦被添加，就可以用鼠标拖动 **关键帧**。也可以一次选中多个关键帧，然后一起拖动。通过先选中关键桢，然后按下删除键，可以删除关键帧；或者先右键点击关键帧，然后在上下文菜单中选择 **删除关键帧**。

<!-- ## Supported Animatable Properties -->
## 支持动画的属性

<!-- The **Animation View** can be used to animate much more than just the position, rotation, and scale of a **Game Object**. The properties of any **Component** and **Material** can be animated - even the public variables of your own scripts components. Making animations with complex visual effects and behaviors is only a matter of adding **Animation Curves** for the relevant properties. -->
**动画视图** 不仅仅支持 **游戏对象的** 位置、旋转和缩放。任何 **组件** 和 **材质** 的属性都可以被赋予动画 — 甚至是脚本组件的公共变量。通过添加 **动画曲线**，可以用可视化的方式，为相关属性制作复杂的动画和行为。

<!-- The following types of properties are supported in the animation system: -->
动画系统支持下面类型的属性：

* Float
* Color
* Vector2
* Vector3
* Vector4
* Quaternion
* Boolean

<!-- Arrays are not supported and neither are structs or objects other than the ones listed above. -->
不支持数组，不在上面列表中的结构和对象也不支持。

<!-- For boolean properties, a value of **0** equals **False** while any other value equals **True**. -->
对于布尔型属性，**0** 等价于 **False**，其他值等价于 **True**。

<!-- Here are a few examples of the many things the **Animation View** can be used for: -->
下面是一些可以用动画视图制作的示例：

<!-- 
* Animate the **Color** and **Intensity** of a **Light** to make it blink, flicker, or pulsate.
* Animate the **Pitch** and **Volume** of a looping **Audio Source** to bring life to blowing wind, running engines, or flowing water while keeping the sizes of the sound assets to a minimum.
* Animate the **Texture Offset** of a **Material** to simulate moving belts or tracks, flowing water, or special effects.
* Animate the **Emit** state and **Velocities** of multiple **Ellipsoid Particle Emitters** to create spectacular fireworks or fountain displays.
* Animate variables of your own script components to make things behave differently over time.
 -->
* 为 **灯光** 的 **颜色** 和 **强度** 制作动画，制作闪烁、摇曳、搏动效果。
* 为循环播放的 **声音源** 的 **音调** 和 **音量** 制作动画，制作生动的吹风、运行中的发动机或流水效果，同时保持音频文件最小化。
* 为 **材质球** 的 **贴图偏移** 制作动画，模拟移动履带、移动轨道、流水或特有的效果。
* 为多个 **椭圆体粒子发射器** 的 **发射** 状态和 **速度** 制作动画，制作壮丽烟火或喷泉效果。
* 为脚步组件的变量制作动画，制作随时间变化的行为。

<!-- When using **Animation Curves** to control game logic, please be aware of the way animations are [played back and sampled](https://docs.unity3d.com/550/Documentation/Manual/AnimationScripting.html) in Unity. -->
当使用 **动画曲线** 控制游戏逻辑时，需要注意的是，在 Unity 中，动画是[重复播放和片段化](https://docs.unity3d.com/550/Documentation/Manual/AnimationScripting.html)的。

<!-- ## Rotation Interpolation Types -->
## 旋转插值类型

<!-- In Unity rotations are internally represented as **Quaternions**. Quaternions consist of **.x**, **.y**, **.z**, and **.w** values that should generally not be modified manually except by people who know exactly what they’re doing. Instead, rotations are typically manipulated using **Euler Angles** which have **.x**, **.y**, and **.z** values representing the rotations around those three respective axes. -->
在 Unity 内部，旋转角度是用 **四元数 Quaternions** 表示的。四元数包含 **.x**、**.y**、**.z** 和 **.w**，通常情况下，不应该手动修改它们的值，除非你明确知道它们的工作原理。相反，旋转角度通常用**欧拉角 Euler Angules**表示，它包括 **.x**、**.y** 和 **.z**，分别表示围绕对应坐标轴旋转的角度。

<!-- When interpolating between two rotations, the interpolation can either be performed on the **Quaternion** values or on the **Euler Angles** values. The **Animation View** lets you choose which form of interpolation to use when animating **Transform** rotations. However, the rotations are always shown in the form of **Euler Angles** values no matter which interpolation form is used. -->
在两个旋转角度之间插值时，既可以基于 **四元数 Quaternion**，也可以基于 **欧拉角 Euler Angles**。当为变换组件 Transform 的旋转制作动画时，**动画视图** 允许选择哪种插值类型。不过，无论使用哪种插值类型，旋转角度总是以 **欧拉角 Euler Angles**格式显示。

![Transform rotations can use Euler Angles interpolation or Quaternion interpolation.](https://docs.unity3d.com/550/Documentation/uploads/Main/AnimationEditorQuaternionInterpolationMenu.png)
<!-- > Transform rotations can use Euler Angles interpolation or Quaternion interpolation. -->
> 变换组件 Transform 的旋转角度可以使用**欧拉角 Euler Angles** 插值或**四元数 Quaternion** 插值。

<!-- ### Quaternion Interpolation -->
### 四元数 Quaternion 插值

<!-- Quaternion interpolation always generates smooth changes in rotation along the shortest path between two rotations. This avoids rotation interpolation artifacts such as Gimbal Lock. However, Quaternion interpolation cannot represent rotations larger than 180 degrees, due to its behaviour of always finding the shortest path. (You can picture this by picking two points on the surface of a sphere - the shortest line between them will never be more than half-way around the sphere). -->
在旋转时，四元数 Quaternion 插值总是沿着两个旋转角度之间的最短路径生成平滑动画。从而避免不必要的旋转插值，例如万向节死锁 Gimbal Lock 这样的人造物体。不过，四元苏 Quaternion 插值不能表示大于 180 度的旋转角度，因为它的行为总是寻找最短路径。（你可以设想，在球体的表面选取两个点 — 它们之间的最短路径永远不会大于球体的一半）。

<!-- If you use Quaternion interpolation and set the numerical rotation values further than 180 degrees apart, the curve drawn in the animation window will still appear to cover more than a 180 degree range, however the actual rotation of the object will take the shortest path. -->
如果你使用四元数 Quaternion 插值，并且设置大于 180 度的旋转角度，动画视图中绘制的曲线依然显示为大于 180 度，但实际上在旋转物体将采用最短路径。

![Placing two keys 270 degrees apart when using Quaternion interpolation will cause the interpolated value to go the other way around, which is only 90 degrees. The magenta curve is what is actually shown in the animation window. The true interpolation of the object is represented by the yellow dotted line in this screenshot, but does not actually appear in the editor.](https://docs.unity3d.com/550/Documentation/uploads/Main/AnimationEditorQuaternionInterpolation.png)
<!-- > Placing two keys 270 degrees apart when using Quaternion interpolation will cause the interpolated value to go the other way around, which is only 90 degrees. The magenta curve is what is actually shown in the animation window. The true interpolation of the object is represented by the yellow dotted line in this screenshot, but does not actually appear in the editor. -->
> 使用四元数 Quaternion 插值，设置两个相差 270 度的关键点，将导致插值执行另一个路径，实际上只有 90 度。动画视图中现实的是洋红色曲线。在这张截图中，对象真正的插值用黄色点线表示，并不会真正显示在编辑器中。

<!-- When using Quaternion interpolation for rotation, changing the keys or tangents of either the x, y or z curve may also change the values of the other two curves, since all three curves are created from the internal Quaternion representation. When using Quaternion interpolation, keys are always linked, so that creating a key at a specific time for one of the three curves (x, y or z) will also create a key at that time for the other two curves. -->
当使用四元数 Quaternion 插值类型表示旋转角度时，改变关键点，或者 x、y、z 曲线之一的切线，可能会改变另外两条曲线的值，因为这 3 条曲线是由内部的四元数 Quaternion 创建的。当使用四元数 Quaternion 插值类型时，关键点之间是关联的，所以，在某个特定时间点，为 3 条曲线中的一条（x、y 或 z）创建关键点时，将同时为两外两条曲线创建关键点。

<!-- ### Euler Angles Interpolation -->
### 欧拉角 Euler Angles 插值

<!-- Euler Angles interpolation is what most people are used to working with. Euler Angles can represent arbitrary large rotations and the **.x**, **.y**, and **.z** curves are independent from each other. Euler Angles interpolation can be subject to artifacts such as Gimbal Lock when rotating around multiple axes at the same time, but are intuitive to work with for simple rotations around one axis at a time. When Euler Angles interpolation is used, Unity internally bakes the curves into the Quaternion representation used internally. This is similar to what happens when importing animation into Unity from external programs. Note that this curve baking may add extra keys in the process and that tangents with the **Constant** tangent type may not be completely precise at a sub-frame level. -->
大多数人使用的其实是欧拉角 Euler Angles 插值。欧拉角 Euler Angles 可以表示任意大的旋转角度，并且，**.x**、**.y** 和 **.z** 曲线是彼此独立的。当同时围绕多个坐标轴旋转时，欧拉角 Euler Angles 插值可以基于某个物体，例如万向节死锁 Gimbal Lock，但是可以一次只围绕一条坐标轴旋转，更加简单和符合直觉。有点类似于从外部程序导入动画到 Unity 中。需要注意的是，当烘培曲线时可能添加额外的关键点，并且，在子桢中，常量类型的切线可能不完全精确。



