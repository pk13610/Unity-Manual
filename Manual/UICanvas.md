<!-- # Canvas -->
# 画布 Canvas

<!-- The **Canvas** is the area that all UI elements should be inside. The Canvas is a Game Object with a Canvas component on it, and all UI elements must be children of such a Canvas. -->

**画布 Canvas** 是一块包含了所有 UI 元素的区域。画布 Canvas 是一个带有 Canvas 组件的游戏对象，所有的 UI 元素都必须是 Canvas 对象的子对象。

<!-- Creating a new UI element, such as an Image using the menu **GameObject > UI > Image**, automatically creates a Canvas, if there isn’t already a Canvas in the scene. The UI element is created as a child to this Canvas. -->

新建一个 UI 元素，例如通过菜单 **GameObject > UI > Image** 创建一个图像，如果场景中不存在 Canvas 对象，将自动创建一个。UI 元素作为 Canvas 的子对象被创建。

<!-- The Canvas area is shown as a rectangle in the Scene View. This makes it easy to position UI elements without needing to have the Game View visible at all times. -->

Canvas 区域在场景视图中显示为一个矩形。这样可以很容易地定位 UI 元素，而不需要（不依赖）一直显示游戏视图。

<!-- **Canvas** uses the EventSystem object to help the Messaging System. -->

**画布 Canvas** 使用 EventSystem 对象来通知 Messaging System。

<!-- ## Draw order of elements -->
## 元素绘制顺序

<!-- UI elements in the Canvas are drawn in the same order they appear in the Hierarchy. The first child is drawn first, the second child next, and so on. If two UI elements overlap, the later one will appear on top of the earlier one. -->

画布 Canvas 中的 UI 元素的绘制顺序与它们在层级视图中显示的顺序相同。首先绘制第一个子对象，然后是第二个子对象，以此类推。如果两个 UI 元素发生重叠，后一个将显示在前一个之上。

<!-- To change which element appear on top of other elements, simply reorder the elements in the Hierarchy by dragging them. The order can also be controlled from scripting by using these methods on the Transform component: SetAsFirstSibling, SetAsLastSibling, and SetSiblingIndex. -->

要使某个元素显示在其他元素之上，只需要在层级视图中通过拖动重新排序元素。也可以在脚本中通过 Transform 组件上的这些方法来控制顺序：`SetAsFirstSibling`、`SetAsLastSibling` 和 `SetSiblingIndex`。

<!-- ## Render Modes -->
## 渲染模式

<!-- The Canvas has a **Render Mode** setting which can be used to make it render in screen space or world space. -->

画布 Canvas 具有一个 **渲染模式 Render Mode** 设置，可以用于控制是在场景空间还是世界空间中渲染。

<!-- ### Screen Space - Overlay -->
### 场景空间 - 叠加

<!-- This render mode places UI elements on the screen rendered on top of the scene. If the screen is resized or changes resolution, the Canvas will automatically change size to match this. -->

该渲染模式放置 UI 元素到屏幕上，位于场景的顶部。如果屏幕调整大小或改变分辨率，画布 Canvas 将自动改变大小，以匹配屏幕。

![UI in screen space overlay canvas](https://docs.unity3d.com/uploads/Main/GUI_Canvas_Screenspace_Overlay.png)
<!-- > UI in screen space overlay canvas -->
> UI，场景空间与画布叠加

<!-- ### Screen Space - Camera -->
### 场景空间 - 摄像机

<!-- This is similar to **Screen Space - Overlay**, but in this render mode the Canvas is placed a given distance in front of a specified **Camera**. The UI elements are rendered by this camera, which means that the Camera settings affect the appearance of the UI. If the Camera is set to **Perspective**, the UI elements will be rendered with perspective, and the amount of perspective distortion can be controlled by the Camera **Field of View**. If the screen is resized, changes resolution, or the camera frustum changes, the Canvas will automatically change size to match as well. -->

该渲染模式类似于 **场景空间 - 叠加**，但是该模式的画布 Canvas 被放置在特定 **摄像机 Camera** 前方给定距离的位置上，这意味着摄像机 Camera 的设置会影响 UI 的外观。如果摄像机 Camera 被设置为 **透视 Perspective**，UI 元素将以透视方式渲染，透视变形程度可以用摄像机 Camera 的 **视野 Field of View** 控制。如果屏幕调整大小、改变分辨率或者摄像机 Camera 视锥发生变化，画布 Canvas 也将自动改变大小，以匹配屏幕。

![UI in screen space camera canvas](https://docs.unity3d.com/uploads/Main/GUI_Canvas_Screenspace_Camera.png)
<!-- > UI in screen space camera canvas -->
> UI，场景空间 - 摄像机 - 画布

<!-- ### World Space -->
### 世界空间

<!-- In this render mode, the Canvas will behave as any other object in the scene. The size of the Canvas can be set manually using its Rect Transform, and UI elements will render in front of or behind other objects in the scene based on 3D placement. This is useful for UIs that are meant to be a part of the world. This is also known as a “diegetic interface”. -->

在该渲染模式下，画布 Canvas 的行为与场景中的任意其他对象一样。通过矩形变换组件 Rect Transform 可以手动调整画布 Canvas 的大小，UI 元素将基于 3D 位置被渲染在场景中其他对象的后面。这意味着，UI 成为了世界的一部分。这种模式也被成为『剧情界面』。

![UI in world space canvas](https://docs.unity3d.com/uploads/Main/GUI_Canvas_Worldspace.png)
<!-- > UI in world space canvas -->
> UI，世界空间 - 画布
