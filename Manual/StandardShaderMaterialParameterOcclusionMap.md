<!-- > [Occlusion Map](http://docs.unity3d.com/Manual/StandardShaderMaterialParameterOcclusionMap.html) -->

<!-- # Occlusion Map -->
# 散射贴图

![](http://docs.unity3d.com/uploads/Main/StandardShaderParameterOcclusion.png)

<!-- The occlusion map is used to provide information about which areas of the model should receive high or low indirect lighting. Indirect lighting comes from ambient lighting and reflections, and so steep concave parts of your model such as a crack or fold would not realistically receive much indirect light. -->
散射贴图用于提供模型某些区域应该接收的非直接光照的数量信息。非直接光照来自环境光和反射光，因此，模型的高陡度凹陷部分，例如裂缝或褶皱，不会接收太多的非直接光照。

<!-- Occlusion texture maps are normally calculated by 3D applications directly from the 3D model using the modeller or third party software. -->
散射纹理贴图通常由 3D 应用程序计算，由建模器或第三方软件从 3D 模型中直接导出。

<!-- An occlusion map is a greyscale image, with white indicating areas that should receive full indirect lighting, and black indicating no indirect lighting. Sometimes this is as simple as a greyscale heightmap, for simple surfaces (such as the knobbly stone wall texture shown in the heightmap example above). -->
散射贴图是一张灰阶图，其中白色表示应该完全接受非直接光照，黑色表示没有非直接光照。
对于简单表面，它像灰阶高度图一样简单（例如前面高度图示例中的不规则石墙纹理）。

<!-- At other times, generating the correct occlusion texture is slightly more complex. For example, if a character in your scene is wearing a hood, the inside edges of the hood should be set to very low indirect lighting, or none at all. In these situations, occlusion maps will be often be produced by artists, using 3D applications to automatically generate an occlusion map based on the model. -->
在其他时候，要生成正确的散射贴图稍微有些复杂。例如，场景中的角色戴了头罩，头罩内边缘的非直接光照应该设置的非常低，甚至完全没有。在这些情况下，散射贴图经常由设计师使用 3D 应用程序基于模型自动生成。

![This occlusion map identifies areas on a characters sleeve that are exposed or hidden from ambient lighting. It is used on the model pictured below.](http://docs.unity3d.com/uploads/Main/StandardShaderOcclusionMapTexture.png)
<!-- > This occlusion map identifies areas on a character’s sleeve that are exposed or hidden from ambient lighting. It is used on the model pictured below. -->
> 散射贴图标识了在环境光照下角色头罩下暴露或隐藏的区域。它用于下面所示的模型。

![Before and after applying an occlusion map. The areas that are partially obscured, particularly in the folds of fabric around the neck, are lit too brightly on the left. After the ambient occlusion map is assigned, these areas are no longer lit by the green ambient light from the surrounding wooded environment.](http://docs.unity3d.com/uploads/Main/StandardShaderOcclusionMap.png)
<!-- > Before and after applying an occlusion map. The areas that are partially obscured, particularly in the folds of fabric around the neck, are lit too brightly on the left. After the ambient occlusion map is assigned, these areas are no longer lit by the green ambient light from the surrounding wooded environment. -->
> 散射贴图应用前和应用后。在左图中，部分被遮挡的区域，特别是围绕颈部的衣服褶皱，被照的太亮了。指定散射贴图后，这些区域不再被来周围森林的绿色环境光所照亮。
