> 当前为 5.4 版本，稍后将升级到 5.5。在 5.5 中，本节内容被拆分成了多个小节。

<!-- Unity Manual > Animation > Animation Clips > Animation Window Guide > Using the Animation View -->
<!-- Unity 手册 > 动画 > 动画剪辑 > 动画视图指南 > 使用动画视图 -->

<!-- # Using the Animation View -->
# 使用动画视图

<!-- The Animation View can be used to preview and edit Animation Clips for animated Game Objects in Unity. The Animation View can be opened from the Window->Animation menu. -->
在 Unity 中，动画视图用于预览和编辑游戏对象的动画剪辑。动画视图可以通过菜单 Window -> Animation 打开。

<!-- ## Viewing Animations on a GameObject -->
## 查看游戏对象上的动画

<!-- The Animation View is tightly integrated with the Hierarchy View, the Scene View, and the Inspector. Similar to the Inspector, the Animation View will show the timeline and keyframes of the animation for the currently selected Game Object. You can select a Game Object using the Hierarchy View or the Scene View. (If you select a Prefab in the Project View you can inspect its animation timeline as well, but you have to drag the Prefab into the Scene View in order to be able to edit the animation.) -->
动画视图和层级视图、场景视图以及检视视图紧密耦合。类似于检视视图，动画视图将显示当前选中对象的动画的时间轴和关键帧。你也可以在层级视图或场景视图中选择一个游戏对象查看。（如果你在项目视图中选择了一个预制体 Prefab，同样可以查看动画时间线，但是只有先拖动预制体 Prefab 到场景视图中，才能编辑动画。）

<!-- ## The Animated Properties List -->
## 动画属性列表

![The Animation View (left) shows the animation used by the currently selected Game Object, and its child objects if they are also controlled by this animation. The scene view and hierarchy view are shown on the right, demonstrating that the animation view shows the currently selected object. ](https://docs.unity3d.com/uploads/Main/AnimationEditorShowsSelected.png)
<!-- > The Animation View (left) shows the animation used by the currently selected Game Object, and its child objects if they are also controlled by this animation. The scene view and hierarchy view are shown on the right, demonstrating that the animation view shows the currently selected object. -->

> 动画视图（左侧）显示了当前选中的游戏对象所使用的动画，如果它的子对象也使用了动画，那么也会显示在这里。场景视图和层级视图显示在右侧，可以看到当前选中的游戏对象。

<!-- At the left side of the **Animation View** is a list of the animated properties. In a newly created clip where no animation has yet been recorded, this list will be empty. When you begin to animate various properties within this clip, the animated properties will appear here. If the animation controls multiple child objects, the list will also include a hierarchical list of each child object’s animated properties. In the example above, various parts of the Robot Arm hierarchy are all animated within the same animation clip, and each animated GameObject is shown according to its hierarchical position in relation to the root object which has the Animator component attached. -->
动画视图的左侧是动画属性列表。在一个新创建的动画剪辑中，这个列表为空，没有记录任何动画的。当你开始让各种属性动起来时，参与动画的属性将显示在这里。如果动画控制了多个子对象，这个列表还会以层级的方式显示子对象的动画属性。在上面的例子中，机械手臂的各个部分都由同一个动画剪辑驱动，每个被它控制的游戏对象，按照它们在附加了动画组件的根元素中的层级关系显示。

<!-- Each property can be folded and unfolded to reveal the exact values recorded at each keyframe. The value fields will show the interpolated value if the playback head (the red line) is in-between keyframes. These fields can be edited directly. If changes are made when the playback head is over a keyframe, the keyframe’s values will be modified. If changes are made when the playback head is between keyframes (and therefore the value shown was an interpolated value), a new keyframe will be created at that point with the new value that you entered. -->
每个属性可以折叠和展开，从而显示每个关键帧记录的精确值。如果在关键帧之间移动磁头（红线），属性右侧的值域将显示补间值。值域可以直接编辑。如果磁头位于某个关键帧上，修改值域将直接修改该关键帧的值。如果磁头在关键帧之间（此时值域显示的是补间值），修改值域将在磁头位置创建一个新的关键帧，值域的值即为该关键帧的值。

![An unfolded property in the Animation View, allowing the keyframe value to be typed in directly. In this image, an interpolated value is shown because the playback head (the red line) is between keyframes. Entering a new value at this point would create a new keyframe.](https://docs.unity3d.com/uploads/Main/AnimationEditorUnfoldedProperty.png)
<!-- > An unfolded property in the Animation View, allowing the keyframe value to be typed in directly. In this image, an interpolated value is shown because the playback head (the red line) is between keyframes. Entering a new value at this point would create a new keyframe. -->
> 在动画视图中展开属性列表，允许直接键入关键帧的值。在这张图中，因为磁头（红线）位于关键帧之间，所以显示的是补间值。如果在该位置输入一个新值，将创建一个新关键帧。

<!-- ## The Animation Timeline -->
## 动画时间轴

<!-- On the right side of the Animation View is the timeline for the current clip. The keyframes for each animated property appear in this timeline. The timeline view has two modes, “Dope Sheet” and “Curves”. You can toggle between these modes by clicking the respective buttons at the bottom of the animated property list area: -->
动画视图的右侧是每个动画剪辑的时间轴。每个动画属性的关键帧显示在时间轴中。时间轴有两种模式：关键帧清单模式和曲线模式。通过点击动画属性列表底部相应的按钮，可以在两种模式之间切换：

![The Dope Sheet / Curves view buttons](https://docs.unity3d.com/uploads/Main/AnimationEditorDopeSheetCurvesButtons.png)
<!-- > The Dope Sheet / Curves view buttons -->
> 关键帧清单模式/曲线模式按钮

<!-- These offer two alternate views of the animation timeline and keyframe data, with each mode having its own benefits. -->
这两种模式可以彼此替换，都可以现实动画的时间轴和关键帧数据，但是各有优势。

<!-- ## Dope Sheet Timeline Mode -->
## 关键帧清单模式

<!-- The Dope Sheet mode offers a more compact view, allowing you to view each property’s keyframe seqence in an individual horizontal track. This allows you have a simple overview of the keyframe timing for multiple properties or objects. -->
关键帧清单模式提供更紧凑的视图，允许你在水平轨道上独立地查看每个属性的关键帧序列。可以让你简单地描述多个属性或对象的关键帧时间设置。

![Here the Animation Window is in Dope Sheet mode, showing the keyframe positions all the animated properties within the Animation Clip](https://docs.unity3d.com/uploads/Main/AnimationEditorDopeSheetView.png)
<!-- > Here the Animation Window is in Dope Sheet mode, showing the keyframe positions all the animated properties within the Animation Clip -->
> 这里的动画视图是关键帧清单模式，显示了动画剪辑中所有动画属性的关键帧位置。

<!-- ## Curves Timeline Mode -->
## 曲线模式

<!-- Curves mode offers a view of how the values for each animated property changes over time in a resizable graph. All selected properties appear overlaid within the same graph view. This mode allows you to have great control over viewing and editing the values, and how they are interpolated between. -->
曲线模式以曲线图的方式显示每个动画属性的值是如何随时间变化的，曲线图可以调整。所有选中的属性叠加显示在同一张图中。这种模式为查看和编辑属性值、补间值，提供了强大的控制。

![Here the Animation Window is showing the curves for the rotation data of four selected GameObjects within this animation clip](https://docs.unity3d.com/uploads/Main/AnimationEditorCurvesViewMultipleSelected.png)
<!-- > Here the Animation Window is showing the curves for the rotation data of four selected GameObjects within this animation clip -->
> 这里的动画视图显示了动画剪辑中 4 个选中对象的旋转曲线。

<!-- When using curves mode to view your animation it’s important to understand that sometimes the various ranges for each property may differ greatly. For example, consider a simple animation clip for a spinning bouncing cube. The bouncing Y position value may vary between the range 0 to 2 (meaning the cube bounces 2 units high during the animation), however the rotation value will go from 0 to 360. When viewing these two curves at the same time, the position animation curves will be very difficult to make out because the view will be zoomed out to fit the 0–360 range within the window: -->
当使用曲线模式查看动画剪辑时，非常重要的一点是，每个属性值的范围有时会相差很大。举个例子，假如有一个同时旋转和弹跳的立方体。弹跳的 Y 坐标值可能介于 0 和 2 之间（也就是说，立方体在动画过程中弹跳 2 个单位），但是，旋转值介于 0 和 360 之间。同时查看这两条曲线时，位置动画曲线将非常难以辨别，因为整个视图被放大以显示 0 到 360。

![The position and rotation curves of a bouncing spinning cube are both selected, but because the view is zoomed out to fit the 0-360 range of the rotation curve, the bouncing Y position curve is not discernible](https://docs.unity3d.com/uploads/Main/AnimationEditorTwoCurvesBigRangeDifference.png)
<!-- > The position and rotation curves of a bouncing spinning cube are both selected, but because the view is zoomed out to fit the 0–360 range of the rotation curve, the bouncing Y position curve is not discernible -->
> 同时选择立方体的位置动画和旋转动画，因为视图被放大以显示旋转曲线的 0 到 360，位置曲线的 Y 轴值不可辨识。

<!-- You can click on individual properties in the list to automatically re-scale the curves view to fit the range for that value, or you can manually adjust the zoom of the curves window by using the special drag handles at each end of the view’s scrollbar sliders. -->
你可以点击列表中的单个动画属性，曲线视图会自动缩放，以匹配值范围；或者，你也可以通过拖动右侧和下方的滚动条，来手动缩放曲线视图。

![Here the Animation Window is zoomed in to view the bouncing Y position animation. The start of the yellow rotation curve is still visible, but now extends way off the top of the view.](https://docs.unity3d.com/uploads/Main/AnimationEditorTwoCurvesZoomedIn.png)
<!-- > Here the Animation Window is zoomed in to view the bouncing Y position animation. The start of the yellow rotation curve is still visible, but now extends way off the top of the view. -->
> 动画视图被放大，以显示位置动画的 Y 轴值。黄色的旋转动画曲线仍然可见，但只显示了一部分。

<!-- ## Creating a New Animation Clip -->
## 创建动画剪辑

<!-- To animate Game Objects in Unity, the object or objects need an Animator Component attached. This Animator Component must reference an Animator Controller, which in turn contains references to one or more Animation Clips. -->
在 Unity 中，为了让游戏对象动起来，需要附加一个动画组件。这个动画组件必须引用一个动画控制器，动画控制器再引用一个或多个动画剪辑。

<!-- When using the Animation View to begin animating a GameObject in Unity, these items will be automatically created, attached and set-up for you. -->
在 Unity 中，当开始使用动画视图让游戏对象动起来时，这些元素将被自动创建和绑定。

<!-- To create a new **Animation Clip** for the selected **Game Object**, click the selection box at the upper right of the **Animation View** and select **[Create New Clip]**. You will then be prompted to save an Animation Clip somewhere in your **Assets** folder. If the Game Object already has an Animator Component attached, with an Animator Controller assigned, the new clip will be added as a state in the existing Animator Controller. -->
点击 **动画视图** 左上角的下拉框，选择 **Create New Clip**，可以为选中的 **游戏对象** 创建一个新的 **动画剪辑**。然后，会提示你把动画剪辑保存到 Assets 文件夹的某个位置。如果这个游戏对象已经附加了动画组件，并且指定了动画控制器，新的动画剪辑将作为一个状态，被添加到现有的动画控制器中。

![Create a new Animation Clip](https://docs.unity3d.com/uploads/Main/AnimationEditorNewClip.png)
<!-- > Create a new Animation Clip -->
> 创建一个新的动画剪辑

<!-- If the Game Object doesn’t have an **Animator Component** already at this stage, a number of things happen automatically: -->
如果这个游戏对象尚未绑定动画组件，那么将自动进行下面的操作：

<!-- 
* A new Animator Controller asset will be will be created
* The new clip being created will be added into the Animator Controller as the default state
* An Animator Component will be added to the GameObject being animated
* The Animator Component will have the new Animator Controller assigned to it
 -->
* 一个新的动画控制器资源文件将被创建
* 新创建的动画剪辑将作为默认状态，被添加到该动画控制器
* 一个动画组件将被添加到该游戏对象
* 该动画组件将引用该动画控制器

<!-- The result of this automatic sequence is that you can begin the animation process of a new object by clicking the record button or selecting [Create New Clip], and all the required elements of the animation system are set up for you. -->
这样做的好处是，你只需要点击记录按钮或选择 Create New Clip，就可以开始构建动画，动画系统所需的所有元素已经被自动配置好。

<!-- The diagram below shows how these pieces are assigned, starting from the new animation clip created in the Animation Window: -->
下面的图演示了，在动画视图中，创建新的动画剪辑时，这些元素是如何分配的：

![A new clip is created, and saved as an asset. The clip is automatically added as the default state to a new Animator Controller which is also saved as an asset. The Animator Controller is assigned to an Animator Component which is added to the GameObject.](https://docs.unity3d.com/uploads/Main/AnimationNewClipAutoSetup.png)
<!-- > A new clip is created, and saved as an asset. The clip is automatically added as the default state to a new Animator Controller which is also saved as an asset. The Animator Controller is assigned to an Animator Component which is added to the GameObject. -->
> 一个新的动画剪辑被创建，并保存为一个资源。该动画剪辑作为默认状态，被自动添加到一个新的动画控制器中，该动画控制器也被保存为一个资源。该动画控制器被分配给游戏对象上的动画组件。

<!-- In the image below, you can see a game object selected that is not animated. We have just a simple cube, with no Animator component. The Animation, Hierarchy, Project and Inspector windows are arranged side-by-side for clarity. -->
在下面的图中，你可以看到一个没有动画的游戏对象。它只是一个简单的立方体，没有附加动画组件。动画视图、检视视图、层级视图和项目视图挨个排列如下。

![Before: An un-animated gameobject (Cube) is selected. It does not yet have an Animator Component, and no Animator Controller exists.](https://docs.unity3d.com/uploads/Main/AnimationEditorNewAnimationBefore.png)
<!-- > Before: An un-animated gameobject (“Cube”) is selected. It does not yet have an Animator Component, and no Animator Controller exists. -->
> 之前：一个无动画的游戏对象（立方体）被选中。它没有动画组件，动画控制器也不存在。

<!-- By pressing the record button in the Animation view (left), or choosing “[Create New Clip]” from the selection box in the Animation view, a new animation clip is created. Unity will ask to pick the name & location to save this new Animation Clip. Unity also creates an Animator Controller asset with the same name as the selected GameObject, adds an Animator component to the GameObject, and connects the assets up appropriately. -->
通过按下（左侧）动画视图中的记录按钮，或选择动画视图中下拉框的 Create New Clip，就创建了一个新的动画剪辑。Unity 将会询问你该动画剪辑的名字和存储位置。Unity 还会创建一个与选中的游戏对象同名的动画控制器资源文件，并且添加一个动画组件到游戏对象上，并且合适地连接这些资源。

![After: After creating a new clip, you can see the new assets created in the project window, and the Animator Component assigned in the Inspector window (far right). You can also see the new clip assigned as the default state in the Animator Window](https://docs.unity3d.com/uploads/Main/AnimationEditorNewAnimationAdded.png)
<!-- > After: After creating a new clip, you can see the new assets created in the project window, and the Animator Component assigned in the Inspector window (far right). You can also see the new clip assigned as the default state in the Animator Window -->
> 之后：创建一个新的动画剪辑后，你可以在项目视图中看到新的资源文件，在检视视图（右侧）中看到附加的动画组件。你还可以在动画控制器视图中看到该动画剪辑被当作了默认状态。

<!-- ## Animating a Game Object -->
## 让游戏对象动起来

<!-- Once you have saved the new animation clip asset, you are ready to begin adding keyframes to the clip. To begin editing an Animation Clip for the selected Game Object, click on the Animation Record button. This will enter Animation Record Mode, where changes to the Game Object are recorded into the Animation Clip. -->
一旦你保存了新动画剪辑，就可以开始为动画剪辑添加关键帧了。开始为选中的游戏对象编辑动画剪辑之前，需要先点击动画记录按钮，进入动画记录模式，此时，对该游戏对象的修改会被记录到动画剪辑。

![Record button](https://docs.unity3d.com/uploads/Main/AnimationEditorAnimationModeButton.png)
<!-- > Record button -->
> 记录按钮

<!-- You can stop the Animation Record Mode at any time by clicking the Animation Mode button again. This will revert the Game Object to the state it was in prior to entering the Animation Mode. -->
任何时候，你都可以通过再次点击动画模式按钮，从而退出动画记录模式。这一操作将把该游戏对象的状态恢复到进入动画记录模式之前。

<!-- The changes you make to the GameObject will be recorded as keyframes at the current time shown by the red line in the Animation Window. -->
你对该游戏对象所做的修改将被记录为关键帧，红线所指示的时间即为关键帧的时间。

<!-- You can animate any property of the object by manipulating the object while in Animation Record Mode. Moving, Rotating or Scaling the object will add corresponding keyframes for those properties in the animation clip. Adjusting values directly in the object’s inspector will also add keyframes while in Record mode. This applies to any property in the inspector, including numeric values, checkboxes, colours, and most other values. -->
在动画记录模式中，通过修改游戏对象，你可以为任何属性添加动画。无论是移动、旋转或缩放游戏对象，对应的属性都将被添加到动画剪辑的相应关键帧中。在游戏对象的检视视图中修改值，也会添加关键帧。支持检视视图中的任意属性，例如，数值型、复选框、颜色等大部分属性。

<!-- Any animated properties of the GameObject are shown listed in the property list on the left-hand side of the Animation Window. Properties which are not animated are not shown in this window. Any new properties that you animate, including properties on child objects, are added to the property list area as soon as you start animating them. -->
游戏对象的动画属性被罗列在动画视图左侧的属性列表中。不参与动画的属性不会显示在视图中。新增加的动画属性，包括子对象上的属性，同样会被添加到属性列表中。

<!-- Transform properties are special in that the .x, .y, and .z properties are linked, so that curves are added three at a time. -->
Tranform 组件的属性有些特别，属性 .x、.y 和 .z 是连接在一起的，所以一次会添加 3 条曲线。

<!-- You can also browse all animatable properties on the current GameObject (and its children) by clicking the Add Curve button. -->
通过点击 Add Curves 按钮，你也可以浏览当前游戏对象（和它的子对象）上所有支持动画的属性。

<!-- Any property can be animated by selecting it from the “Add Curves” button popup menu. -->
通过 Add Curves 按钮，你可以选择任意属性，为它添加动画。

![Add curves](https://docs.unity3d.com/540/Documentation/uploads/Main/AnimationEditorAddCurves.png)
<!-- > Add curves -->
> 添加曲线

<!-- When in **Animation Mode**, a red vertical line will show which frame of the **Animation Clip** is currently previewed. The **Inspector** and **Scene View** will show the Game Object at that frame of the Animation Clip. The values of the animated properties at that frame are also shown in a column to the right of the property names. -->
在 **动画录制模式** 中，红色的垂直线表示当前预览的是动画剪辑的哪一桢。检视视图和场景视图将显示游戏对象在该桢的状态。动画属性在该桢的值显示在属性名称的右侧。

<!-- In Animation Mode a red vertical line shows the currently previewed frame. -->
在动画录制模式中，红色的垂直线表示当前预览的桢。

![Current frame](https://docs.unity3d.com/uploads/Main/AnimationEditorPreviewFrame.png)
<!-- > Current frame -->
> 当前桢

<!-- ### Time Line -->
### 时间轴

<!-- You can click anywhere on the Time Line to preview or modify that frame in the Animation Clip. The numbers in the Time Line are shown as seconds and frames, so 1:30 means 1 second and 30 frames. -->
在动画剪辑中，你可以点击 **时间轴** 上的任意一点，来预览或修改该桢。时间轴上的数字是秒数和帧数，所以 1:30 的意思是 1 秒加 30 桢。

![Time Line](https://docs.unity3d.com/uploads/Main/AnimationEditorTimeLine.png)
<!-- > Time Line -->
> 时间轴

<!-- ### Frame Navigation -->
### 桢导航

<!-- You can also use the following keyboard shortcuts to navigate between frames: -->
你可以使用下面的键盘快捷键在桢之间导航：

<!-- 
* Press Comma (,) to go to the previous frame.
* Press Period (.) to go to the next frame.
* Hold Alt and press Comma (,) to go to the previous keyframe.
* Hold Alt and press Period (.) to go to the next keyframe.
 -->
* 按下逗号（,）切换到前一桢。
* 按下句号（.）切换到下一桢。
* 同时按下 Alt 和逗号（,）切换到前一个关键帧。
* 同时按下 Alt 和句号（.）切换到下一个关键帧。

![Frame navigation](https://docs.unity3d.com/uploads/Main/AnimationEditorFrameNavigation.png)
<!-- > Frame navigation -->
> 桢导航

<!-- ### Animation Mode -->
### 动画模式

<!-- In Animation Mode you can move, rotate, or scale the Game Object in the Scene View. This will automatically create Animation Curves for the position, rotation, and scale properties of the Animation Clip if they didn’t already exist, and keys on those Animation Curves will automatically be created at the currently previewed frame to store the respective Transform values you changed. -->
在动画模式下，你可以在场景视图中移动、旋转或缩放游戏对象。如果位置、旋转或缩放属性在动画剪辑中不存在的话，这些操作将自动创建动画曲线；并且，自动在当前预览的桢上创建关键帧，以存储改变后的 Transform 值。

<!-- You can also use the Inspector to modify any of the animatable properties of the Game Object. This too will create Animation Curves as needed, and create keys on those Animation Curves at the currently previewed frame to store your changed values. -->
你也可以在检视视图中修改游戏对象的任意动画属性。如果需要的话，这些操作也会自动创建动画曲线，并且在当前预览的动画曲线上创建关键帧，以存储改变后的 Transform 值。

<!-- ### Keyframe Creation -->
### 创建关键帧

<!-- You can manually create a **keyframe** using the **Add Keyframe button**. This will create a key for all the properties that are currently selected in the **Animation View**. This is useful for selectively adding keys to specific properties only. -->
你可以使用 **添加关键桢按钮** 手动创建一个 **关键帧**。这个操作将会为 **动画视图** 中当前选中的所有属性创建一个关键帧。也就是说，你可以有选择性地只为特定属性添加关键帧。

![The Add Keyframe Button](https://docs.unity3d.com/uploads/Main/AnimationEditorKeyframeButton.png)
<!-- > The Add Keyframe Button -->
> 添加关键桢按钮

<!-- ### Playback -->
### 播放

<!-- The **Animation Clip** can be played back at anytime by clicking the **Play button** in the **Animation View**. -->
任意时候，在 **动画视图** 中点击 **播放按钮**，都可以播放&重放 **动画剪辑**。

![The Play button](https://docs.unity3d.com/540/Documentation/uploads/Main/AnimationEditorPlayButton.png)
> The Play button
> 播放按钮

<!-- ### Locking The Window -->
### 锁定动画视图

<!-- You can lock the animation editor window so that it will not automatically switch to reflect the currently selected Game Object in the hierarchy or scene. Locking the window is useful if you want to focus on the animation for one particular object, while being able to select and manipulate other objects in the scene. -->
你可以锁定动画视图，这样，当你在层级视图或场景视图中切换选中的游戏对象时，动画视图不会自动切换。如果只关注某个特定的游戏对象，那么锁定动画视图会非常有用，此时你可以选择或编辑场景视图中的其他对象。

![The Lock button](https://docs.unity3d.com/uploads/Main/AnimationEditorWindowLockIcon.png)
<!-- > The Lock button -->
> 锁定按钮

<!-- ## More Information -->
## 更多资料

<!-- To learn more about navigating the **Curve View**, see the section on Using Animation Curves. -->
想要学习控制 **曲线模式** 的更多内容，请查阅 [使用动画曲线](https://docs.unity3d.com/Manual/animeditor-AnimationCurves.html) 一节。
