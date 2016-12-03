<!-- Unity Manual > Animation > Animation Clips > Animation Window Guide > Editing Curves -->

<!-- # Editing Curves -->
# 编辑动画曲线

<!-- There are several different features and windows in the Unity Editor which use **Curves** to display and edit data. The methods you can use to view and manipulate curves is largely the same across all these areas, although there are some exceptions. -->
Unity 编辑器提供了几种不同的功能和窗口，用 **曲线** 来显示和编辑数据。这些用来查看和编辑的方法大体上相同，但是也有一些区别。

<!-- * The [Animation View](https://docs.unity3d.com/Manual/AnimationEditorGuide.html) uses curves to display and edit the values of animated properties over time in an **Animation Clip**. -->

* [动画视图](https://docs.unity3d.com/Manual/AnimationEditorGuide.html) 使用曲线来显示和编辑 **动画剪辑** 中动画属性随时间变化的值。

![The Animation View.](https://docs.unity3d.com/uploads/Main/AnimationEditorCurve.png)
<!-- > The Animation View. -->
> 动画视图

<!-- * Script components can have member variables of type [AnimationCurve](https://docs.unity3d.com/Manual/EditingValueProperties.html) that can be used for all kinds of things. Clicking on those in the Inspector will open up the **Curve Editor**. -->

* 脚步组件可以含有 [动画曲线](https://docs.unity3d.com/Manual/EditingValueProperties.html) 类型的成员变量，可以用于各种对象。在检视视图中点击这些变量将弹出 **曲线编辑器**。

![The Curve Editor.](https://docs.unity3d.com/uploads/Main/CurveEditorPopup.png)
<!-- > The Curve Editor. -->
> 曲线编辑器。

<!-- * The [Audio Source](https://docs.unity3d.com/Manual/class-AudioSource.html) component uses curves to control roll-off and other properties as a function of distance to the Audio Source. -->
* [声源](https://docs.unity3d.com/Manual/class-AudioSource.html) 组件使用曲线来控制声源的衰减量（随着距离变化）和其他属性。

![Distance function curves in the AudioSource component in the Inspector.](https://docs.unity3d.com/uploads/Main/AudioSourceCurve.png)
<!-- > Distance function curves in the AudioSource component in the Inspector. -->
> 在检视视图中，声源组件的距离函数曲线。

<!-- While these controls have subtle differences, the curves can be edited in exactly the same way in all of them. This page explains how to navigate and edit curves in those controls. -->
随着这些控制方法有些微小差异，但是，所有曲线的编辑方式完全相同。本页将介绍如何在这些控制方法中导航和编辑曲线。

<!-- ## Adding and Moving Keys on a Curve -->
## 在曲线上添加和移动关键点

<!-- A key can be added to a curve by double-clicking on the curve at the point where the **key** should be placed. It is also possible to add a **key** by right-clicking on a curve and select **Add Key** from the context menu. -->
在想要放置关键点的位置双击曲线，可以在该点添加一个关键点。也可以右键点击曲线，并从上下文菜单中选择 **添加关键点**，来添加一个 **关键点**。

<!-- Once placed, **keys** can be dragged around with the mouse: -->
添加的 **关键点** 可以用鼠标拖动：

<!-- 
* Click on a **key** to select it. Drag the selected **key** with the mouse.
* To snap the **key** to the grid while dragging it around, hold down **Command** on Mac / **Control** on Windows while dragging.
 -->
* 点击 **关键点** 来选中它。用鼠标拖动选中的 **关键点**。
* 拖动时，在 Mac 上按下 **Command** 键或在 Windows 上按下 **Control** 键，可以让 **关键点** 对齐到网格。

<!-- It is also possible to select multiple **keys** at once: -->
也可以一次选中多个 **关键点**：

<!-- 
* To select multiple **keys** at once, hold down **Shift** while clicking the keys.
* To deselect a selected **key**, click on it again while holding down **Shift**.
* To select all **keys** within a rectangular area, click on an empty spot and drag to form the rectangle selection.
* The rectangle selection can also be added to existing selected keys by holding down **Shift**.
 -->
* 想要选择多个 **关键点**，请在点击关键点时按住 **Shift** 键。
* 想要取消选择的 **关键点**，请在点击关键点时按住 **Shift** 键。
* 想要选择矩形区域内的所有 **关键点**，请点击空白处并拖动鼠标形成一个矩形选择区域。
* 也可以在矩形选择时按住 **Shift** 键，把矩形区域内的关键点添加到已选中的关键点中。

<!-- **Keys** can be deleted by selecting them and pressing **Delete**, or by right-clicking on them and selecting **Delete Key** from the context menu. -->
选中并按下 **Delete** 键，，或者右键点击并从上下文菜单中选择 **Delete Key**，可以删除 **关键点**。

<!-- ## Editing Keys -->
## 编辑关键点

<!-- Direct editing of key values in curve editors is a new feature in Unity 5.1. Use **Enter/Return** or context menu to start editing selected keys, **Tab** to switch between fields, **Enter/Return** to commit, and **Escape** to cancel editing. -->
在曲线编辑器中直接编辑关键点的值，是 Unity 5.1 新增的一个功能。使用 **Enter/Return** 键或上下文菜单来开始编辑选中的关键点，使用 **Tab** 键在输入域之间切换，使用 **Enter/Return** 键来提交修改，使用 **Escape** 来取消修改。

<!-- ## Navigating the Curve View -->
## 浏览曲线视图

<!-- When working with the **Animation View** you can easily zoom in on details of the curves you want to work with or zoom out to get the full picture. -->
使用 **动画视图** 时，可以很容易地放大要处理的曲线细节，或缩小曲线以获得完整的图像。

<!-- You can always press **F** to frame-select the shown curves or selected keys in their entirely. -->
你可以随时按下 **F** 键，完整地查看曲线，或者放大显示选中的关键点。

> 译注：没有选中关键点时，曲线被自动缩放至合适的尺寸，以完整显示整个曲线；选中关键点时，将放大曲线，视图中只显示选中的关键点。

<!-- ### Zooming -->
### 缩放

<!-- You can **zoom** the Curve View using the scroll-wheel of your mouse, the zoom functionality of your trackpad, or by holding **Alt** while right-dragging with your mouse. -->
使用鼠标滚轮或触控板的缩放功能，或者鼠标右键拖动时按住 **Alt** 键，可以缩放曲线视图。

<!-- You can zoom on only the horizontal or vertical axis: -->
你可以只在水平或垂直方向上缩放曲线视图。

<!-- 
* **zoom** while holding down **Command** on Mac / **Control** on Windows to zoom horizontally.
* **zoom** while holding down **Shift** to zoom vertically.
Furthermore, you can drag the end caps of the scrollbars to shrink or expand the area shown in the Curve View.
 -->
* 在 Mac 中按住 **Command** 键，或者在 Windows 中按住 **Control** 键，只进行水平缩放。
* 按住 **Shift** 键，只进行垂直缩放。

<!-- Furthermore, you can drag the end caps of the scrollbars to shrink or expand the area shown in the Curve View. -->
此外，你可以在曲线视图中拖动滚动条的两端来缩小或放大可见区域。

<!-- ### Panning -->
### 移动

<!-- You can **pan** the Curve View by middle-dragging with your mouse or by holding **Alt** while left-dragging with your mouse. -->
按住鼠标滚轮并拖动，或鼠标左键拖动时按住 **Alt** 键，可以移动曲线视图。

<!-- ### Editing Tangents -->
### 编辑切线


<!-- A key has two **tangents** - one on the left for the incoming slope and one on the right for the outgoing slope. The tangents control the shape of the curve between the keys. You can select from a number of different tangent types to control how your curve leaves one key and arrives at the next key. Right-click a key to select the tangent type for that key. -->
一个关键点拥有两条 **切线** —— 左侧的逼近斜率和右侧的远离斜率。切线控制了关键点之间的曲线形状。你可以从多个不同的切线类型中选择，来控制曲线如何离开一个关键点和到达下一个关键点。右键单击某个关键点来选择该关键点的切线类型。

![](https://docs.unity3d.com/uploads/Main/AnimationCurveTangentMenu.png)

<!-- For animated values to change smoothly when passing a key, the left and right tangent must be co-linear. The following tangent types ensure smoothness: -->
要使动画值在经过关键点时平滑变化，左侧切线和右侧切线必须是共线的（在同一条直线上）。下面的切线类型可以保证平滑度：

<!-- * **Clamped Auto:** This is the default tangent mode. The tangents are automatically set to make the curve pass smoothly through the key. When editing the key’s position or time, the tangent adjusts to prevent the curve from “overshooting” the target value. If you manually adjust the tangents of a key in Clamped Auto mode, it is switched to **Free Smooth** mode. In the example below, the tangent automatically goes into a slope and levels out while the key is being moved: -->

* **自动钳位（Clamped Auto）：** 默认切线类型。自动设置切线，使曲线平滑地经过该关键点。当编辑该关键点的位置或时间时，自动调整切线，以避免曲线被过度调整。在自动钳位模式下，如果你手动调整了该关键点的切线，切线类型会被切换为 **自由平滑（Free Smooth）** 模式。在下面的例子中，当移动关键点时，切线的逼近斜率和远离斜率被自动调整：

![](https://docs.unity3d.com/uploads/Main/AnimationClampedAutoTangents.gif)

<!-- * **Auto:** This is a [Legacy tangent mode](https://docs.unity3d.com/Manual/UpgradeGuide550), and remains an option to be backward compatible with older projects. Unless you have a specific reason to use this mode, use the default **Clamped Auto**. When a key is set to this mode, the tangents are automatically set to make the curve pass smoothly through the key. However, there are two differences compared with **Clamped Auto** mode: -->

* **自动（Auto）：** 这是一个[遗留切线模式](https://docs.unity3d.com/Manual/UpgradeGuide550)，保留该模式是为了向后兼容旧项目。除非你有特殊原因必须使用该模式，否则请使用默认的 **钳位自动（Clamped Auto）**。当关键点被设置为该模式时，切线被自动设置，使曲线平滑地经过该关键点。但是，相比 **钳位自动（Clamped Auto）** 模式，有两点差异：

    <!-- 1. The tangents do not adjust automatically when the key’s position or time is edited; they only adjust when initially setting the key to this mode. -->
    <!-- 2. When Unity calculates the tangent, it does not take into account avoiding “overshoot” of the target value of the key. -->

    1. 当编辑该关键点的位置或时间时，切线不会自动调整；切线仅仅在该关键点被第一次设置为 **自动（Auto）** 模式（初始化）时才会进行调整。
    2. Unity 在计算切线时，不会考虑避免过度调整（即可能会导致过度调整）。

![](https://docs.unity3d.com/uploads/Main/AnimationAuto.png)

<!-- * **Free Smooth:** Drag the tangent handles to freely set the tangents. They are locked to be co-linear to ensure smoothness. -->

* **自由平滑（Free Smooth）：**拖动切线图柄来自由地设置切线。切线被锁定为共线，以确保平滑度。

![](https://docs.unity3d.com/uploads/Main/AnimationFreeSmooth.png)

<!-- * **Flat:** The tangents are set to be horizontal (this is a special case of Free Smooth). -->

* **水平（Flat）：**切线被设置为水平（自由平滑的一种特殊情况）。

![](https://docs.unity3d.com/uploads/Main/AnimationFlat.png)

<!-- Sometimes you might not want the curve to be smooth when passing through a key. To create sharp changes in the curve, choose one of the **Broken** tangent modes. -->

有时你可能不希望曲线平滑地通过某个关键点。想要在曲线中创建剧烈的变化，请选择 **折线** 切线模式。

![](https://docs.unity3d.com/uploads/Main/AnimationCurveTangentTypes.png)

<!-- When using broken tangents, the left and right tangent can be set individually. Each of the left and right tangents can be set to one of the following types: -->

使用折线切线时，可以单独设置左右切线。左右切线可以设置为以下类型之一：

<!-- * **Broken - Free:** Drag the tangent handle to freely set the tangents. -->

* **折线 - 自由（Broken - Free）：** 拖动切线图柄来自由地设置切线。

![](https://docs.unity3d.com/uploads/Main/AnimationBrokenFree.png)

<!-- * **Broken - Linear:** The tangent points towards the neighboring key. To make a linear curve segment, set the tangents at both ends to be **Linear**. In the example below, all three keys have been set to **Broken - Linear**, to achieve straight lines from key to key. -->

* **折线 - 直线（Broken - Linear）：** 切线指向相邻的关键点。要创建直线型的曲线片段，请将切换的两边都设置为 **直线 Linear**。在下面的例子总，3 个关键点都被设置为 **折线 - 直线，Broken - Linear**，以实现关键点到关键点的直线。

![](https://docs.unity3d.com/uploads/Main/AnimationBrokenLinear.png)

<!-- * **Broken - Constant:** The curve retains a constant value between two keys. The value of the left key determines the value of the curve segment. -->

* **折线 - 常量（Broken - Constant）:** 曲线在两个关键点之间保持为一个常量值。左侧关键点的值决定了曲线片段的值。

![](https://docs.unity3d.com/uploads/Main/AnimationBrokenConstant.png)
