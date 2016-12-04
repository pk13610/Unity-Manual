<!-- Unity Manual > Animation > Animator Controllers > The Animator Window -->

<!-- # The Animator Window -->
# 动画控制器视图

<!-- The Animator Window allows you to create, view and modify Animator Controller assets. -->

动画控制器视图允许你创建、查看和修改动画控制器资源。

![The Animator Window showing a new empty Animator Controller asset](https://docs.unity3d.com/uploads/Main/AnimatorWindowNewEmpty.png)
<!-- > The Animator Window showing a new empty Animator Controller asset -->
> 动画控制器视图显示了一个新的空动画控制器资源

<!-- The Animator window has two main sections: the main gridded layout area, and the left-hand Layers & Parameters pane. -->

动画控制器视图主要有两部分：网格布局主体区域，左侧的分层和参数面板。

![The layout area of the Animator window](https://docs.unity3d.com/uploads/Main/AnimatorWindowLayoutArea.png)
<!-- > The layout area of the Animator window -->
> 动画控制器视图的布局区域

<!-- The main section with the dark grey grid is the layout area. You can use this area to create, arrange and connect states in your [Animator Controller](https://docs.unity3d.com/Manual/Animator.html). -->

深灰色网格部分是主体布局区域。你可以在这里创建、排列和连接 [动画控制器](https://docs.unity3d.com/Manual/Animator.html) 的状态（即动画剪辑）。

<!-- You can right-click on the grid to create a new state nodes. Use the middle mouse button or Alt/Option drag to pan the view around. Click to select state nodes to edit them, and click & drag state nodes to rearrange the layout of your state machine. -->

可以在网格上右键点击创建一个新的状态节点。使用鼠标中键拖动，或拖动时按住 Alt/Option 键，可以移动视图。可以单击状态节点编辑它们，可以点击并拖动状态节点来重新排版状态机的布局。

![The Parameters view, with two example parameters created.](https://docs.unity3d.com/uploads/Main/AnimatorWindowParametersPane.png)
<!-- > The Parameters view, with two example parameters created. -->
> 参数视图，创建了两个示例参数。


<!-- The left-hand pane can be switched betwen Parameters view and Layers view. The parameters view allows you to create, view and edit the [Animator Controller Parameters](https://docs.unity3d.com/Manual/AnimationParameters.html). These are variables you define that act as inputs into the state machine. To add a parameter, click the Plus icon and select the parameter type from the pop up menu. To delete a parameter, select the parameter in the lists and press the delete key. -->

左侧的面板可以在参数视图和分层视图之间切换。参数视图允许你创建、查看和编辑 [动画控制器参数]。这里定义的变量用作状态机的输入。想要添加一个参数，请点击加号图标，然后从弹出的菜单中选择参数类型。想要删除一个删除，请在列表中选中参数，然后按下删除键。

[动画控制器参数]: https://docs.unity3d.com/Manual/AnimationParameters.html

![The Layers view](https://docs.unity3d.com/uploads/Main/AnimatorWindowLayersPane.png)
<!-- > The Layers view -->
> 分层视图

<!-- When the left-hand pane is switched to Layers view, you can create, view and edit [layers](https://docs.unity3d.com/Manual/AnimationLayers.html) within your Animator Controller. This allows you to have multiple layers of animation within a single animation controller working at the same time, each controlled by a separate state machine. A common use of this is to have a separate layer playing upper-body animations over a base layer that controls the general movement animations for a character. -->

当左侧面板被切换为分层视图时，你可以创建、查看和编辑动画控制器的[分层]。允许在一个动画控制器中同时运行多个动画分层，每个分层由一个独立的状态机控制。一个常见的用例是，用一个基础分层控制角色的移动动画，在这之上，用一个独立分层控制上身动画。

[分层]: https://docs.unity3d.com/Manual/AnimationLayers.html

<!-- To add a layer, click the plus icon. To delete a layer, select the layer and press the delete key. -->

想要增加一个分层，请点击加号图标。想要删除一个分层，请选中它，然后按下删除键。

![The Layers & Parameters hide icon](https://docs.unity3d.com/uploads/Main/AnimatorWindowEyeIcon.png)
<!-- > The Layers & Parameters hide icon -->
> 分层和参数的隐藏图标

<!-- Clicking the “eye” icon on or off will show or hide the Parameters & Layers side-pane, allowing you more room to see and edit your state machine. -->

点击眼睛图标，将显示或隐藏参数和分层边栏，这样可以有更多的空间来查看和编辑状态机。

![The hierarchical breadcrumb location](https://docs.unity3d.com/uploads/Main/AnimatorWindowBreadcrumbLocation.png)
<!-- > The hierarchical breadcrumb location -->
> 层级面包屑定位

<!-- The “breadcrumb” hierarchical location within the current state machine. States can contain [sub-states](https://docs.unity3d.com/Manual/NestedStateMachines.html) and [trees](https://docs.unity3d.com/Manual/class-BlendTree.html) and these structures can be nested repeatedly. When drilling down into sub states, the hierarchy of parent states and the current state being viewed is listed here. Clicking on the parent states allows you to jump back up to parent states or go straight back to the base layer of the state machine. -->

层级面包屑定位。状态可以包含 [子状态] 和 [混合树]，并且，这些结构可以重复嵌套。当向下钻入（进入）子状态时，这里会列出父级状态和当前（子级状态）。点击父级状态可以跳回父级状态，后者直接返回状态机的根状态。

[子状态]: https://docs.unity3d.com/Manual/NestedStateMachines.html
[混合树]: https://docs.unity3d.com/Manual/class-BlendTree.html


![The lock icon](https://docs.unity3d.com/uploads/Main/AnimatorWindowLockIcon.png)
<!-- > The lock icon -->
> 锁定图标

<!-- Enabling the lock icon will keep the Animator Window focused on the current state machine. When the lock icon is off, clicking a new animator asset or a Game Object with an animator component will switch the Animator Window to show that item’s state machine. Locking the window allows you to keep the Animator window showing the same state machine, regardless of which other assets or Game Objects are selected. -->

启动锁定图表将使动画控制器视图聚焦于当前状态机。当锁定图标关闭时，点击一个新的动画控制器资源或带有动画组件的游戏对象时，动画控制器视图将现实该元素的状态机。锁定视图，使动画控制器视图总是显示同一个状态机，无论你选择了其他哪个资源或游戏对象。
