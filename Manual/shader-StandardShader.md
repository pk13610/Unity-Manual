<!-- > [Standard Shader](http://docs.unity3d.com/Manual/shader-StandardShader.html) -->

<!-- Unity Manual > Graphics > Graphics Overview > Materials, Shaders & Textures > Standard Shader -->

<!-- # Standard Shader -->
# 标准着色器

<!-- The Unity Standard Shader is a built-in shader with a comprehensive set of features. It can be used to render “real-world” objects such as stone, wood, glass, plastic and metal, and supports a wide range of shader types and combinations. Its features are enabled or disabled by simply using or not using the various texture slots and parameters in the material editor. -->
Unity 标准着色器是一个内置着色器，具有全面的功能。它可以用于渲染『真实世界』的对象，例如，石头、木材、玻璃、塑料和金属，并支持各种各样的着色器类型和组合。通过使用或不使用材质编辑器中的各种纹理插槽和参数，可以简单地启动或禁用其功能。

<!-- The Standard Shader also incorporates an advanced lighting model called **Physically Based Shading**. Physically Based Shading (PBS) simulates the interactions between materials and light in a way that mimics reality. PBS has only recently become possible in real-time graphics. It works at its best in situations where lighting and materials need to exist together intuitively and realistically. -->
标准着色起还包括一个称为 **物理着色器（Physically Based Shading，PBS）** 的高级光照模型。物理着色器以模拟真实世界的方式模拟材质和光照之间的相互作用。物理着色器最近才在实时图形中变为可能。最适合物理着色器的场景是，光照和材质需要直观并真实地共存时。

<!-- The idea behind our Physically Based Shader is to create a user-friendly way of achieving a consistent, plausible look under different lighting conditions. It models how light behaves in reality, without using multiple ad-hoc models that may or may not work. To do so, it follows principles of physics, including energy conservation (meaning that objects never reflect more light than they receive), Fresnel reflections (all surfaces become more reflective at grazing angles), and how surfaces occlude themselves (what is called Geometry Term), among others. -->
物理着色器背后的想法是，在不同光照条件下，以用户友好的方式，实现一致、可信的视觉效果。它模拟了光照在真实世界中的行为，并且不需要使用其他特殊模型（不管特殊模型可以运行或不可运行）。为此，物理着色器遵循物理学法则，包括能量守恒（对象反射的光永远不会超过接收的光）、菲涅尔反射（所有表面在掠射角时反射更多的光），和表面如何闭合自身（几何术语）。

<!-- The Standard Shader is designed with hard surfaces in mind (also known as “architectural materials”), and can deal with most real-world materials like stone, glass, ceramics, brass, silver or rubber. It will even do a decent job with non-hard materials like skin, hair and cloth. -->
标准着色器的设计考虑了硬表面（也成为『建筑材料』），可以处理大多数真实世界的材料，如石头、玻璃、陶瓷、黄铜或橡胶。它甚至可以处理非硬材料，如皮肤、头发和衣服。

![A scene rendered using the standard shader on all models](http://docs.unity3d.com/uploads/Main/StandardShaderIntroVikingScene.png)
<!-- > A scene rendered using the standard shader on all models -->
> 在所有模型上使用标准着色起渲染的场景

<!-- With the Standard Shader, a large range of shader types (such as such as Diffuse, Specular, Bumped Specular, Reflective) are combined into a single shader intended to be used across all material types. The benefit of this is that the same lighting calculations are used in all areas of your scene, which gives a realistic, consistent and believable distribution of light and shade across all models that use the shader. -->
通过标准着色器，大量的着色器类型（例如，漫反射、镜面、凹凸镜面、反射）被合并为单个着色器，应用于所有材质类型。这么做的好处是，在场景的所有区域都使用同样的光照计算，从而为使用标准着色器的所有模型提供真实、一直、可信的光照和阴影分布。

<!-- ## Terminology -->
## 术语

<!-- There are a number of concepts that are very useful when talking about Physically Based Shading in Unity. These include: -->
在谈论 Unity 的物理着色器时，有许多概念非常有用。包括：

<!-- * **Energy conservation** - This is a physics-based concept that ensures objects never reflect more light than they receive. The more specular a material is, the less diffuse it should be; the smoother a surface is, the stronger and smaller the highlight gets. -->
* **能量守恒** —— 这是一个物理概念，确保对象反射的光不会超过接收的光。材质越接近镜面，散射的光越少；表面越光滑，反射的光越强，反射的光束越小。

![The light rendered at each point on a surface is calculated to be the same as the amout of light received from its environment. The microfacets of rough surfaces are affected by light from a wider area. Smoother surfaces give stronger and smaller highlights. Point A reflects light from the source towards the camera. Point B takes on a blue tint from ambient light from the sky. Point C takes its ambient and reflective lighting from the surrounding ground colours.](http://docs.unity3d.com/uploads/Main/StandardShaderEnergyConservation.png)
<!-- > The light rendered at each point on a surface is calculated to be the same as the amout of light received from its environment. The microfacets of rough surfaces are affected by light from a wider area. Smoother surfaces give stronger and smaller highlights. Point A reflects light from the source towards the camera. Point B takes on a blue tint from ambient light from the sky. Point C takes its ambient and reflective lighting from the surrounding ground colours. -->
> 在表面每个点处渲染的光与从环境接收的光的数量相等。粗糙表面的细微颗粒受到来自更大区域的光的影响。越平滑的表面，反射的光越越强，反射的光束越小。点 A 将光从光源反射到摄像机。点 B 从天空的环境光获得蓝色色调。点 C 接收环境光，并反射来自周围地面的光。

<!-- * **High Dynamic Range (HDR)** - This refers to colours outside the usual 0–1 range. For instance, the sun can easily be ten times brighter than a blue sky. For an in-depth discussion, see the Unity Manual [HDR](https://docs.unity3d.com/550/Documentation/Manual/HDR.html) page. -->
* **高动态范围图像（High Dynamic Range，HDR）** — 通常指 0 - 1 范围之外的光。例如，太阳光的亮度比蓝天高 10 倍。相关的深入讨论，请参阅 Unity 手册的 [HDR](https://docs.unity3d.com/550/Documentation/Manual/HDR.html) 页。

![A scene using High Dynamic Range. The sunlight reflecting in the car window appears far brighter than other objects in the scene, because it has been processed using HDR](http://docs.unity3d.com/uploads/Main/GlowWithHdrAdjusted.png)
<!-- > A scene using High Dynamic Range. The sunlight reflecting in the car window appears far brighter than other objects in the scene, because it has been processed using HDR -->
> 一个使用高动态范围图像的场景。从车窗反射的太阳光比场景中的其他对象明亮的多，因为它已经用 HDR 处理过。
