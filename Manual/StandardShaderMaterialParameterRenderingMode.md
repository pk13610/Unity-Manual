<!-- > [Rendering Mode](http://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html) -->

<!-- Unity Manual > Graphics > Graphics Overview > Materials, Shaders & Textures > Standard Shader > Material parameters > Rendering Mode -->

<!-- # Rendering Mode -->
# 渲染模式

![A Standard Shader material with default parameters and no values or textures assigned. The Rendering Mode parameter is highlighted.](http://docs.unity3d.com/uploads/Main/StandardShaderParameterRenderMode.png)
<!-- > A Standard Shader material with default parameters and no values or textures assigned. The Rendering Mode parameter is highlighted. -->
> 一个具有默认参数并且未分配值和纹理的标准着色器材质。参数『渲染模式』被突出显示。

<!-- The first Material Parameter in the Standard Shader is **Rendering Mode**. This allows you to choose whether the object uses transparency, and if so, which type of blending mode to use. -->
标准着色器的第一个参数是**渲染模式**。该参数描述对象是否透明。

<!-- 
* **Opaque** - Is the default, and suitable for normal solid objects with no transparent areas.
* **Cutout** - Allows you to create a transparent effect that has hard edges between the opaque and transparent areas. In this mode, there are no semi-transparent areas, the texture is either 100% opaque, or invisible. This is useful when using transparency to create the shape of materials such as leaves, or cloth with holes and tatters.
* **Transparent** - Suitable for rendering realistic transparent materials such as clear plastic or glass. In this mode, the material itself will take on transparency values (based on the texture’s alpha channel and the alpha of the tint colour), however reflections and lighting highlights will remain visible at full clarity as is the case with real transparent materials.
* **Fade** - Allows the transparency values to entirely fade an object out, including any specular highlights or reflections it may have. This mode is useful if you want to animate an object fading in or out. It iss not suitable for rendering realistic transparent materials such as clear plastic or glass because the reflections and highlights will also be faded out.
 -->
* **不透明** — 默认值，适用于没有透明区域的常规固态物体。
* **镂空** — 允许你创建在不透明和透明区域之间具有硬边缘的透明效果。在该模式下，没有半透明区域，纹理或者 100% 不透明，或者不可见。当创建带有透明区域的材质时，例如叶子、带孔衣服和碎布这类形状，使用该模式。
* **透明** — 适用于渲染逼真的透明材质，例如塑料或玻璃。在该模式下，材质自身具有透明度（基于纹理的 alpha 通道和色调的 alpha 值），并且，如同真实的透明材质一样，反射和高光将清晰可见。
* **渐变** — 允许物体逐渐消失，直至完全头透明，包括镜面高光和光照反射。如果想创建一个让物体渐显或渐隐的动画，则该模式非常有用。该模式不适合渲染真实的透明材质，例如透明塑料或玻璃，因为光照反射和高光也会逐渐隐藏。

![The helmet visor in this image is rendered using the Transparent mode, because it is supposed to represent a real physical object that has transparent properties. Here the visor is reflecting the skybox in the scene. ](http://docs.unity3d.com/uploads/Main/StandardShaderTransparencySkyBoxReflection.png)
<!-- > The helmet visor in this image is rendered using the Transparent mode, because it is supposed to represent a real physical object that has transparent properties. Here the visor is reflecting the skybox in the scene. -->
> 上图中的头盔面罩（密封偷窥观察窗）使用透明模式渲染，因为它可以表示具有透明度属性的真实物理对象。这里的面罩反射了场景中的天空盒。

![These windows use Transparent mode, but have some fully opaque areas defined in the texture (the window frames). The Specular reflection from the light sources reflects off the transparent areas and the opaque areas.](http://docs.unity3d.com/uploads/Main/StandardShaderTransparentWindow.png)
<!-- > These windows use Transparent mode, but have some fully opaque areas defined in the texture (the window frames). The Specular reflection from the light sources reflects off the transparent areas and the opaque areas. -->
> 这些窗户使用了透明模型，但是在纹理中定义一些不透明区域（窗框）。透明区域和不透明区域以镜面的方式反射来自光源的光照。

![The hologram in this image is rendered using the Fade mode, because it is supposed to represent an opaque object that is partially faded out.](http://docs.unity3d.com/uploads/Main/StandardShaderFadeHologram.png)
<!-- > The hologram in this image is rendered using the Fade mode, because it is supposed to represent an opaque object that is partially faded out. -->
> 图中的全息图使用渐变模式渲染，因为它可以表示部分渐隐的不透明对象。

![The grass in this image is rendered using the Cutout mode. This gives clear sharp edges to objects which is defined by specifying a cut-off threshold. All parts of the image with the alpha value above this threshold are 100% opaque, and all parts below the threshold are invisible. To the right in the image you can see the material settings and the alpha channel of the texture used.](http://docs.unity3d.com/uploads/Main/StandardShaderCutoutGrassExample.png)
<!-- > The grass in this image is rendered using the Cutout mode. This gives clear sharp edges to objects which is defined by specifying a cut-off threshold. All parts of the image with the alpha value above this threshold are 100% opaque, and all parts below the threshold are invisible. To the right in the image you can see the material settings and the alpha channel of the texture used. -->
> 图中的草使用镂空模式渲染。通过定义镂空阀值可以显示清晰的锐利边缘。在图像中，alpha 高于该阀值的部分是 100% 不透明的，低于阀值的所有部分是不可见的。在图像的右侧，你可以到材质的设置，和所使用纹理的 alpha 通道。
