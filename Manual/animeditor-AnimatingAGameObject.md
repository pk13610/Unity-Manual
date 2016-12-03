<!-- Unity Manual > Animation > Animation Clips > Animation Window Guide > Animating a Game Object -->

# Animating a Game Object
# 让游戏对象动起来

<!-- Once you have saved the new Animation clip Asset, you are ready to begin adding keyframes to the clip. To begin editing an Animation Clip for the selected Game Object, click on the Animation Record button. This will enter Animation Record Mode, where changes to the Game Object are recorded into the Animation Clip. -->
一旦你保存了新动画剪辑，就可以开始为动画剪辑添加关键帧了。开始为选中的游戏对象编辑动画剪辑之前，需要先点击动画记录按钮，进入动画记录模式，此时，对该游戏对象的修改会被记录到动画剪辑。

![Record button](https://docs.unity3d.com/uploads/Main/AnimationEditorAnimationModeButton.png)
<!-- > Record button -->
> 记录按钮

<!-- You can stop the **Animation Record Mode** at any time by clicking the **Animation Mode button** again. This will revert the **Game Object** to the state it was in prior to entering the Animation Mode. -->
任何时候，你都可以通过再次点击 **动画模式按钮**，从而退出 **动画记录模式**。这一操作将把该 **游戏对象** 的状态恢复到进入动画记录模式之前。

<!-- The changes you make to the GameObject will be recorded as keyframes at the current time shown by the red line in the Animation Window. -->
你对该游戏对象所做的修改将被记录为关键帧，红线所指示的时间即为关键帧的时间。

<!-- You can animate any property of the object by manipulating the object while in Animation Record Mode. Moving, Rotating or Scaling the object will add corresponding keyframes for those properties in the animation clip. Adjusting values directly in the object’s inspector will also add keyframes while in Record mode. This applies to any property in the inspector, including numeric values, checkboxes, colours, and most other values. -->
在动画记录模式中，通过修改游戏对象，你可以为任何属性添加动画。无论是移动、旋转或缩放游戏对象，对应的属性都将被添加到动画剪辑的相应关键帧中。在游戏对象的检视视图中修改值，也会添加关键帧。支持检视视图中的任意属性，例如，数值型、复选框、颜色等大部分属性。

<!-- Any animated properties of the GameObject are shown listed in the property list on the left-hand side of the Animation Window. Properties which are not animated are not shown in this window. Any new properties that you animate, including properties on child objects, are added to the property list area as soon as you start animating them. -->
游戏对象的动画属性被罗列在动画视图左侧的属性列表中。不参与动画的属性不会显示在视图中。新增加的动画属性，包括子对象上的属性，同样会被添加到属性列表中。

<!-- **Transform** properties are special in that the **.x**, **.y**, and **.z** properties are linked, so that curves are added three at a time. -->
**Tranform** 组件的属性有些特别，属性 **.x**、**.y** 和 **.z** 是连接在一起的，所以一次会添加 3 条曲线。

<!-- You can also add animatable properties to the current GameObject (and its children) by clicking the **Add Property** button. Clicking this button shows a pop up list of the GameObject’s animatable properties. These correspond with the properties you can see listed in the inspector. -->
你也可以点击 **添加属性按钮**，为当前游戏对象（和它的子对象）添加动画属性。点击这个按钮，将弹出一个浮层，现实该游戏对象上所有支持动画的属性。这些属性与检视试图中列出的属性一一对应。

![The animatable properties of a GameObject are revealed when you click the Add Property button](https://docs.unity3d.com/uploads/Main/AnimationEditorMatchesInspector.png)
<!-- > The animatable properties of a GameObject are revealed when you click the **Add Property** button -->
> 当点击 **Add Property** 按钮，游戏对象上可参与动画的属性被显示出来。

<!-- When in **Animation Mode**, a red vertical line will show which frame of the **Animation Clip** is currently previewed. The **Inspector** and **Scene** View will show the Game Object at that frame of the Animation Clip. The values of the animated properties at that frame are also shown in a column to the right of the property names. -->
在 **动画录制模式** 中，红色的垂直线表示当前预览的是动画剪辑的哪一桢。**检视视图** 和 **场景视图** 将显示游戏对象在该桢的状态。动画属性在该桢的值显示在属性名称的右侧。

<!-- In Animation Mode a red vertical line shows the currently previewed frame. -->
在动画录制模式中，红色的垂直线表示当前预览的桢。

![Current frame](https://docs.unity3d.com/uploads/Main/AnimationEditorPreviewFrame.png)
<!-- > Current frame -->
> 当前桢

<!-- ### Time Line -->
### 时间轴

<!-- You can click anywhere on the **Time Line** to preview or modify that frame in the Animation Clip. The numbers in the **Time Line** are shown as seconds and frames, so 1:30 means 1 second and 30 frames. -->
在动画剪辑中，你可以点击 **时间轴** 上的任意一点，来预览或修改该桢。**时间轴** 上的数字是秒数和帧数，所以 1:30 的意思是 1 秒加 30 桢。

![Time Line](https://docs.unity3d.com/uploads/Main/AnimationEditorTimeLine.png)
<!-- > Time Line -->
> 时间轴

<!-- ### Animation Mode -->
### 动画模式

<!-- In **Animation Mode** you can move, rotate, or scale the **Game Object** in the **Scene View**. This will automatically create **Animation Curves** for the position, rotation, and scale properties of the **Animation Clip** if they didn’t already exist, and keys on those Animation Curves will automatically be created at the currently previewed frame to store the respective **Transform** values you changed. -->
在 **动画模式** 下，你可以在 **场景视图** 中移动、旋转或缩放 **游戏对象**。如果位置、旋转或缩放属性在 **动画剪辑** 中不存在的话，这些操作将自动创建动画曲线；并且，自动在当前预览的桢上创建关键帧，以存储改变后的 **Transform** 值。

<!-- You can also use the **Inspector** to modify any of the other animatable properties of the **Game Object**. This too will create **Animation Curves** as needed, and create **keys** on those Animation Curves at the currently previewed frame to store your changed values. -->
你也可以在 **检视视图** 中修改 **游戏对象** 的任意动画属性。如果需要的话，这些操作也会自动创建 **动画曲线**，并且在当前预览的动画曲线上创建 **关键帧**，以存储改变后的值。

<!-- ### Keyframe Creation -->
### 创建关键帧

<!-- You can manually create a **keyframe** using the **Add Keyframe button**. This will create a key for all the properties that are currently selected in the **Animation View**. This is useful for selectively adding keys to specific properties only. -->
你可以使用 **添加关键桢按钮** 手动创建一个 **关键帧**。这个操作将会为 **动画视图** 中当前选中的所有属性创建一个关键帧。也就是说，你可以有选择性地只为特定属性添加关键帧。

![The Add Keyframe Button](https://docs.unity3d.com/uploads/Main/AnimationEditorKeyframeButton.png)
<!-- > The Add Keyframe Button -->
> 添加关键桢按钮