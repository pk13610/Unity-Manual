<!-- # Interaction Components -->
# 交互组件

<!-- This section covers components in the UI system that handles interaction, such as mouse or touch events and interaction using a keyboard or controller. -->

本节介绍 UI 系统中处理交互的组件，例如鼠标或触摸事件，以及使用键盘或控制器进行的交互。

<!-- The interaction components are not visible on their own, and must be combined with one or more [visual elements] in order to work correctly. -->

交互组件本身不可见，必须与一个或多个 [视觉组件] 组合，才能正确工作。

[visual elements]: https://docs.unity3d.com/Manual/UIVisualComponents.html
[视觉组件]: https://docs.unity3d.com/Manual/UIVisualComponents.html

<!-- ## Common Functionality -->
## 常用功能

<!-- Most of the interaction components have some things in common. They are selectables, which means they have shared built-in functionality for visualising transitions between states (normal, highlighted, pressed, disabled), and for navigation to other selectables using keyboard or controller. This shared functionality is described on the [Selectable] page. -->

大多数交互组件有一些共同点。它们是可选择的，这意味它们内置支持可视化的状态转换（正常、高亮、按下、禁用），以及使用键盘或控制器导航导其他可选项。这一内置功能的描述请参阅 [Selectable] 页。

[Selectable]: https://docs.unity3d.com/Manual/script-Selectable.html

<!-- ## Button -->
## 按钮 Button

<!-- A Button has an **OnClick** UnityEvent to define what it will do when clicked. -->

按钮具有 **OnClick** 事件，用于定义点击后执行的行为。

![](https://docs.unity3d.com/uploads/Main/UI_ButtonExample.png)

<!-- See the [Button] page for details on using the Button component. -->

有关 Button 组件的详细用法，请参阅 [Button] 页面。

[Button]: https://docs.unity3d.com/Manual/script-Button.html

<!-- ## Toggle -->
## 开关 Toggle

<!-- A Toggle has an **Is On** checkbox that determines whether the Toggle is currently on or off. This value is flipped when the user clicks the Toggle, and a visual checkmark can be turned on or off accordingly. It also has an **OnValueCHanged** UnityEvent to define what it will do when the value is changed. -->

开关 Toggle 含有一个复选框，用于确定 Toggle 当前是打开还是关闭的。当用户点击 Toggle，它的值被反转，并且相应的打开或关闭视觉标记。它还具有一个 **OnValueCHanged** 事件，用于定义值被改变时执行的行为。

![](https://docs.unity3d.com/uploads/Main/UI_ToggleExample.png)

<!-- See the [Toggle] page for details on using the Toggle component. -->

有关 Toggle 组件的详细用法，请参阅 [Toggle] 页面。

[Toggle]: https://docs.unity3d.com/Manual/script-Toggle.html

<!-- ## Toggle Group -->
## 开关组 Toggle Group


<!-- A Toggle Group can be used to group a set of [Toggles] that are mutually exclusive. Toggles that belong to the same group are constrained so that only one of them can be selected at a time - selecting one of them automatically deselects all the others. -->

开关组可用于对彼此互斥的一组 [开关 Toggles] 进行分组。同属一个组（属于同一组）的开关被约束为一次只能选中其中一个 —— 选中其中一个自动取消所有其他开关。

[Toggles]: https://docs.unity3d.com/Manual/script-Toggle.html
[开关 Toggles]: https://docs.unity3d.com/Manual/script-Toggle.html

![](https://docs.unity3d.com/uploads/Main/UI_ToggleGroupExample.png)

<!-- See the [Toggle Group] page for details on using the Toggle Group component. -->

有关 Toggle Group 组件的详细用法，请参阅 [Toggle Group] 页面。

[Toggle Group]: https://docs.unity3d.com/Manual/script-ToggleGroup.html

<!-- ## Slider -->
## 滑块 Slider

<!-- A Slider has a decimal number **Value** that the user can drag between a minimum and maximum value. It can be either horizontal or vertical. It also has a **OnValueChanged** UnityEvent to define what it will do when the value is changed. -->

滑块 Slider 具有一个小数 **Value**，用户可以在最小值和最大值之间拖动。它可以是水平或垂直的。它还有一个 **OnValueChanged** 事件，用于定义值被改变时执行的行为。

![](https://docs.unity3d.com/uploads/Main/UI_SliderExample.png)

<!-- See the [Slider] page for details on using the Slider component. -->

有关 Slider 组件的详细用法，请参阅 [Slider] 页。

[Slider]: https://docs.unity3d.com/Manual/script-Slider.html

<!-- ## Scrollbar -->
## 滚动条 Scrollbar

<!-- A Scrollbar has a decimal number **Value** between 0 and 1. When the user drags the scrollbar, the value changes accordingly. -->

滚动条 Scrollbar 具有一个小数 **Value**，介于 0 和 1 之间。当用户拖动滚动条时，值会相应地改变。

<!-- Scrollbars are often used together with a [Scroll Rect] and a [Mask] to create a scroll view. The Scrollbar has a **Size** value between 0 and 1 that determines how big the handle is as a fraction of the entire scrollbar length. This is often controlled from another component to indicate how big a proportion of the content in a scroll view is visible. The Scroll Rect component can automatically do this. -->

滚动条 Scrollbars 通常与 [滚动矩形 Scroll Rect] 和 [遮罩 Mask] 一起使用，来创建滚动视图。Scrollbar 具有一个 **Size** 值，介于 0 和 1 之间，决定了手柄相对于整个滚动条长度的大小。该值通常由其他组件控制，用于指定滚动视图中内容的可见比例。滚动矩形组件 Scroll Rect 可以自动执行该操作。

[Scroll Rect]: https://docs.unity3d.com/Manual/script-ScrollRect.html
[Mask]: https://docs.unity3d.com/Manual/script-Mask.html
[滚动矩形 Scroll Rect]: https://docs.unity3d.com/Manual/script-ScrollRect.html
[遮罩 Mask]: https://docs.unity3d.com/Manual/script-Mask.html

<!-- The Scrollbar can be either horizontal or vertical. It also has a **OnValueChanged** UnityEvent to define what it will do when the value is changed. -->

滚动条 Scrollbar 可以是水平或垂直的。它还有一个 **OnValueChanged** 事件，用于定义值被改变时执行的行为。

![](https://docs.unity3d.com/uploads/Main/UI_ScrollbarExample.png)

<!-- See the [Scrollbar] page for details on using the Scrollbar component. -->

有关 Scrollbar 组件的详细用法，请参阅滚 [Scrollbar] 页。

[Scrollbar]: https://docs.unity3d.com/Manual/script-Scrollbar.html

<!-- ## Dropdown -->
## 下拉列表 Dropdown

<!-- A Dropdown has a list of options to choose from. A text string and optionally an image can be specified for each option, and can be set either in the Inspector or dynamically from code. It has a **OnValueChanged** UnityEvent to define what it will do when the currently chosen option is changed. -->

下拉列表 Dropdown 包含一个可供选择的选项列表。可以为每个选项指定一段文本字符串和一张可选的图像，并且可以在检视视图中设置，或者通过代码动态设置。它有一个 **OnValueChanged** 事件，用于定义当前选中的选项被改变时执行的行为。

![](https://docs.unity3d.com/uploads/Main/UI_DropdownExample.png)

<!-- See the [Dropdown] page for details on using the Dropdown component. -->

有关 Dropdown 组件的详细用法，请参阅 [Dropdown] 页。

[Dropdown]: https://docs.unity3d.com/Manual/script-Dropdown.html

<!-- ## Input Field -->
## 输入域 Input Field

<!-- An Input Field is used to make the text of a [Text Element] editable by the user. It has a UnityEvent to define what it will do when the text content is changed, and an another to define what it will do when the user has finished editing it. -->

输入域 Input Field 使用户可以编辑 [文本元素 Text Element] 的文本内容。它有一个 **OnValueChange** 事件，用于定义文本内容被改变时执行的行为，还有一个 **EndEdit** 事件，用于定义用户完成编辑后执行的行为。

[Text Element]: https://docs.unity3d.com/Manual/script-Text.html
[文本元素 Text Element]: https://docs.unity3d.com/Manual/script-Text.html

![](https://docs.unity3d.com/uploads/Main/UI_InputFieldExample.png)

<!-- See the [Input Field] page for details on using the Input Field component. -->

有关 Input Field 组件的详细用法，请参阅 [Input Field] 页。

[Input Field]: https://docs.unity3d.com/Manual/script-InputField.html

<!-- ## Scroll Rect (Scroll View) -->
## 滚动矩形（滚动视图） Scroll Rect

<!-- A Scroll Rect can be used when content that takes up a lot of space needs to be displayed in a small area. The Scroll Rect provides functionality to scroll over this content. -->

当占据大量空间的内容需要显示在很小区域中时，可以使用滚动矩形 Scroll Rect。滚动矩形为内容提供了滚动功能。

<!-- Usually a Scroll Rect is combined with a [Mask] in order to create a scroll view, where only the scrollable content inside the Scroll Rect is visible. It can also additionally be combined with one or two [Scrollbars] that can be dragged to scroll horizontally or vertically. -->

通常，滚动矩形与 [遮罩 Mask] 一起使用，来创建滚动视图，只有位于滚动矩形内的滚动内容可见。它也可以结合一个或两个 [滚动条 Scrollbars]，通过从拖动滚动条来水平或垂直滚动内容。

[Mask]: https://docs.unity3d.com/Manual/script-Mask.html
[Scrollbars]: https://docs.unity3d.com/Manual/script-Scrollbar.html
[遮罩 Mask]: https://docs.unity3d.com/Manual/script-Mask.html
[滚动条 Scrollbars]: https://docs.unity3d.com/Manual/script-Scrollbar.html

![](https://docs.unity3d.com/uploads/Main/UI_ScrollRectExample.png)

<!-- See the [Scroll Rect] page for details on using the Scroll Rect component. -->

有关 Scroll Rect 的详细用法，请参阅 [Scroll Rect] 页。

[Scroll Rect]: https://docs.unity3d.com/Manual/script-ScrollRect.html
