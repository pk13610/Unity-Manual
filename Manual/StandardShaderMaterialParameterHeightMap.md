<!-- > [Heightmap](http://docs.unity3d.com/Manual/StandardShaderMaterialParameterHeightMap.html) -->

<!-- Unity Manual > Graphics > Graphics Overview > Materials, Shaders & Textures > Standard Shader > Material parameters > Heightmap -->

<!-- # Heightmap -->
# 高度图

![](http://docs.unity3d.com/uploads/Main/StandardShaderParameterHeightmap.png)

<!-- Height mapping (also known as parallax mapping) is a similar concept to normal mapping, however this technique is more complex - and therefore also more performance-expensive. Heightmaps are usually used in conjunction with normalmaps, and often they are used to give extra definition to surfaces where the texture maps are responsible for rendering large bumps and protrusions. -->
高度图（也称为视差贴图）是一个类似于法线贴图的概念，但是技术更复杂 — 因此更性能开销更大。高度图通常与法线贴图结合使用，负责定义和渲染表面额外的大型凸起。

<!-- While normal mapping modifies the lighting across the surface of the texture, parallax height mapping goes a step further and actually shifts the areas of the visible surface texture around, to achieve a kind of surface-level occlusion effect. This means that apparent bumps will have their near side (facing the camera) expanded and exaggerated, and their far side (facing away from the camera) will be reduced and seem to be occluded from view. -->
虽然法线贴图改变了纹理表面的光照，但是视差高度图更进一步，它会移动表面纹理的可见区域，从而实现表面遮挡效果。这意味着，明显的凸起将具有放大的正面（面向相机）和缩小的反面（背向相机），并且反面会被遮挡住。

<!-- This effect, while it can produce a very convincing representation of 3D geometry, is still limited to the surface of the flat polygons of an object’s mesh. This means that while surface bumps will appear to protrude and occlude each other, the “silhouette” of the model will never be modified, because ultimately the effect is drawn onto the surface of the model and does not modify the actual geometry. -->
虽然可以产生非常逼真的 3D 几何效果，但是仅限于物体网格的平面多边形表面。这意味着，表面凸起将会突出现实并且彼此遮挡，但是并不会改变模型的『轮廓』，因为最终效果是绘制在模型表面，并不会实际的几何形状。

A heightmap should be a greyscale image, with white areas representing the high areas of your texture and black representing the low areas. Here’s a typical albedo map and a heightmap to match.
一张高度图应该是一张灰阶图，白色区域表示纹理的高区域，黑色区域代表低区域。下面是一张典型的漫反射贴图和对应的高度图。

![An albedo colour map, and a heightmap to match.](http://docs.unity3d.com/uploads/Main/StandardShaderHeightmapTexture.png)
<!-- > An albedo colour map, and a heightmap to match. -->
> 一张漫反射颜色贴图，和一张对应的高度图。

![](http://docs.unity3d.com/uploads/Main/StandardShaderParallaxMap.jpg)

<!-- From left to right in the above image: 1. A rocky wall material with albedo assigned, but no normalmap or heightmap. 2. The normal assigned. Lighting is modified on the surface, but rocks do not occlude each other. 3. The final effect with normalmap and heightmap assigned. The rocks appear to protrude out from the surface, and nearer rocks seem to occlude rocks behind them. -->
上图从左往右：1. 石墙材质被指定了漫反射贴图，但是没有法线贴图和高度图。2. 指定了法线贴图。表面光照被改变，但是岩石避免没有遮挡。3. 设置了法线贴图和高度图的最终效果。岩石看起来从表面凸起，近处岩石看起来遮挡了它们后面的岩石。

<!-- Often (but not always) the greyscale image used for a heightmap is also a good image to use for the occlusion map. For information on occlusion maps, see the next section. -->
用于高度图的灰阶图，通常（但不总是）也可以很好地用于散射贴图。关于散射贴图请参阅下一节。
