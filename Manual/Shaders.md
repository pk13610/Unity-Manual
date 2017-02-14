<!-- > [Materials, Shaders & Textures](http://docs.unity3d.com/Manual/Shaders.html) -->

<!-- Unity Manual > Graphics > Graphics Overview > Materials, Shaders & Textures -->

<!-- # Materials, Shaders & Textures -->
# 材质、着色器、纹理

<!-- Rendering in Unity is done with **Materials**, **Shaders** and **Textures**. -->
在 Unity 中，渲染通过 **材质**、**着色器** 和 **纹理** 完成。

<!-- There is a close relationship between Materials, Shaders and Textures in Unity. -->
在 Unity 中，材质、着色器和纹理之间的关系非常紧密。

<!-- **Materials** are definitions of how a surface should be rendered, including references to textures used, tiling information, colour tints and more. The available options for a material depend on which shader the material is using. -->

**材质** 定义了应该如何渲染表面，包含了对贴图的引用、拼接信息、颜色等等。材质的有效选项取决于所使用的的着色器。

<!-- **Shaders** are small scripts that contain the mathematical calculations and algorithms for calculating the colour of each pixel rendered, based on the lighting input and the Material configuration. -->

**着色器** 是一些小脚本，包含了计算每个像素渲染颜色的数学计算和算法，基于光照输入和材质配置。

<!-- **Textures** are bitmap images. A Material may contain references to textures, so that the Material’s shader can use the textures while calculating the surface colour of an object. In addition to basic colour (albedo) of an obejct’s surface, textures can represent many other aspects of a material’s surface such as its reflectivity or roughness. -->

**纹理** 是一些位图图像。一个材质可以包含对多个纹理的引用，材质的着色器在计算物体表面颜色时可以使用这些纹理。相对于物体表面的基础颜色（漫反射），纹理可以表示更多的材质表面细节，例如反射率或粗糙度。

<!-- A material specifies one specific shader to use, and the shader used determines which options are available in the material. A shader specifies one or more textures variables that it expects to use, and the Material Inspector in Unity allows you to assign your own texture assets to these these texture variables. -->

一个材质只能使用一个着色器，这个着色器决定了材质中的哪些选项是有效的。一个着色器指定一个或多个希望使用的纹理变量，在材质的检视视图中，你可以为这些纹理变量指定纹理资源。

<!-- For most normal rendering - by which we mean characters, scenery, environments, solid and transparent objects, hard and soft surfaces etc., the [Standard Shader](http://docs.unity3d.com/Manual/shader-StandardShader.html) is usually the best choice. This is a highly customisable shader which is capable of rendering many types of surface in a highly realistic way. -->

对于大多数渲染 —— 角色、场景、环境、固体、透明物体、坚硬外表、柔软外表等，[标准着色器](http://docs.unity3d.com/Manual/shader-StandardShader.html) 往往是最佳选择。这是一种可高度定制的着色器，可以非常逼真地渲染很多种外表类型。

<!-- There are other situations where a different built-in shader, or even a custom written shader might be appropriate - such as liquids, foliage, refractive glass, particle effects, cartoony, illustrative or other artistic effects, or other special effects like night vision, heat vision or x-ray vision, etc. -->

而在某些情况下，使用其他内置着色器，甚至是自定义着色器，可能更加合适 —— 例如，液体、植物、玻璃折射、粒子效果、卡通化或者其他艺术效果，或者其他特技效果，例如，夜视仪、热成像仪或 X 光透视。

<!-- The following pages describe: -->
下面这些页面介绍了：

<!-- 
* [Creating and Using Materials.](http://docs.unity3d.com/Manual/Materials.html)
* [The Built-in Standard Shader.](http://docs.unity3d.com/Manual/shader-StandardShader.html)
* [Other built-in Shaders.](http://docs.unity3d.com/Manual/Built-inShaderGuide.html)
* [Writing Your Own Shaders.](http://docs.unity3d.com/Manual/ShadersOverview.html)
 -->
* [创建和使用材质](http://docs.unity3d.com/Manual/Materials.html)
* [内置标准着色器](http://docs.unity3d.com/Manual/shader-StandardShader.html)
* [其他内置着色器](http://docs.unity3d.com/Manual/Built-inShaderGuide.html)
* [编写着色器](http://docs.unity3d.com/Manual/ShadersOverview.html)
