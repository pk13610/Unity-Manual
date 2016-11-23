Unity Manual > Graphics > Graphics Overview > Lighting > Light troubleshooting and performance

# Light troubleshooting and performance

Lights can be rendered using either of two methods:

* **Vertex lighting** calculates the illumination only at the vertices of meshes and interpolates the vertex values over the rest of the surface. Some lighting effects are not supported by vertex lighting but it is the cheaper of the two methods in terms of processing overhead. Also, this may be the only method available on older graphics cards.
* **Pixel lighting** is calculated separately at every screen pixel. While slower to render, pixel lighting does allow some effects that are not possible with vertex lighting. Normal-mapping, light cookies and realtime shadows are only rendered for pixel lights. Additionally, spotlight shapes and point light highlights look much better when rendered in pixel mode.

![Comparison of a spotlight rendered in pixel vs vertex mode](http://docs.unity3d.com/uploads/Main/LightPixVertComp.svg)
> Comparison of a spotlight rendered in pixel vs vertex mode

Lights have a big impact on rendering speed, so lighting quality must be traded off against frame rate. Since pixel lights have a much higher rendering overhead than vertex lights, Unity will only render the brightest lights at per-pixel quality and render the rest as vertex lights. The maximum number of pixel lights can be set in the [Quality Settings](http://docs.unity3d.com/Manual/class-QualitySettings.html) for standalone build targets.

You can favour a light to be rendered as a pixel light using its **Render Mode** property. A light with the mode set to **Important** will be given higher priority when deciding whether or not to render it as a pixel light. With the mode set to **Auto** (the default), Unity will classify the light automatically based on how much a given object is affected by the light. The lights that are rendered as pixel lights are determined on an object-by-object basis.

See the page about [Optimizing Graphics Performance](http://docs.unity3d.com/Manual/OptimizingGraphicsPerformance.html) for further information.

## Shadow performance

Realtime shadows have quite a high rendering overhead, so you should use them sparingly. Any objects that might cast shadows must first be rendered into the shadow map and then that map will be used to render objects that might receive shadows. Enabling shadows has an even bigger impact on performance than the pixel/vertex trade-off mentioned above.

Soft shadows have a greater rendering overhead than hard shadows but this only affects the GPU and does not cause much extra CPU work.

The [Quality Settings](http://docs.unity3d.com/Manual/class-QualitySettings.html) include a **Shadow Distance** value. Objects that are beyond this distance from the camera will be rendered with no shadows at all. Since the shadows on distant objects will not usually be noticed anyway, this can be a useful optimisation to reduce the number of shadows that must be rendered.

A particular issue with directional lights is that a single light can potentially illuminate the whole of a scene. This means that the shadow map will often cover a large portion of the scene at once and this makes the shadows susceptible to a problem known as “perspective aliasing”. Simply put, perspective aliasing means that shadow map pixels seen close to the camera look enlarged and “chunky” compared to those farther away. Although you can just increase the shadow map resolution to reduce this effect, the result is that rendering resources are wasted for distant areas whose shadow map looked fine at the lower resolution.

A good solution to the problem is therefore to use separate shadow maps that decrease in resolution as the distance from camera increases. These separate maps are known as **cascades**. From the [Quality Settings](http://docs.unity3d.com/Manual/class-QualitySettings.html), you can choose zero, two or four cascades; Unity will calculate the positioning of the cascades within the camera’s frustum. Note that cascades are only enabled for directional lights. See [directional light shadows](http://docs.unity3d.com/Manual/DirLightShadows.html) page for details.

## How the size of a shadow map is calculated

The first step in calculating the size of the map is to determine the area of the screen view that the light can illuminate. For directional lights, the whole screen can be illuminated but for spot lights and point lights, the area is the onscreen projection of the shape of the light’s extent (a sphere for point lights or a cone for spot lights). The projected shape has a certain width and height in pixels on the screen; the larger of those two values is then taken as the light’s “pixel size”.

When the shadow map resolution is set to High (from the Quality Settings) the shadow map’s size is calculated as follows:

* **Directional lights:** [NextPowerOfTwo](http://docs.unity3d.com/ScriptReference/Mathf.NextPowerOfTwo.html) (pixelSize * 1.9), up to a maximum of 2048.
* **Spot lights:** [NextPowerOfTwo](http://docs.unity3d.com/ScriptReference/Mathf.NextPowerOfTwo.html) (pixelSize), up to a maximum of 1024.
* **Point lights:** [NextPowerOfTwo](http://docs.unity3d.com/ScriptReference/Mathf.NextPowerOfTwo.html) (pixelSize * 0.5), up to a maximum of 512.
If the graphics card has 512MB or more video memory, the upper shadow map limits are increased to 4096 for directional lights, 2048 for spot lights and 1024 for point lights.

At *Medium* shadow resolution, the shadow map size is half the value for **High** resolution and for *Low*, it is a quarter of the size.

Point lights have a lower limit on size than the other types is because they use cubemaps for shadows. That means that six cubemap faces at this resolution must be kept in video memory at once. They are also quite expensive to render, as potential shadow casters might need to be rendered into all six cubemap faces.

## Limited Memory Conditions

If your game is running very low on video memory then it will automatically reduce the resolution of shadow maps below the usual value.

Generally, the screen data (backbuffer, frontbuffer, depth buffer) and data for render textures *must* be held in video memory. The memory needed to store the screen and render texture data will be subtracted from the total available; *one third* of the remaining video memory will then be reserved for use by shadow maps. The resolution of any given shadow map will be reduced as far as necessary to fit into this space (ie, the calculations given above are still applied but with the reduced resolution).

Assuming all regular textures, vertex data and other graphics objects could be swapped in and out of video memory, the theoretical maximum amount of VRAM that could be used by a shadow map would be given by the formula `(TotalVideoMemory - ScreenMemory - RenderTextureMemory)`. However, the amounts of memory taken by screen and render textures can never be determined exactly. Furthermore, some objects should not be swapped; performance would suffer badly if all textures were constantly swapped in and out, for example. To allow for this, Unity does not allow a shadow map to exceed one third of “generally available” video memory, and this compromise is found to work quite well in practice.

## Troubleshooting shadows

If you find that one or more objects are not casting shadows then you should check the following points:

* Old graphics hardware may not support shadows. See below for a list of minimal hardware specs that can handle shadows.
* Shadows can be disabled in the [Quality Settings](http://docs.unity3d.com/Manual/class-QualitySettings.html). Make sure that you have the correct quality level enabled and that shadows are switched on for that setting.
* All [Mesh Renderers](http://docs.unity3d.com/Manual/class-MeshRenderer.html) in the scene must be set up with their *Receive Shadows* and *Cast Shadows* correctly set. Both are enabled by default but check that they haven’t been disabled unintentionally.
* Only opaque objects cast and receive shadows so objects using the built-in [Transparent](http://docs.unity3d.com/Manual/shader-TransparentFamily.html) or Particle shaders will neither cast nor receive. Generally, you can use the [Transparent Cutout](http://docs.unity3d.com/Manual/shader-TransparentCutoutFamily.html) shaders instead for objects with “gaps” such as fences, vegetation, etc. Custom [Shaders](http://docs.unity3d.com/Manual/Shaders.html) must be pixel-lit and use the [Geometry render queue](http://docs.unity3d.com/Manual/SL-SubShaderTags.html).
* Objects using **VertexLit** shaders can’t receive shadows but they can cast them.
* With the [Forward rendering path](http://docs.unity3d.com/Manual/RenderTech-ForwardRendering.html), some shaders allow only the brightest directional light to cast shadows (in particular, this happens with Unity’s legacy built-in shaders from 4.x versions). If you want to have more than one shadow-casting light then you should use the [Deferred Shading](http://docs.unity3d.com/Manual/RenderTech-DeferredShading.html) rendering path instead. You can enabled your own shaders to support “full shadows” by using the `fullforwardshadows` [surface shader](http://docs.unity3d.com/Manual/SL-SurfaceShaders.html) directive.

## Hardware support for shadows

Built-in shadows work on almost all devices supported by Unity. The following cards are supported on each platform:

### PC (Windows/Mac/Linux)

* Generally all GPUs support shadows. Exceptions might occur in some really old GPUs (for example, Intel GPUs made in 2005).

### Mobile

* iPhone 4 does not support shadows. All later models starting with iPhone 4S and iPad 2 support shadows.
* Android: Requires Android 4.0 or later, and `GL_OES_depth_texture` support. Most notably, some Android Tegra 2/3-based Android devices do not have this, so they don’t support shadows.
* Windows Phone: Shadows are only supported on DX11-class GPUs (Adreno 4xx/5xx).

## Consoles

All consoles support shadows.
