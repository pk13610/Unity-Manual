<!-- # Cameras -->
# 摄像机

<!-- A Unity scene is created by arranging and moving objects in a three-dimensional space. Since the viewer’s screen is two-dimensional, there needs to be a way to capture a view and “flatten” it for display. This is accomplished using **Cameras**. -->

通过在三维空间中布置和移动游戏对象来创建 Unity 场景。而观察者的屏幕是二维的，因此需要通过某种方式来来捕获视图，并使之平面化，才能显示在屏幕上。这个过程通过 **摄像机 Camera** 完成。

<!-- A camera is an object that defines a view in scene space. The object’s position defines the viewpoint, while the forward (Z) and upward (Y) axes of the object define the view direction and the top of the screen, respectively. The [Camera component] also defines the size and shape of the region that falls within the view. With these parameters set up, the camera can display what it currently “sees” to the screen. As the camera object moves and rotates, the displayed view will also move and rotate accordingly. -->

摄像机是一个游戏对象，定义了场景空间的观察视图。它的位置定义了观察点，它的向前轴（Z）和向上轴（Y）分别定义了观察方向和屏幕的垂直方向。[摄像机组件 Camera] 还定义了视椎体（落入观察视图的区域）的大小和形状。设置这些参数后，摄像机就可以把它当前『看到』的内容显示到屏幕上。当摄像机对象移动和旋转时，显示的视图也将相应地移动和旋转。

[Camera component]: https://docs.unity3d.com/Manual/class-Camera.html
[摄像机组件 Camera]: https://docs.unity3d.com/Manual/class-Camera.html

<!-- ## Perspective and orthographic cameras -->
## 透视相机和正交相机

![The same scene shown in perspective mode (left) and orthographic mode (right)](https://docs.unity3d.com/uploads/Main/CameraPerspectiveAndOrtho.jpg)
<!-- > The same scene shown in perspective mode (left) and orthographic mode (right) -->
> 同一场景的透视模式（左）和正交模式（右）。

<!-- A camera in the real world, or indeed a human eye, sees the world in a way that makes objects look smaller the farther they are from the point of view. This well-known perspective effect is widely used in art and computer graphics and is important for creating a realistic scene. Naturally, Unity supports perspective cameras, but for some purposes, you want to render the view without this effect. For example, you might want to create a map or information display that is not supposed to appear exactly like a real-world object. A camera that does not diminish the size of objects with distance is referred to as _orthographic_ and Unity cameras also have an option for this. The perspective and orthographic modes of viewing a scene are known as camera _projections_. (scene above from [BITGEM]) -->

真实世界中的摄像机或人眼，观察世界的方式是，离观察点越远，物体看起来越小。这种众所周知的透视效果被广泛应用于艺术和计算机图形，并且对于创建一个真实的场景至关重要。Unity 支持透视摄像机，不过出于某些目的，你可能希望渲染的视图不具有这种效果。例如，创建地图或信息显示时，它们看起来不应该像真实世界中的物体那样。不随距离缩小物体的大小的摄像机称为 _正交摄像机_，Unity 摄像机为此提供了一个选项。以透视模式和正交模式观察场景被称为摄像机 _投影_。（上面的场景来自 [BITGEM]）。

[BITGEM]: https://www.assetstore.unity3d.com/en/#!/publisher/1299

<!-- ## The shape of the viewed region -->
## 视椎体的形状

<!-- Both perspective and orthographic cameras have a limit on how far they can “see” from their current position. The limit is defined by a plane that is perpendicular to the camera’s forward (Z) direction. This is known as the far clipping plane since objects at a greater distance from the camera are “clipped” (ie, excluded from rendering). There is also a corresponding near clipping plane close to the camera - the viewable range of distance is that between the two planes. -->

透视摄像机和正交摄像机都对从当前位置能『看』多远有限制。该限制由一个垂直于摄像机向前轴的平面定义。该平面被称为远剪裁平面，因为大于这个距离的物体将被『剪裁』掉（即从渲染中剔除）。相应地，在摄像机附近还有一个近剪裁平面 —— 这两个平面之间的距离就是可见的距离范围。

<!-- Without perspective, objects appear the same size regardless of their distance. This means that the viewing volume of an orthographic camera is defined by a rectangular box extending between the two clipping planes. -->

如果没有透视效果，不管距离多远，物体的大小看起来都一样。这意味着，正交摄像机的视椎体是一个限制在两个剪裁平面之间的长方体。

<!-- When perspective is used, objects appear to diminish in size as the distance from camera increases. This means that the width and height of the viewable part of the scene grows with increasing distance. The viewing volume of a perspective camera, then, is not a box but a pyramidal shape with the apex at the camera’s position and the base at the far clipping plane. The shape is not exactly a pyramid, however, because the top is cut off by the near clipping plane; this kind of truncated pyramid shape is known as a frustum. Since its height is not constant, the frustum is defined by the ratio of its width to its height (known as the aspect ratio) and the angle between the top and bottom at the apex (known as the _field of view of FOV_). See the page about [understanding the view frustum] for a more detailed explanation. -->

使用透视效果时，随着与摄像机的距离增加，物体的大小看起来被减小了。这意味着，屏幕可视区域的宽度和高度睡着距离的增加而增加。投射摄像机的视椎体不是一个长方体，而是一个金字塔形状，顶点位于摄像机位置，底部位于远剪裁平面。由于它的高度不是恒定的，截头椎体由其宽度和高度的比率（称为 _纵横比、高宽比_）和定点处上剪裁平面和下剪裁平面的夹角（称为 _视场 FOV_）来定义。相关详细说明请参阅 [了解截头视椎体]。

[understanding the view frustum]: https://docs.unity3d.com/Manual/UnderstandingFrustum.html
[了解截头视椎体]: https://docs.unity3d.com/Manual/UnderstandingFrustum.html

<!-- ## The background to the camera view -->
## 摄像机视图的背景

<!-- For indoor scenes, the camera may always be completely inside some object representing the interior of a building, cave or other structure. When the action takes place outdoors, however, there will be many empty areas in between objects that are filled with nothing at all; these background areas typically represent the sky, space or the murky depths of an underwater scene. -->

对于室内场景，例如建筑物、洞穴或其他结构，摄像机可以一直显示它们的内部结构。然后在室外场景时，物体之间将会有许多没有任何填充的空区域；这些背景区域通常代表了天空、太空或黑暗的水下场景。

<!-- A camera can’t leave the background completely undecided and so it must fill in the empty space with something. The simplest option is to clear the background to a flat color before rendering the scene on top of it. You can set this color using the camera’s _Background_ property, either from the inspector or from a script. A more sophisticated approach that works well with outdoor scenes is to use a [Skybox]. As its name suggests, a skybox behaves like a “box” lined with images of a sky. The camera is effectively placed at the center of this box and can see the sky from all directions. The camera sees a different area of sky as it rotates but it never moves from the center (so the camera cannot get “closer” to the sky). The skybox is rendered behind all objects in the scene and so it represents a view at infinite distance. The most common usage is to represent the sky in a standard outdoor scene but the box actually surrounds the camera completely, even underneath. This means that you can use a skybox to represent parts of the scene (eg, rolling plains that stretch beyond the horizon) or the all-round view of a scene in space or underwater. -->

摄像机不能没有背景，它必须用某些东西来填充空区域。最简单的方式是，在渲染场景之前把背景设置为单一的颜色。通过摄像机的 _背景 Background_ 属性可以设置颜色，可以在检视视图中设置，也可以在脚本中设置。一个更复杂的方式是，为室外场景使用 [天空盒 Skybox]。正如其名字所暗示的，天空盒的行为像是一个内衬了天空图像的盒子。摄像机被放置在盒子的中心，可以从任何角度看到天空。随着摄像机的旋转，它可以看到不同的天空区域，但是一直位于盒子的中心（因此摄像机无法靠近天空）。天空盒被渲染在场景中所有物体的背后，所以它代表了无限距离处的视图。天空盒最常见的用法是表示室外场景的天空，而实际上，盒子完全包围住了摄像机，包括摄像机的下方。这意味着可以用天空盒来表示部分场景（例如，延伸到地平线之外的平原），或是太空中或水下的全景视图。

[Skybox]: https://docs.unity3d.com/Manual/class-Skybox.html
[天空盒 Skybox]: https://docs.unity3d.com/Manual/class-Skybox.html

<!-- You can add a skybox to a scene simply by setting the _Skybox_ property in the [Lighting window] (menu: **Window > Lighting**). See [this page] for further details on how to create your own skybox. -->

通过设置 [光照窗口]（菜单：**Window > Lighting**）的 _天空盒 Skybox_ 属性，可以很容易地为场景添加天空盒。有关如何创建自定义天空盒的更多详细信息，请参阅 [这个页面]。

[Lighting window]: https://docs.unity3d.com/Manual/GlobalIllumination.html
[this page]: https://docs.unity3d.com/Manual/HOWTO-UseSkybox.html
[光照窗口]: https://docs.unity3d.com/Manual/GlobalIllumination.html
[这个页面]: https://docs.unity3d.com/Manual/HOWTO-UseSkybox.html