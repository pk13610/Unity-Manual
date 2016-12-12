<!-- # The Light inspector -->
# 灯光检视视图

<!-- [SWITCH TO SCRIPTING] -->

[切换到脚本参考页]

[SWITCH TO SCRIPTING]: https://docs.unity3d.com/ScriptReference/Light.html
[切换到脚本参考页]: https://docs.unity3d.com/ScriptReference/Light.html

<!-- Lights are a fundamental part of graphical rendering since they determine the shading of an object and the shadows it casts. See the [Lighting] and [Global Illumination] sections of the manual for further details about lighting concepts in Unity. -->

灯光是图形渲染的基础组成部分，因为它们决定了对象的着色和投射的阴影。有关 Unity 中光照概念的更多详细介绍，请参阅本手册手册的 [灯光类型] 和 [全局照明] 部分。

[Lighting]: https://docs.unity3d.com/Manual/LightingOverview.html
[Global Illumination]: https://docs.unity3d.com/Manual/GlobalIllumination.html
[光照]: https://docs.unity3d.com/Manual/LightingOverview.html
[全局光照]: https://docs.unity3d.com/Manual/GlobalIllumination.html

![](https://docs.unity3d.com/uploads/Main/LightInspectorV3.png)

<!-- ## Properties -->
## 属性

<!-- Property:   Function: -->

<!-- **Type**    The current type of light. Possible values are Directional, Point, Spot and Area (see the [Lighting Overview] for details of these types). -->

**Type** 灯光的当前类型。可选值有平行光 Directional、点光源 Point、聚光灯 Spot 和区域光 Area（这些类型的详细介绍请参阅 [光照]）。

[Lighting Overview]: https://docs.unity3d.com/Manual/Lighting.html

<!-- **Baking**  This allows you to choose if the light should be baked if Baked GI is selected. Mixed will also bake it, but it will still be present at runtime to give direct lighting to non-static objects. Realtime works both for Precomputed Realtime GI and when not using GI. See the [Global Illumination] section of the manual for further information about lightmaps and baking. -->

**Baking** 当前灯光是否应该被烘培，如果开启了 Baked GI，选择 Mixed 仍然会烘培，并且仍然会在运行时为非静态对象提供直接光。选择 Realtime，既适用于预计算全局 GI，也适用于不使用 GI 的情况。有关光照贴图和烘培的更多信息请参阅本手册的 [全局光照] 部分。

<!-- **Range**   How far light is emitted from the center of the object (Point and Spot lights only). -->

**Range** 从灯光对象中心发出的光的传播距离（仅限点光源和聚光灯）。

<!-- **Spot Angle**  Determines the angle (in degrees) at the base of a spot light’s cone (Spot light only). -->

**Spot Angle** 决定聚光灯椎体（光锥）的角度（以度为单位）。仅限聚光灯。


<!-- **Color**   The color of the light emitted. -->

**Color** 被发射的光的颜色。

<!-- **Intensity**   Brightness of the light. The default value for a Point, Spot or Area light is 1 but for a Directional light, it is 0.5. -->

**Intensity** 光的亮度（强度）。对于点光源、聚光灯和区域光，默认值是 1，对于平行光，默认值是 0.5。


<!-- **Bounce Intensity**    This allows you to vary the intensity of indirect light (ie, light that is bounced from one object to another. The value is a multiple of the default brightness calculated by the GI system; if you set Bounce Intensity to a value greater than one then bounced light will be made brighter, while a value less than one will make it dimmer. This is useful, for example, when a dark surface in shadow (such as the interior of a cave) needs to be rendered brighter in order to make detail visible. Or alternatively, if you want to use Precomputed Realtime GI in general, but want to limit a single light to give direct light only, you can set its Bounce Intensity to 0. See the [Global Illumination] section of the manual for further information. -->

**Bounce Intensity** 改变非直接光（例如，从一个对象弹射向另一个对象的光）的强度。该值是 GI 系统计算的默认亮度的倍数；如果该值大于 1，那么弹射光将变亮，如果该值小于 1，则变暗。这个功能是有用的，例如，位于阴影中的暗表面（例如洞穴的内部）需要渲染的更亮，以使细节可见。还有一种方案，如果想要使用预计算实时 GI，但是想要限制某个灯光为只提供直接光，你可以设置该值为 0。更多相关信息请参阅本手册的 [全局光照] 部分。

<!-- **Shadow Type** Determines whether Hard Shadows Soft Shadows or no shadows at all will be cast by this light. -->

**Shadow Type** 决定灯光是否投射硬阴影（尖锐阴影）、软阴影（柔和阴影）或没有阴影。

<!-- **Baked Shadow Radius** If shadows are enabled then this property adds some artificial softening to the edges of shadows cast by point or spot lights (in theory, light originating from a point casts perfectly sharp shadows but this situation rarely occurs in nature). -->

**Baked Shadow Radius** 如果启用了阴影，这个属性会为点光源或聚光灯投射的阴影边缘添加一些虚化效果（理论上，源自某个点的光线投射出完美的锐利阴影，但是这种情况现在自然界中很少发生）。

<!-- **Baked Shadow Angle**  If shadows are enabled then this property adds some artificial softening to the edges of shadows cast by directional lights (in theory, parallel light rays coming from a truly “directional” source cast perfectly sharp shadows but natural light sources don’t strictly behave like this). -->

**Baked Shadow Angle** 如果启动了阴影，这个属性会为平行光投射的阴影边缘添加一些虚化效果（理论上，来自真实平行光源的平行光线投射出完美的锐利阴影，但是自然光源的行为不严格遵循该规则）。

<!-- **Draw Halo**   If checked, a spherical halo of light will be drawn with a radius equal to Range. See also the page about the [Halo] component. -->

**Draw Halo** 如果选中，将绘制灯光的球形光晕，光晕半径等于 Range。另请参阅 [光晕] 组件。

[Halo]: https://docs.unity3d.com/Manual/class-Halo.html
[光晕]: https://docs.unity3d.com/Manual/class-Halo.html

<!-- **Flare**   Optional reference to the [Flare] that will be rendered at the light’s position. -->

**Flare** 可选。引用一个 [镜头光晕]，将在灯关所处位置渲染。

[Flare]: https://docs.unity3d.com/Manual/class-Flare.html
[镜头光晕]: https://docs.unity3d.com/Manual/class-Flare.html

<!-- **Render Mode** Importance of this light. This can affect lighting fidelity and performance, see _Performance Considerations_ below. The options are Auto (the rendering method is determined at runtime depending on the brightness of nearby lights and current [Quality Settings]), Important (the light is always rendered at per-pixel quality) and Not Important (the light is always rendered in a faster, vertex/object light mode). Use Important mode only for the most noticeable visual effects (eg, headlights of a player’s car). -->

**Render Mode** 该灯光的重要性。可能会影响光照保真度和性能，请参阅下面的_性能注意事项_。可选值有 Auto（在运行时决定渲染模式，取决于附件灯关的亮度和当前的 [画质设置]），Important（该灯光始终以像素级别的质量渲染）和 Not Important（该灯管始终以更快的顶点光照模式渲染）。仅为最值得注意的视觉效果使用 Important 模式（例如，玩家所驾驶车辆的前灯）。

[Quality Settings]: https://docs.unity3d.com/Manual/class-QualitySettings.html
[画质设置]: https://docs.unity3d.com/Manual/class-QualitySettings.html

<!-- **Culling Mask**    Use to selectively exclude groups of objects from being affected by the light; see [Layers](https://docs.unity3d.com/Manual/Layers.html). -->

**Culling Mask** 剔除遮罩，用于有选择性地排除该灯光所能影响的对象分组；请参阅 [分层]。

[Layers]: https://docs.unity3d.com/Manual/Layers.html
[分层]: https://docs.unity3d.com/Manual/Layers.html

<!-- ## Details -->
## 详细介绍

<!-- You can create a texture that contains an alpha channel and assign it to the **Cookie** variable of the light. The Cookie will be projected from the light. The Cookie’s alpha mask modulates the light amount, creating light and dark spots on surfaces. They are a great way af adding lots of complexity or atmosphere to a scene. -->

你可以创建一张含有 alpha 通道的纹理，并分配给灯光的 **Cookie** 变量。这个 Cookie 将被灯光投射。Cookie 的 alpha 蒙板调节光量，在表面上创建明亮和阴暗斑点。可以非常有效地为场景添加复杂的氛围效果。

<!-- All [built-in shaders] in Unity seamlessly work with any type of light. However, **VertexLit** shaders cannot display Cookies or Shadows. -->

Unity 中的所有 [内置着色器] 都可以和任意类型的灯光无缝协作。不过，**顶点光照** 着色器无法显示 Cookie 或阴影。

[built-in shaders]: https://docs.unity3d.com/Manual/Built-inShaderGuide.html
[内置着色器]: https://docs.unity3d.com/Manual/Built-inShaderGuide.html

<!-- All Lights can optionally cast [Shadows]. This is done by selecting either **Hard Shadows** or **Soft Shadows** for the **Shadow Type** property of each individual Light. For more information about shadows, please read the [Shadows] page. -->

所有灯管可以选择性地投射 [阴影]。通过选择 **Shadow Type** 为 **Hard Shadows** 或 **Soft Shadows** 来完成。有关阴影的更多信息请阅读 [阴影] 页。

[Shadows]: https://docs.unity3d.com/Manual/ShadowOverview.html
[阴影]: https://docs.unity3d.com/Manual/ShadowOverview.html

<!-- ## Directional Light Shadows -->
## 平行光阴影

<!-- Shadows from directional lights are explained in depth on [this page]. Note that shadows are disabled for directional lights with cookies when forward rendering is used. It is, however, possible to write custom shaders to enable shadows in such a case by using the **fullforwardshadows** tag; see [this page](https://docs.unity3d.com/Manual/SL-SurfaceShaders.html) for further details. -->

来自平行光的阴影在 [这个页面] 深入解释。注意，当采用正向渲染时，带有 Cookie 的平行光的阴影将被禁用。不过，在这种情况下，可以编写自定义着色器，使用 **fullforwardshadows** 标签来启用阴影；更多详情请参阅 [这个页面](https://docs.unity3d.com/Manual/SL-SurfaceShaders.html)。

[this page]: https://docs.unity3d.com/Manual/DirLightShadows.html
[这个页面]: https://docs.unity3d.com/Manual/DirLightShadows.html

<!-- ## Hints -->
## 提示

<!-- 
* Spot lights with cookies can be extremely effective for making light coming in from windows.
* Low-intensity point lights are good for providing depth to a scene.
* For maximum performance, use a [VertexLit] shader. This shader only does per-vertex lighting, giving a much higher throughput on low-end cards.
* Auto lights can cast dynamic shadows over lightmapped objects without adding extra illumination. For this to work the Auto lights must be active when the Lightmap is baked. Otherwise they render as real time lights.
 -->

* 带有 Cookie 的聚光灯可以非常有效地创建窗户透射光。
* 低强度的点光源适合为场景提供深度。
* 为了获得最佳性能，请使用 [顶点光照] 着色器。这个着色器只会计算每个顶点的光照，为低端显卡提供更高的吞吐量。
* 重要性为 Auto 的灯光可以在使用了灯光贴图的对象上投射动态阴影，并且不会添加额外的光照。为了实现这点，当烘培光照贴图时，该灯光必须处于激活状态。否则，将作为实时灯光进行渲染。

[VertexLit]: https://docs.unity3d.com/Manual/Built-inShaderGuide.html
[顶点光照]: https://docs.unity3d.com/Manual/Built-inShaderGuide.html
