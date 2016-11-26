<!-- > [Content and Context](http://docs.unity3d.com/Manual/StandardShaderContextAndContent.html) -->

<!-- Unity Manual > Graphics > Graphics Overview > Materials, Shaders & Textures > Standard Shader > Content and Context -->

<!-- # Content and Context -->
# 内容和上下文

<!-- When thinking about lighting in Unity, it is handy to divide the concepts into what we call the **content** the item being lit and rendered, and the **context**, which is the lighting that exists in the scene which affects the object being lit. -->
当考虑 Unity 中的光照时，可以非常方便地分成两个概念：**内容**和**上下文**。内容是指被渲染和照亮的物体，上下文是指存在于场景中的光照，会照亮（影响）物体。

<!-- ## The Context -->
## 上下文

<!-- When lighting an object it is important to understand which sources of light are affecting the object. There are usually direct light sources in your scene: Game Object lights that you may have placed around your scene. There are also indirect light sources such as reflections and bounced light. These all have an effect on the object’s material to give the final result that the camera sees across the surface of the object. -->
当照亮一个物体时，重要的是要了解哪些光源正在在影响物体。在你的场景中，通用会有直接光源，那些你可能已经放在场景中的光源对象。还会有非直接光源，例如反射光和反弹光。这些都会影响物体的材质，最终生成摄像机在物体表面上所看到的结果。

<!-- This is not a hard and fast separation, often what might be considered “content” could also be the part of the lighting context for another object. -->
这种划分并不是固定的，往往被认为是『内容』物体，也可以是另一个物体的光照上下文。

<!-- A good example of this would be a building situated in a desert landscape. The building would take light information from the skybox, and perhaps bounced light from the surrounding ground. -->
一个很好的例子是位于沙漠环境的建筑物。建筑物从天空盒获取光照信息，并且可能弹射周围地面的光照。

<!-- However there may be a character standing near an exterior wall of the building. For this character, the building is part of the lighting context - it may be casting a shadow, it may be casting bounced light from its wall onto the character, or the character may have reflective parts which are directly reflecting the building itself. -->
不过，可能有个角色正站在建筑物的外墙附近。对于这个角色，建筑物是光照上下文的一部分 — 建筑物可能投射阴影，可能把光照从墙壁弹射到角色上，或者角色身上的某个部位（镜面）可以直接反射建筑物。

<!-- ### The Default Lighting Context -->
### 默认光照上下文

<!-- At startup, Unity 5 shows an empty scene. This scene already has a default lighting context available with ambient, skydome-based reflections and a directional light. Any object placed in that scene should, by default, have all lighting it needs to look correct. -->
Unity 5 启动时会显示一个空场景。该场景中有一个默认的光照上下文：天幕反射和一个平行光。默认情况下，任何放入该场景中的物体，都应该拥有必需的光照，使整个场景看起来是正确的。

<!-- Let’s add a sphere to the scene, to see the effect of the default lighting context. -->
让我们向场景添加一个球体，看看默认光照上下文的效果。

![](http://docs.unity3d.com/uploads/Main/StandardShaderGOCreateSphereMenu.png)

<!-- The added sphere will be using the Standard shader by default. Focusing the camera on the sphere will result on something like this: -->
默认情况下，添加的球体将使用标准着色器。将相机对焦在球体上会得到这样的东西：

![](http://docs.unity3d.com/uploads/Main/StandardShaderSphereInScene.png)

<!-- Notice the reflection along the edges of the sphere as well as the subtle ambient, from brown (bottom) to the sky blue (top). By default, in an empty scene, all lighting context is derived from the skybox and a directional light (which is added to the Scene by default). -->
请注意沿着球体边缘的反射光，以及细微的环境光，从棕色（底部）到天蓝色（顶部）。默认情况下，在一个空场景中，所有光照上下文都来自天空盒和一个平行光（默认被添加到场景中）。

<!-- Of course this is the default setup, a single lighting and sky reflection may not be enough in some cases. You can easily add more lighting and reflection probes: -->
当前这是默认设置，在某些情况下，单个光照和天空反射可能不够。你可以轻松地添加更多光照和反射探针：

<!-- For an in-depth view on how reflection and light probes work please see the documentation on [light probes](http://docs.unity3d.com/Manual/LightProbes.html) and [reflection probes](http://docs.unity3d.com/Manual/ReflectionProbes.html). -->
要深入了解反射光和光照探针的工作远离，请参阅有关 [光照探针](http://docs.unity3d.com/Manual/LightProbes.html) 和 [反射探针](http://docs.unity3d.com/Manual/ReflectionProbes.html)。

<!-- ## Skyboxes -->
## 天空盒

<!-- A Skybox, baked or procedural, can be an integral part of your lighting setup. It can be used to control the ambient lighting and the reflections in your objects in addition to rendering the sky. Procedural Skyboxes also allow you to set the colours directly and create a sun disc instead of using a bitmap - more information can be found in the [Skybox Documentation](http://docs.unity3d.com/Manual/class-Skybox.html) -->
天空盒，无论是预先烘培还是程序实时生成，是光照设置不可或缺的组成部分。除了渲染天空外，它还可以用于控制环境光照和物体的反射光。程序实时生成的天空盒允许直接设置颜色，并创建一个太阳光盘，而不是使用一张位图 - 更多信息可以 [天空盒文档] 中找到。

[天空盒文档]: http://docs.unity3d.com/Manual/class-Skybox.html

<!-- While reflecting the skybox can be useful for many objects in your scenes, particularly outdoor scenes, there are often cases where you need to vary the reflections an object uses - there may be dark areas in an outdoor scene, such as alleyways or dense forest, or you may have interior areas which require reflections to match each room. -->
对于场景中的许多物体来说，虽然反射天空盒是有用的，特别是户外场景，但是也有许多情况，需要你改变物体的反射设置 — 可能是户外场景的黑暗区域，例如小巷或茂密的森林，或者某些室内区域需要单独设置反射光照。

<!-- To meet the needs of these various reflective requirements, Unity has [reflection probes](http://docs.unity3d.com/Manual/class-ReflectionProbe.html) which allow you to sample the environment in your scene at a certain point in space, for use as the ambient light and reflection source for any objects near that point instead of the default skybox. Reflection probes can be placed around your scene in any locations where the scene’s skybox is not sufficient or appropriate. -->
为了满足各种反射需求，Unity 提供了 [反射探针]，允许你在空间中的某个点，对场景环境进行采样，用该点附近的环境光和反射源，来代替默认的天空盒。反射探针可以放置在场景中的任意位置，在该位置，天空盒不能满足光照需求，或者不适合。

[反射探针]: http://docs.unity3d.com/Manual/class-ReflectionProbe.html

<!-- ## Global Illumination -->
## 全局光照

<!-- The concept of Global Illumination is integral to Unity 5. Both the Standard shader and Unity 5’s GI systems have been designed to play well with each other. The GI system takes care of creating and tracking bounced light, light from emissive materials and light from the environment. You can find the details [here](http://docs.unity3d.com/Manual/GlobalIllumination.html). -->
全局光照概念是 Unity 5 不可或缺的部分。标准着色器和全局光照彼此协作。全局光照系统负责创建和跟踪反射光、来自发光材质的光，以及来自环境的光。你可以在 [这里] 找到更多细节。

[这里]: http://docs.unity3d.com/Manual/GlobalIllumination.html

<!-- The context is a critical part of the overall look of the image. In this example you can see how a scene reflects changes in context, while content and camera remains the same. -->
上下文是整体图像的关键部分。在这个示例中，你可以看到，在内容和摄像机保持不变的情况下，场景是如何反射上下文的。

![](http://docs.unity3d.com/uploads/Main/StandardShaderChangingSkyboxesEffect.gif)

<!-- ## The Content -->
## 内容

<!-- The content is the term used to describe the objects in your scene that are being rendered. Their appearance is a result of the lighting context acting on the materials that have been applied to the objects. -->
内容是一个术语，用于描述场景中正在渲染的物体。它是光照上下文应用于物体材质之后的结果。

<!-- ### The Material Editor -->
### 材质编辑器

<!-- When viewing a material in the inspector which uses the Standard Shader, the editor displays all parameters for the material including textures, blending modes, masking and secondary maps. At a glance you be able to see which features are used and preview the material. As the Standard shader is data-driven: Unity will only use the shader code required by the configuration the user has set for the material. In other words if a feature or texture slot of the material is not used, there is no cost for it and the shader combination is optimised behind the scenes. -->
在检视试图中查看使用了标准着色器的材质时，编辑器将显示材质的所有参数，包括纹理、混合模式、遮罩和辅助图。你可以一目了然地看到哪些功能被使用，并且实时预览材质。标准着色器是数据驱动的：Unity 将只使用用户已经设置过参数的着色器代码。换句话说，如果材质的某个功能或纹理插槽没有被用到，那么就不会消耗性能，着色器在幕后执行这一优化。

![Tip: You can Ctrl+click on the texture thumbnails for a large preview, which will also let you check the contents of the color and alpha channels separately!](http://docs.unity3d.com/uploads/Main/StandardShaderMaterialInspector.png)
<!-- > Tip: You can Ctrl+click on the texture thumbnails for a large preview, which will also let you check the contents of the color and alpha channels separately! -->
> 你可以按住 Ctrl 点击纹理缩略图，来查看它的大预览图，并且允许你检查颜色和 alpha 通道。

<!-- ### How to create a material -->
### 如何创建材料

<!-- The Standard shader allows for many configurations in order to represent a great variety of material types. Values can be set with texture maps or colour pickers and sliders. Generally UV mapping is required in conjunction with textures to describe which part of your mesh refers to which part of the texture map. The Standard Shader material allows you therefore to have different material properties across the same mesh when used in conjunction with specular and smoothness map or a metallic map. In other words you can create rubber, metal and wood on one mesh where the resolution of the texture can exceed the polygon topology allowing for smooth borders and transition between material types, of course this has implications for a greater complexity in the workflow, but this will depend on your texture creation method. -->
为了支持各种各样的材质类型，标准着色器提供了许多配置。可以使用纹理贴图、颜色选择起和滑动器设置值。通常，UV 映射是必须的，泳衣描述网格和问题贴图的对应关系。使用了标准着色器的材质，支持在同一个网格上设置多个的材质属性，例如反射贴图、平滑度贴图和金属贴图，并把它们结合起来渲染。换句话说，你可以在同一个网格上同时设置橡胶、金属和木材纹理；纹理的分辨率可以超过网格，从而支持平滑边角和材质过度，当然，这会让工作流程更复杂，不过，这将取决于材质的创建方式。

<!-- Textures for your materials tend to be generated in one of two ways - painting and compositing in a 2D image editor like Photoshop, or rendering / baking from your 3D package, where you can also make use of higher resolution models to generate your normal maps and occlusion maps in addition to the albedo, specular and other maps. This workflow varies dependent on the external packages used. -->
材质纹理通常有两种生成方式 — 在 2D 图像编辑器中绘制和合成，或者在 3D 软件中渲染和烘培，第二种方式可以使用更高分辨率的模型生成反射贴图、法线贴图和散射贴图等。工作流程取决于使用的外部软件。

<!-- Generally no texture map should contain inherent lighting (shadows, highlights, etc). One of the advantages of PBS is that objects react to light as you would expect, which is not possible if maps already contain lighting information. -->
通常，纹理贴图不应该包含固定光照（例如阴影、高光等）。PBS 的优点之一是，物体可以如你期望的那样响应光照，但是如果贴图已经包含了光照信息，就无法使用这一优点。
