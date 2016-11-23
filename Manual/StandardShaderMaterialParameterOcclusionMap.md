> [Occlusion Map](http://docs.unity3d.com/Manual/StandardShaderMaterialParameterOcclusionMap.html)

Occlusion Map

![](http://docs.unity3d.com/uploads/Main/StandardShaderParameterOcclusion.png)

The occlusion map is used to provide information about which areas of the model should receive high or low indirect lighting. Indirect lighting comes from ambient lighting and reflections, and so steep concave parts of your model such as a crack or fold would not realistically receive much indirect light.

Occlusion texture maps are normally calculated by 3D applications directly from the 3D model using the modeller or third party software.

An occlusion map is a greyscale image, with white indicating areas that should receive full indirect lighting, and black indicating no indirect lighting. Sometimes this is as simple as a greyscale heightmap, for simple surfaces (such as the knobbly stone wall texture shown in the heightmap example above).

At other times, generating the correct occlusion texture is slightly more complex. For example, if a character in your scene is wearing a hood, the inside edges of the hood should be set to very low indirect lighting, or none at all. In these situations, occlusion maps will be often be produced by artists, using 3D applications to automatically generate an occlusion map based on the model.

![This occlusion map identifies areas on a characters sleeve that are exposed or hidden from ambient lighting. It is used on the model pictured below.](http://docs.unity3d.com/uploads/Main/StandardShaderOcclusionMapTexture.png)
> This occlusion map identifies areas on a character’s sleeve that are exposed or hidden from ambient lighting. It is used on the model pictured below.

![Before and after applying an occlusion map. The areas that are partially obscured, particularly in the folds of fabric around the neck, are lit too brightly on the left. After the ambient occlusion map is assigned, these areas are no longer lit by the green ambient light from the surrounding wooded environment.](http://docs.unity3d.com/uploads/Main/StandardShaderOcclusionMap.png)
> Before and after applying an occlusion map. The areas that are partially obscured, particularly in the folds of fabric around the neck, are lit too brightly on the left. After the ambient occlusion map is assigned, these areas are no longer lit by the green ambient light from the surrounding wooded environment.