<!-- # Shadows -->
# 阴影

<!-- Unity’s lights can cast **Shadows** from an object onto other parts of itself or onto other nearby objects. Shadows add a degree of depth and realism to a scene since they bring out the scale and position of objects that can otherwise look “flat”. -->

Unity 的灯光可以将 **阴影** 从一个游戏对象投射到自身的其他部分或是附近的其他游戏对象上。阴影以『扁平』的方式体现游戏对象的尺寸和位置，因此可以为场景添加一定程度的深度和真实感。

![Scene with objects casting shadows](https://docs.unity3d.com/uploads/Main/ShadowIntro.png)
<!-- > Scene with objects casting shadows -->
> 场景视图中的游戏对象正在投射阴影

<!-- ## How Do Shadows Work? -->
## 阴影如何工作？

<!-- Consider the simplest case of a scene with a single light source. Light rays travel in straight lines from that source and may eventually hit objects in the scene. Once a ray has hit an object, it can’t travel any further to illuminate anything else (ie, it “bounces” off the first object and doesn’t pass through). The shadows cast by the object are simply the areas that are not illuminated because the light couldn’t reach them. -->

考虑一种最简单的情况，在场景中只有单个光源。光线从光源出发并沿着直线传播，最终可能会碰撞到场景中的游戏对象。一旦光线碰撞到某个游戏对象，光线将无法继续传播和照亮前方的任何其他游戏对象（例如，光线无法通过第一个游戏对象，并从该游戏对象上反弹离开）。游戏对象投射的阴影不过是一些不被照亮的区域，因为光线无法到达这些区域。

![](https://docs.unity3d.com/uploads/Main/ShadowMapIntro.svg)

<!-- Another way to look at this is to imagine a camera at the same position as the light. The areas of the scene that are in shadow are precisely those areas that the camera can’t see. -->

观察阴影的另一个方式是，想象在光源位置处有一个摄像机。场景中的阴影区域恰好是摄像机无法看到的区域。

![A lights eye view of the same scene](https://docs.unity3d.com/uploads/Main/ShadowLightsEyeView.svg)
> A “light’s eye view” of the same scene
> 同一场景中，光源位置的眼睛所看到的视图

<!-- In fact, this is exactly how Unity determines the positions of shadows from a light. The light uses the same principle as a camera to “render” the scene internally from its point of view. A depth buffer system, as used by scene cameras, keeps track of the surfaces that are closest to the light; surfaces in a direct line of sight receive illumination but all the others are in shadow. The depth map in this case is known as a **Shadow Map** (you may find the Wikipedia Page on shadow mapping useful for further information). -->

事实上，这正是 Unity 确定阴影位置的方式。光源使用与摄像机相同的原理，来『渲染』光源视角范围内的场景。光源像摄像机一样使用一个深度缓存系统，持续跟踪面向光源的表面；只有位于视线中的表面接受光照，其他所有表面则都在阴影中。这里的深度映射称为 **阴影映射**（你可以在阴影映射的 [维基百科页] 中找到更多信息）。

[Wikipedia Page]: http://en.wikipedia.org/wiki/Shadow_mapping
[维基百科页]: http://en.wikipedia.org/wiki/Shadow_mapping

<!-- ## Enabling Shadows -->
## 开启阴影

<!-- Use the **Shadow Type** property in the Inspector to enable and define shadows for an individual light. -->

使用检视视图中的 **Shadow Type** 属性来开启和定义来自单个光源的阴影。

![](https://docs.unity3d.com/uploads/Main/ShadowTypeInspector.svg)

<!-- > Property:   Function: -->
<!-- ### 属性和功能 -->

<!-- **Shadow Type** The **Hard Shadows** setting produces shadows with a sharp edge. Hard shadows are not particularly realistic compared to **Soft Shadows** but they involve less processing, and are acceptable for many purposes. Soft shadows also tend to reduce the “blocky” aliasing effect from the shadow map. -->

#### **Shadow Type** 阴影类型

选项 **Hard Shadows** 产生具有尖锐边缘的阴影。与 **Soft Shadows** 相比，它不是特别逼真，但是只涉及较少的计算，并且对于大多数场合是可接受的。Soft Shadows 则可以减少阴影纹理的『块状』混叠效应。

<!-- **Strength**    This determines how dark the shadows are. In general, some light is scattered by the atmosphere and reflected off other GameObjects, so you usually don’t want shadows to be set to maximum strength. -->

#### **Strength** 阴影强度

决定阴影的暗度。一般来说，某些光线会被大气层散射，和被其他游戏对象反射，所以通常不希望阴影被设置为最大暗度。

<!-- **Resolution**  This sets the rendering resolution for the shadow map’s “Camera” mentioned above. If your shadows have very visible edges, then you might want to increase this value. -->

#### **Resolution** 阴影分辨率

设置阴影纹理在『摄像机』上的的渲染分辨率。如果阴影具有非常明显的边缘，那么可能需要增大该值。

<!-- **Bias**    Use this to fine-tune the position and definition of your shadow. See [Shadow mapping and the Bias property], below, for more information. -->

#### **Bias** 阴影偏差

微调阴影的位置和定义。相关详细信息，请参阅下面的 [阴影映射和偏差属性 Bias]。

[Shadow mapping and the Bias property]: https://docs.unity3d.com/Manual/ShadowOverview.html#LightBias
[阴影映射和偏差属性 Bias]: https://docs.unity3d.com/Manual/ShadowOverview.html#LightBias

<!-- **Normal Bias** Use this to fine-tune the position and definition of your shadow. See [Shadow mapping and the Bias property], below, for more information. -->

#### **Normal Bias** 阴影法线偏差

微调阴影的位置和定义。相关详细信息，请参阅下面的 [阴影映射和偏差属性 Bias]。

<!-- **Shadow Near Plane**   This allows you to choose the value for the near plane when rendering shadows. GameObjects closer than this distance to the light do not cast any shadows. -->

#### **Shadow Near Plane** 阴影近剪裁平面

允许在渲染阴影时选择近剪裁平面的 Near 值。如果游戏对象到光源的距离小于该值，这不会投射任何阴影。

<!-- Each [Mesh Renderer] in the Scene also has a **Cast Shadows** and a **Receive Shadows** property, which must be enabled as appropriate. -->

场景中的每个 [网格渲染器 Mesh Renderer] 还具有 **投射阴影 Cast Shadows** 和 **接收阴影 Receive Shadows** 属性，它们必须按需开启。

[Mesh Renderer]: https://docs.unity3d.com/Manual/class-MeshRenderer.html
[网格渲染器 Mesh Renderer]: https://docs.unity3d.com/Manual/class-MeshRenderer.html

<!-- Enable **Cast Shadows** by selecting **On** from the drop-down menu to enable or disable shadow casting for the mesh. Alternatively, select **Two Sided** to allow shadows to be cast by either side of the surface (so backface culling is ignored for shadow casting purposes), or **Shadows Only** to allow shadows to be cast by an invisible GameObject. -->

在 **投射阴影 Cast Shadows** 的下拉菜单中选择 **On** 或 **Off** 可以开启或禁用该网格投射阴影。或者选择 **Two Sided**，以允许表面的两面都投射阴影（此时，背面剔除被忽略）；或者选择 **Shadows Only**，以允许一个不可见的游戏对象投射阴影。

<!-- ## Shadow mapping and the Bias property -->
## 阴影映射和偏差属性 Bias

<!-- The shadows for a given Light are determined during the final Scene rendering. When the Scene is rendered to the main Camera view, each pixel position in the view is transformed into the coordinate system of the Light. The distance of a pixel from the Light is then compared to the corresponding pixel in the shadow map. If the pixel is more distant than the shadow map pixel, then it is presumably obscured from the Light by another GameObject and it obtains no illumination. -->

光源的阴影在渲染最终场景期间被确定。当场景被渲染到主摄像机视图时，视图中每个像素的位置被转换为光源坐标。比较表面像素和阴影纹理中像素距光源的距离。如果表面像素的距离更远，那么表面像素可能被它与光源之间的另一个游戏对象所遮挡，所以它不会被照亮。

![Correct shadowing](https://docs.unity3d.com/uploads/Main/ShadowBiasGood.jpg)
<!-- > Correct shadowing -->
> 正确的投影

<!-- A surface directly illuminated by a Light sometimes appears to be partly in shadow. This is because pixels that should be exactly at the distance specified in the shadow map are sometimes calculated as being further away (this is a consequence of using shadow filtering, or a low-resolution image for the shadow map). The result is arbitrary patterns of pixels in shadow when they should really be lit, giving a visual effect known as “shadow acne”. -->

被光源直接照亮的表面，有时看起来部分位于阴影中。这是因为位于阴影中特定距离的像素，有时被计算为更远（这是使用了阴影过滤，或是为阴影纹理设置了低分辨率图像）。最终，位于阴影中的像素上的图纹，原本应该被真正照亮，却产生了成为了『阴影痤疮』的视觉效果。


![Shadow acne in the form of false self-shadowing artifacts](https://docs.unity3d.com/uploads/Main/ShadowBiasAcne.jpg)
<!-- > Shadow acne in the form of false self-shadowing artifacts -->
> 错误的自投影产生了阴影痤疮

<!-- To prevent shadow acne, a **Bias** value can be added to the distance in the shadow map to ensure that pixels on the borderline definitely pass the comparison as they should, or to ensure that while rendering into the shadow map, GameObjects can be inset a little bit along their normals. These values are set by the **Bias** and **Normal Bias** properties in the Light Inspector window when shadows are enabled. -->

为了防止阴影痤疮，可以让阴影纹理的距离加上 **Bias** 值，以确保位于边界的像素通过距离比较，或者，在渲染阴影纹理时，稍微修正游戏对象的法线。当开启阴影时，这些值可以通过灯光检视视图中的 **阴影偏差 Bias** 和 **阴影法线偏差 Normal Bias** 属性设置。

<!-- Do not set the **Bias** value too high, because areas around a shadow near the GameObject casting it are sometimes falsely illuminated. This results in a disconnected shadow, making the GameObject look as if it is flying above the ground. -->

不要将 **阴影偏差 Bias** 设置的太大，因为阴影周围靠近游戏对象的区域有时会被错误地照亮。从而导致阴影和游戏对象分离，使得游戏对象看起来好像是在地面上空飞行。

![A high Bias value makes the shadow appear disconnected from the GameObject](https://docs.unity3d.com/uploads/Main/ShadowBiasPeterPanning.jpg)
<!-- > A high **Bias** value makes the shadow appear “disconnected” from the GameObject -->
> **阴影偏差 Bias** 过大，使得阴影与游戏对象分离。

<!-- Likewise, setting the **Normal Bias** value too high makes the shadow appear too narrow for the GameObject: -->

同样地，**阴影法线偏差 Normal Bias** 过大，会使阴影相比游戏对象显得太窄：

![A high Normal Bias value makes the shadow shape too narrow](https://docs.unity3d.com/uploads/Main/ShadowBiasTooThin.jpg)
<!-- > A high **Normal Bias** value makes the shadow shape too narrow -->
> **阴影法线偏差 Normal Bias** 过大，使得阴影的形状太窄

<!-- In some situations, **Normal Bias** can cause an unwanted effect called “light bleeding”, where light bleeds through from nearby geometry into areas that should be shadowed. A potential solution is to open the GameObject’s [Mesh Renderer] and change the **Cast Shadows** property to **Two Sided**. This can sometimes help, although it can be more resource-instensive and increase performance overhead when rendering the Scene. -->

在某些情况下，**阴影法线偏差 Normal Bias** 可能导致称为『光线泄漏』的意外效果，光线穿过相邻的几何体，泄漏到被遮盖的区域。一个可行的解决方案是，打开游戏对象的 网格渲染器 Mesh Renderer，修改 **Cast Shadows** 属性为 **Two Sided**。但是这个方案可能需要更多的计算资源，增加渲染场景时的性能开销，尽管它在某些情况下确实有效。

[Mesh Renderer]: https://docs.unity3d.com/Manual/class-MeshRenderer.html

<!-- The bias values for a Light may need tweaking to make sure that unwanted effects occur. It is generally easier to gauge the right value by eye rather than attempting to calculate it. -->

为了避免发生这种意外效果，光源的阴影偏差可能需要调整。通常，通过眼睛来判定正确的偏差值更容易些，而不是尝试通过计算获得。

<!-- To further prevent shadow acne we are using a technique known as **Shadow pancaking** (see [Directional light shadows: Shadow pancaking]). This generally works well, but can create visual artifacts for very large triangles. -->

为了进一步防止阴影痤疮，我们使用了一种成为『阴影着陆』的技术（参见 [平行光阴影：阴影着陆]）。通常，这种技术是有效的，并且可以为非常大的三角形创建人为的视觉效果。

[Directional light shadows: Shadow pancaking]: https://docs.unity3d.com/Manual/DirLightShadows.html
[平行光阴影：阴影着陆]: https://docs.unity3d.com/Manual/DirLightShadows.html

![A low Shadow near plane offset value create the appearance of holes in shadows](https://docs.unity3d.com/uploads/Main/ShadowNearOffsetTooLow.png)
<!-- > A low **Shadow near plane offset** value create the appearance of holes in shadows -->
> 设置较低的 **阴影近剪裁平面偏移 Shadow near plane offset** 值，导致阴影中的孔状效果。

<!-- Tweak the **Shadow Near Plane Offset** property to troubleshoot this problem. Setting this value too high introduces shadow acne. -->

调整 **阴影近剪裁平面偏移 Shadow Near Plane Offset** 属性，可以解决这个问题。该值太大，也会导致阴影痤疮。

![Correct shadowing](https://docs.unity3d.com/uploads/Main/ShadowNearOffsetOk.png)
<!-- > Correct shadowing -->
> 正确的投影
