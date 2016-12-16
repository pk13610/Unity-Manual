# Using Particle Systems in Unity
# 使用粒子系统

<!-- Unity implements Particle Systems with a component, so placing a Particle System in a Scene is a matter of adding a pre-made GameObject (menu: **GameObject > Create General > Particle System**) or adding the component to an existing GameObject (menu: **Component > Effects > Particle System**). Because the component is quite complicated, the Inspector is divided into a number of collapsible sub-sections or **modules** that each contain a group of related properties. Additionally, you can edit one or more systems at the same time using a separate Editor window accessed via the **Open Window** button in the Inspector. See documentation on the [Particle System component] and individual [Particle System modules] to learn more. -->

Unity 使用一个组件实现粒子系统。在场景中放置粒子系统的常用方式是，添加一个预制的游戏对象（菜单：GameObject > Create General > Particle Syste**），或者为一个现有的游戏对象添加粒子系统组件（菜单：**Component > Effects > Particle System**）。因为该组件相当复杂，所以检视视图被分割成数个可折叠的部分或 **模块**，每个模块包含一组相关属性。另外，在检视视图中点击 **Open Window** 按钮，可以弹出单独的编辑窗口。相关信息请参阅 [粒子系统组件] 和 [粒子系统模块]。

[Particle System component]: https://docs.unity3d.com/Manual/class-ParticleSystem.html
[Particle System modules]: https://docs.unity3d.com/Manual/ParticleSystemModules.html
[粒子系统组件]: https://docs.unity3d.com/Manual/class-ParticleSystem.html
[粒子系统模块]: https://docs.unity3d.com/Manual/ParticleSystemModules.html

<!-- When a GameObject with a Particle System is selected, the Scene view contains a small **Particle Effect** panel, with some simple controls that are useful for visualising changes you make to the system’s settings. -->

当选中具有粒子系统的游戏对象时，场景视图将包含一个 **粒子效果** 小面板，其中包含一些简单的控件，用于可视化对系统设置的更改。

![](https://docs.unity3d.com/uploads/Main/PartSysEffectPanel.png)

<!-- The **Playback Speed** allows you to speed up or slow down the particle simulation, so you can quickly see how it looks at an advanced state. The **Playback Time** indicates the time elapsed since the system was started; this may be faster or slower than real time depending on the playback speed. The **Particle Count** indicates how many particles are currently in the system. The playback time can be moved backwards and forwards by clicking on the **Playback Time** label and dragging the mouse left and right. The buttons at the top of the panel can be used to pause and resume the simulation, or to stop it and reset to the initial state. -->

**播放速度 Playback Speed** 用于加速或减慢粒子模拟，以高级状态快速查看粒子效果。**播放时间 Playback Time** 表示自系统启动以来流逝的的时间；这个时间可能比真实时间更快或更慢，取决于播放速度。**粒子计数 Particle Count** 表示当前系统中的粒子数量。通过点击 **播放时间 Playback Time** 标签并左右拖动鼠标，可以向后和向前移动播放时间。面板顶部的按钮用于暂停和恢复模拟，或者停止并复位到初始状态。

<!-- ## Varying properties over time -->
## 随时间改变属性

<!-- Many of the numeric properties of particles or even the whole Particle System can vary over time. Unity provides several different methods of specifying how this variation happens: -->

粒子或个粒子系统的许多数值型属性可以随时间变化。Unity 提供了几种不同的方法来指定变化如何发生：

<!-- 
* **Constant**: The property’s value is fixed throughout its lifetime.
* **Curve**: The value is specified by a curve/graph.
* **Random Between Two Constants**: Two constant values define the upper and lower bounds for the value; the actual value varies randomly over time between those bounds.
* **Random Between Two Curves**: Two curves define the upper and lower bounds of the the value at a given point in its lifetime; the current value varies randomly between those bounds.
 -->
* **常量 Constant** 属性值在其生命周期中是固定的。
* **曲线 Curve** 属性值由一条曲线或图形指定。
* **在两个常量之间随机 Random Between Two Constants** 两个常量值分别定义属性值的上限和下限；真实值随着时间在这个范围内随机变化。
* **在两条曲线之间随机 Random Between Two Curves** 两条曲线分别定义属性值在其生命周期内给点时间点上的上限和下限；当前值在这个范围内随机变化。

<!-- Similarly, the **Start Color** property in the main module has the following options: -->

类似的，主模块中的 **起始颜色 Start Color** 属性具有以下选项：

<!-- 
* **Color**: The particle start color is fixed throughout the system’s lifetime.
* **Gradient**: Particles are emitted with a start color specified by a gradient, with the gradient representing the lifetime of the Particle System.
* **Random Between Two Colors**: The starting particle color is chosen as a random linear interpolation between the two given colors.
* **Random Between Two Gradients**: Two colors are picked from the given Gradients at the point corresponding to the current age of the system; the starting particle color is chosen as a random linear interpolation between these colors.
 -->
* **颜色 Color**：粒子的起始颜色在其生命周期中是固定的。
* **渐变 Gradient**：以渐变指定的起始颜色发射粒子；渐变表示粒子系统的生命周期。
* **在两个颜色之间随机 Random Between Two Colors**：粒子的起始颜色为两个给定颜色之间的随机线性插值。
* **在两个渐变之前随机 Random Between Two Gradients**：在粒子系统的当前年龄点上，从给定的两个渐变上选取两个颜色；粒子的起始颜色为这两个颜色之间的随机线性插值。

<!-- For other color properties, such as **Color over Lifetime**, there are two separate options: -->

对于其他颜色属性，例如 **颜色随生命周期变化 Color over Lifetime**，提供了两个单独的选项：

<!-- 
* **Gradient**: The color value is taken from a gradient which represents the lifetime of the Particle System.
* **Random Between Two Gradients**: Two colors are picked from the given gradients at the point corresponding to the current age of the Particle System; the color value is chosen as a random linear interpolation between these colors.
 -->
* **渐变 Gradient**：以渐变指定的起始颜色发射粒子；渐变表示粒子系统的生命周期。
* **在两个渐变之前随机 Random Between Two Gradients**：在粒子系统的当前年龄点上，从给定的两个渐变上选取两个颜色；粒子的起始颜色为这两个颜色之间的随机线性插值。

<!-- Color properties in various modules are multiplied together per channel to calculate the final particle color result. -->

各模块中的颜色属性在每个通道上相互叠加，以计算出最终的粒子颜色。

<!-- ## Animation bindings -->
## 绑定动画

<!-- All particle properties are accessible by the Animation system, meaning you can keyframe them in and control them from your animations. -->

动画系统可以访问所有的粒子属性，这意味可以为它们添加关键帧，并用动画控制它们。

<!-- To access the Particle System’s properties, there must be an Animator component attached to the Particle System’s GameObject. An Animation Controller and an Animation are also required. -->

在一个绑定了粒子系统的游戏对象上，为了访问粒子系统的属性，必须再绑定一个动画组件。还需要一个动画控制器和一个动画剪辑。

![To animate a Particle System, add an Animator Component, and assign an Animation Controller with an Animation.](https://docs.unity3d.com/uploads/Main/ParticleSystemAnimatorComponent.png)
<!-- > To animate a Particle System, add an Animator Component, and assign an Animation Controller with an Animation. -->
> 要为粒子系统添加动画，请添加一个动画组件，并分配一个带有动画剪辑的动画控制器。

<!-- To animate a Particle System property, open the **Animation Window** with the GameObject containing the Animator and Particle System selected. Click **Add Property** to add properties. -->

为了粒子系统的属性添加动画，选中包含了动画控制器和粒子系统的游戏对象，然后打开 **动画视图 Animation Window**。点击 **添加属性 Add Property**。

![Add properties to the animation in the Animation Window.](https://docs.unity3d.com/uploads/Main/ParticleSystemAnimationWindow.png)
<!-- > Add properties to the animation in the Animation Window. -->
> 在动画视图 Animation Window 中，添加一个属性到动画剪辑中。

<!-- Scroll to the right to reveal the add controls. -->
向右滚动以显示添加控件。



![](https://docs.unity3d.com/uploads/Main/ParticleSystemAnimationScrollRight.png)

<!-- Note that for curves, you can only keyframe the overall **curve multiplier**, which can be found next to the curve editor in the **Inspector**. -->

请注意，为曲线添加关键帧时，添加的是整条曲线的 **倍增器**，你可以在 **检视视图** 的曲线编辑器中看到。
