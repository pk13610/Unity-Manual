<!-- # Basic Layout -->
# 基本布局

<!-- In this section we’ll look at how you can position UI elements relative to the Canvas and each other. If you want to test yourself while reading, you can create an Image using the menu **GameObject -> UI -> Image**. -->

在本节中，我们将看看如何定位 UI 元素，相对于画布 Canvas 或其他元素。如果你想边阅读边测试，可以使用菜单 **GameObject -> UI -> Image** 创建一个 Image。

<!-- ## The Rect Tool -->
## 矩形工具 Rect Tool

<!-- Every UI element is represented as a rectangle for layout purposes. This rectangle can be manipulated in the Scene View using the **Rect Tool** in the toolbar. The Rect Tool is used both for Unity’s 2D features and for UI, and in fact can be used even for 3D objects as well. -->

为了方便布局，每个 UI 元素都用一个矩形表示。在场景视图下，可以使用菜单栏中的 **矩形工具 Rect Tool** 操作矩形。矩形工具可以用于 Unity 的 2D 功能和 UI，事实上甚至还可以用于 3D 对象。

![Toolbar buttons with Rect Tool selected](https://docs.unity3d.com/uploads/Main/GUI_Rect_Tool_Button.png)
<!-- > Toolbar buttons with Rect Tool selected -->
> 工具栏按钮，选中了矩形工具

<!-- The Rect Tool can be used to move, resize and rotate UI elements. Once you have selected a UI element, you can move it by clicking anywhere inside the rectangle and dragging. You can resize it by clicking on the edges or corners and dragging. The element can be rotated by hovering the cursor slightly away from the corners until the mouse cursor looks like a rotation symbol. You can then click and drag in either direction to rotate. -->

矩形工具可以用于移动、调整大小和旋转 UI 元素。一旦选中了某个 UI 元素，你可以通过单击矩形内部的任意位置并拖动来移动矩形。你可以通过单击边缘或边角并拖动来调整矩形大小。你可以把鼠标光标移动到稍微远离边角的位置，直到光标变成一个旋转符号，然后单击并向任意方向拖动，来旋转矩形。

<!-- Just like the other tools, the Rect Tool uses the current pivot mode and space, set in the toolbar. When working with UI it’s usually a good idea to keep those set to **Pivot** and **Local**. -->

就像其他工具一样，矩形工具基于工具栏上设置的当前轴心和空间。当使用 UI 时，通常最好将它们设置为 **Pivot** 和 **Local**。

![Toolbar buttons set to Pivot and Local](https://docs.unity3d.com/uploads/Main/GUI_Pivot_Local_Buttons.png)
<!-- > Toolbar buttons set to Pivot and Local -->
> 工具栏按钮，设置为 Pivot 和 Local

<!-- ## Rect Transform -->
## 矩形变换 Rect Transform

<!-- The **Rect Transform** is a new transform component that is used for all UI elements instead of the regular **Transform** component. -->

**矩形变换 Rect Transform** 是一个新变换组件，用于所有 UI 元素，而不是常规的 **变换 Transform** 组件。

![](https://docs.unity3d.com/uploads/Main/UI_RectTransform.png)

<!-- Rect Transforms have position, rotation, and scale just like regular Transforms, but it also has a width and height, used to specify the dimensions of the rectangle. -->

Rect Transform 具有位置、旋转和缩放属性，类似于常规的 Transform，但是前者还具有宽度和高度，用于指定矩形的尺寸。

<!-- ### Resizing Versus Scaling -->
### 调整大小 vs 缩放

<!-- When the Rect Tool is used to change the size of an object, normally for Sprites in the 2D system and for 3D objects it will change the local _scale_ of the object. However, when it’s used on an object with a Rect Transform on it, it will instead change the width and the height, keeping the local scale unchanged. This resizing will not affect font sizes, border on sliced images, and so on. -->

当使用矩形工具改变对象的大小时，对于 2D 系统中的精灵 Sprite 和 3D 对象，将改变本地缩放比例 _scale_。但是，对于具有矩形变换 Rect Transform 的对象，将改变宽度和高度，保持本地缩放比例不变。并且，调整大小不会影响字体大小、切片图像的边框，等等。

<!-- ### Pivot -->
### 轴心 Pivot

<!-- Rotations, size, and scale modifications occur around the pivot so the position of the pivot affects the outcome of a rotation, resizing, or scaling. When the toolbar Pivot button is set to Pivot mode, the pivot of a Rect Transform can be moved in the Scene View. -->

旋转、大小和缩放的变化围绕轴心进行，所以轴心的位置会影响旋转、调整大小或缩放的结果。当工具栏上的『轴心』按钮设置为 Pivot 模式时，可以在场景视图中移动矩形变换的轴心。

![](https://docs.unity3d.com/uploads/Main/UI_PivotRotate.png)

<!-- ### Anchors -->
### 锚点 Anchors

<!-- Rect Transforms include a layout concept called **anchors**. Anchors are shown as four small triangular handles in the Scene View and anchor information is also shown in the Inspector. -->

矩形变换包含一个称为 **锚点 Anchors** 的布局概念。在场景视图中，锚点显示为 4 个小三角形手柄，锚点信息则显示在检视视图中。

<!-- If the parent of a Rect Transform is also a Rect Transform, the child Rect Transform can be anchored to the parent Rect Transform in various ways. For example, the child can be anchored to the center of the parent, or to one of the corners. -->

如果某个矩形变换的父元素也是一个矩形变换，那么子矩形变换可以通过各种方式锚定到父矩形变换。例如，子矩形变换可以锚定到父矩形变换的中心或某个边角。

![UI element anchored to the center of the parent. The element maintains a fixed offset to the center.](https://docs.unity3d.com/uploads/Main/UI_Anchored1.gif)
<!-- > UI element anchored to the center of the parent. The element maintains a fixed offset to the center. -->
>  UI 元素锚定到父元素的中心。元素与中心保持固定的偏移。

![UI element anchored to the lower right corner of the parent. The element maintains a fixed offset to the lower right corner.](https://docs.unity3d.com/uploads/Main/UI_Anchored2.gif)
<!-- > UI element anchored to the lower right corner of the parent. The element maintains a fixed offset to the lower right corner. -->
> UI 元素锚定到父元素的右下角。元素与右下角保持固定的偏移。

<!-- The anchoring also allows the child to stretch together with the width or height of the parent. Each corner of the rectangle has a fixed offset to its corresponding anchor, i.e. the top left corner of the rectangle has a fixed offset to the top left anchor, etc. This way the different corners of the rectangle can be anchored to different points in the parent rectangle. -->

锚定还允许子元素随着父元素的宽度或高度一起伸展。矩形的每个边角与相应的锚点具有固定的偏移，例如，矩形的左上角与左上锚点具有固定的偏移，以此类推。这样，矩形的不同边角可以锚定到父矩形的不同点。

![UI element with left corners anchored to lower left corner of the parent and right corners anchored to lower right. The corners of the element maintains fixed offsets to their respective anchors.](https://docs.unity3d.com/uploads/Main/UI_Anchored3.gif)
<!-- > UI element with left corners anchored to lower left corner of the parent and right corners anchored to lower right. The corners of the element maintains fixed offsets to their respective anchors. -->
> UI 元素的左侧边角锚定到父矩形的左下角，右侧边角锚定到父矩形的右下角。该元素的边角与各自的锚点保持固定的偏移。

<!-- The positions of the anchors are defined in fractions (or percentages) of the parent rectangle width and height. 0.0 (0%) corresponds to the left or bottom side, 0.5 (50%) to the middle, and 1.0 (100%) to the right or top side. But anchors are not limited to the sides and middle; they can be anchored to any point within the parent rectangle. -->

锚点的位置用父矩形宽度和高度的分数（或百分比）来定义。0.0（0%）对应左侧或底部，0.5（50%）对应中间，1.0（100%）对应右侧或顶部。但是锚点不限于边框和中间，子矩形可以锚定于父矩形内的任意点。

![UI element with left corners anchored to a point a certain percentage from the left side of the parent and right corners anchored to a point a certain percentage from the right side of the parent rectangle.](https://docs.unity3d.com/uploads/Main/UI_Anchored4.gif)
<!-- > UI element with left corners anchored to a point a certain percentage from the left side of the parent and right corners anchored to a point a certain percentage from the right side of the parent rectangle. -->
> UI 元素的左侧边角锚定于距父元素左侧特定比例的点，右侧边角锚定于距父矩形右侧特定比例的点。

<!-- You can drag each of the anchors individually, or if they are together, you can drag them together by clicking in the middle in between them and dragging. If you hold down **Shift** key while dragging an anchor, the corresponding corner of the rectangle will move together with the anchor. -->

你可以单独地拖动每个锚点，也可以一次拖动多个。如果在拖动锚点时按下 **Shift** 键，对应的矩形边角将与锚点一起移动。

> 这段文档的前半句没看懂。

<!-- A useful feature of the anchor handles is that they automatically snap to the anchors of sibling rectangles to allow for precise positioning. -->

锚点手柄的一个很有用的功能是，它们自动对齐到兄弟矩形的锚点，从而可以精确定位。

<!-- ### Anchor presets -->
### 预设锚点

<!-- In the Inspector, the Anchor Preset button can be found in the upper left corner of the Rect Transform component. Clicking the button brings up the Anchor Presets dropdown. From here you can quickly select from some of the most common anchoring options. You can anchor the UI element to the sides or middle of the parent, or stretch together with the parent size. The horizontal and vertical anchoring is independent. -->

在检视视图中，在矩形变换组件 Rect Transform 的左上角可以找到预设锚点按钮 Anchor Preset。点击该按钮将显示预设锚点下拉菜单。在这里，你可以快速选择一些最常见的锚点选项。你可以将 UI 元素锚定到父元素的边和中间，或者随父元素的大小伸展。水平和垂直锚定是独立的。

![](https://docs.unity3d.com/uploads/Main/UI_AnchorPreset.png)

<!-- The Anchor Presets buttons displays the currently selected preset option if there is one. If the anchors on either the horizontal or vertical axis are set to different positions than any of the presets, the custom options is shown. -->

预设锚点按钮显示了当前选择的预设选项，如果有选的话。如果在水平轴或垂直轴上选择了与预设不同的位置，则会显示自定义选项。

<!-- ### Anchor and position fields in the Inspector -->
### 检视视图中的锚点和位置属性

<!-- You can click the Anchors expansion arrow to reveal the anchor number fields if they are not already visible. **Anchor Min** corresponds to the lower left anchor handle in the Scene View, and **Anchor Max** corresponds to the upper right handle. -->

点击锚点 Anchors 的展开箭头，可以显示锚点的数值域（如果它们不可见的话）。**Anchor Min** 对应场景视图中左上角的锚点手柄，**Anchor Max** 对于右上角的手柄。

<!-- The position fields of rectangle are shown differently depending on whether the anchors are together (which produces a fixed width and height) or separated (which causes the rectangle to stretch together with the parent rectangle). -->

矩形位置属性的显示方式取决于锚点是聚集在一起（产生固定的宽度和高度）还是分离的（导致矩形随着父矩形伸展）。

<!-- When all the anchor handles are together the fields displayed are Pos X, Pos Y, Width and Height. The Pos X and Pos Y values indicate the position of the pivot relative to the anchors. -->

当所有锚点手柄聚集在一起时，数值域显示为 `Pos X`、`Pos Y`、`Width` 和 `Height`。`Pos X` 和 `Pos Y` 的值指示了轴心相对于锚点的位置。

<!-- When the anchors are separated the fields can change partially or completely to Left, Right, Top and Bottom. These fields define the padding inside the rectangle defined by the anchors. The Left and Right fields are used if the anchors are separated horizontally and the Top and Bottom fields are used if they are separated vertically. -->

当锚点是分离的，数值域的部分或全部显示为 `Left`、`Right`、`Top` 和 `Bottom`。这些数值域定义了锚点矩形的内边距。如果锚点在水平方向上是分离的，则使用 `Left` 和 `Right` 域，如果在垂直方向上是分离的，则使用 `Top` 和 `Bottom` 域。

<!-- Note that changing the values in the anchor or pivot fields will normally counter-adjust the positioning values in order to make the rectangle stay in place. If cases where this is not desired, the **Raw Mode** can be enabled using a small button in the Inspector. This causes the anchor and pivot value to be able to be changed without any other values changing as a result. This will likely cause the rectangle to be visually moved or resized, since its position and size is dependent on the anchor and pivot values. -->

请注意，更改锚点域或轴心域的值通常会反过来调整位置域的值，以使矩形保持原位。如果不希望出现这种情况，可以在检视视图中开启 **原始模式 Raw Mode**，它是一个小按钮。在这种模式下，改变锚点和轴心的值不会改变任何其他值。这也可能导致矩形在视觉上移动或改变大小，因为矩形的位置和大小取决于锚点和轴心的值。
