<!-- > [Smoothness](http://docs.unity3d.com/Manual/StandardShaderMaterialParameterSmoothness.html) -->

<!-- Unity Manual > Graphics > Graphics Overview > Materials, Shaders & Textures > Standard Shader > Material parameters > Smoothness -->

<!-- Unity 手册 > 图形 > 图形预览 > 材质、着色器、纹理 > 标准着色器 > 材质参数 > 平滑度 -->

<!-- # Smoothness -->
# 平滑度

![The smoothness parameter, shown in both Metallic & Specular shader modes.](http://docs.unity3d.com/uploads/Main/StandardShaderParameterSmoothness.png)
<!-- > The smoothness parameter, shown in both Metallic & Specular shader modes. -->
> 平滑度参数，同时存在于标准着色器的金属模式和镜面模式中。

<!-- The concept of Smoothness applies to both the Specular workflow and the Metallic workflow, and works in very much the same way in both. By default, without a [Metallic](http://docs.unity3d.com/Manual/StandardShaderMaterialParameterMetallic.html) or [Specular](http://docs.unity3d.com/Manual/StandardShaderMaterialParameterSpecular.html) texture map assigned, the smoothness of the material is controlled by a slider. This slider allows you to control the “microsurface detail” or smoothness across a surface. -->
平滑度概念同时支持镜面模式和金属模式，并且工作方式也一样。默认情况下，没有指定金属或镜面纹理贴图，材质的平滑度通过一个滑动器控制。这个滑动器允许你控制『表面微观节』或整个表面的平滑度。

<!-- Both shader modes are shown above, because if you choose to use a texture map for the **Metallic** or **Specular** parameter, the smoothness values are taken from that same map. This is explained in further detail down the page. -->
不管是哪种着色器模式，如果为**金属属性**或**镜子属性**使用了纹理题图，平滑度的值将从该贴图中读取。更多细节会在本页的后面介绍。

![A range of smoothness values from 0 to 1](http://docs.unity3d.com/uploads/Main/StandardShaderSmoothnessGraduationTable.svg)
<!-- > A range of smoothness values from 0 to 1 -->
> 平滑度的值范围为从 0 到 1。

<!-- The “microsurface detail” is not something directly visible in Unity. It is a concept used in the lighting calculations. You can, however, see the effect of this microsurface detail represented by the amount the light that is diffused as it bounces off the object. With a smooth surface, all light rays tend to bounce off at predictable and consistent angles. Taken to its extreme, a perfectly smooth surface reflects light like a mirror. Less smooth surfaces reflect light over a wider range of angles (as the light hits the bumps in the microsurface), and therefore the reflections have less detail and are spread across the surface in a more diffuse way. -->
在 Unity 中，『表面微观细节』不是直接可见的东西。它是一个光照计算中使用的概念。尽管如此，当光从物体表面反射时，通过衡量其中漫反射光的数量，可以看到表面微观细节的效果。在光滑的表面上，所有光以可预测和一致的角度反射。极端情况下，一个绝对光滑的表面像镜子一样反射光。不太光滑的表面以更大的角度范围反射光（就像光撞击到微小的凸起），因此，反射光含有的信息更少，并且，以松散的方式散布在整个表面。

> 译注：漫反射，是投射在粗糙表面上的光向各个方向反射的现象。当一束平行的入射光线射到粗糙的表面时，表面会把光线向着四面八方反射，所以入射线虽然互相平行，由于各点的法线方向不一致，造成反射光线向不同的方向无规则地反射，这种反射称之为“漫反射”或“漫射”。这种反射的光称为漫射光。很多物体，如植物、墙壁、衣服等，其表面粗看起来似乎是平滑，但用放大镜仔细观察，就会看到其表面是凹凸不平的，所以本来是平行的太阳光被这些表面反射后，弥漫地射向不同方向。—来自百度百科

![A comparison of low, medium and high values for smoothness (left to right), as a diagram of the theoretical microsurface detail of a material. The yellow lines represent light rays hitting the surface and reflecting off the angles encountered at varying levels of smoothness.](http://docs.unity3d.com/uploads/Main/StandardShaderMicrosurfaceDiagram.svg)
<!-- > A comparison of low, medium and high values for smoothness (left to right), as a diagram of the theoretical microsurface detail of a material. The yellow lines represent light rays hitting the surface and reflecting off the angles encountered at varying levels of smoothness. -->
> 材质表面微观细节在低、中、高平滑度下的理论对比图（从左到右）。黄色线条表示在不同光滑度下，光线撞击表面和反射的角度。

<!-- A smooth surface has very low microsurface detail, or none at all, so light bounces off in uniform ways, creating clear reflections. A rough surface has high peaks and troughs in its microsurface detail, so light bounces off in a wide range of angles which, when averaged out, create a diffuse colour with no clear reflections. -->
光滑的表面具有非常低的表面微观细节，甚至更本没有，因此光以均匀的方式反弹，产生清晰的反射。粗糙的表面在微观程度上具有高峰和低谷，因此光在宽范围角度内反弹，平均下来，产生不清晰的漫反射颜色。

![A comparison of low, medium and high values for smoothness (top to bottom).](http://docs.unity3d.com/uploads/Main/StandardShaderEnergyConservation.png)
<!-- > A comparison of low, medium and high values for smoothness (top to bottom). -->
> 低、中、高平滑度的对比（从上往下）。

<!-- At low smoothness levels, the reflected light at each point on the surface comes from a wide area, because the microsurface detail is bumpy and scatters light. At high values of smoothness, the light at each point comes from a narrowly focused area, giving a much clearer reflection of the object’s environment. -->
低平滑度时，物体表面每个点的反射光位于广泛的区域中，因为微观细节崎岖不平，光被分散开。高平滑度时，每个点的反射光位于狭窄聚焦的区域，对物体环境的反射更加清晰。

<!-- ## Using a Smoothness Texture Map -->
## 使用平滑度纹理贴图

<!-- In a similar way to many of the other parameters, you can assign a texture map instead of using a single slider value. This allows you greater control over the strength and colour of the specular light reflections across the surface of the material. -->
与许多其他参数一样，你可以设置一张纹理贴图，来代替滑动器的值。这样可以更好地控制物体表面反射光的强度和颜色。

<!-- Using a map instead of a slider means you can create materials which include a variety of smoothness levels across the surface (usually designed to match what is shown in the albedo texture). -->
使用贴图代替滑动器，意味着你可以创建包含各种平滑度表面的材质（通常被设计为与漫反射纹理相同）。

<!-- 
> Property:   Function:

* **Smoothness source**   Select the texture channel where the smoothness value is stored.
    * **Specular/Metallic Alpha** Because the smoothness of each point on the surface is a single value, only a single channel of an image texture is required for the data. Therefore the smoothness data is assumed to be stored in the Alpha Channel of the same image texture used for the Metallic or Specular texture map (depending which of these two modes you are using).
    * **Albedo Alpha**    This lets you reduce the total number of textures, or use textures of different resolutions for Smoothness and Specular/Metallic.
* **Highlights**  Check this box to disable highlights. This is an optional performance optimization for mobile. It removes the calculation of highlights from the Standard Shader. How this affects the appearance mainly depends on the Specular/Metallic value and the Smoothness.
* **Reflections** Check this box to disable environment reflections. This is an optional performance optimization for mobile. It removes the calculation of highlights from the Standard Shader. Instead of sampling the environment map, an approximation is used. How this affects the appearance depends on the smoothness.
 -->

### 属性和功能

* **平滑度来源** 选择存储平滑度值的纹理通道。
    - **镜面/金属的 Alpha 通道** 因为物体表面每个点的平滑度只需要一个值，所以只需要图像纹理的一个通道。因此，平滑度数据被预设存储在金属或镜面纹理贴图的 Alpha 通道中（取决于在这两种模式中你使用的是哪一种）。
    - **漫反射的 Alpha 通道** 使用这个通道，可以减少纹理的总数，或者为镜面/金属的平滑度采用不同分辨率的纹理。
* **高光** 选中此框可以禁用高光。这是针对移动设备的性能优化。它从标准着色器中移除高光计算。禁用后对外边的影响主要取决于镜面/金属和平滑度的值。
* **反射** 选中此框可以禁用环境反射。这是针对移动设备的性能优化。它从标准着色器中移除高光计算。采用近似计算的方式，代替环境贴图采样。禁用后对外观的影响取决于平滑度。

<!-- Smoother surfaces are more reflective and have smaller, more tightly-focused specular highlights. Less smooth surfaces do not reflect as much, so specular highlights are less noticable and spread wider across the surface. By matching the specular and smoothness maps to the content in your albedo map, you can begin to create very realistic-looking textures. -->
更平滑的表面更具反射性（反射率更高），具有更小、更聚焦的镜面高光。不太平滑的表面不能反射太多光照，所以镜面高光不太明显，并广泛地扩展在整个表面。调整反射率和平滑度贴图，使之与漫反射贴图相匹配，你就可以开始创建爱你非常逼真的问题。
