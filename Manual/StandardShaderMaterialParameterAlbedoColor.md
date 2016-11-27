<!-- > [Albedo Color and Transparency](http://docs.unity3d.com/Manual/StandardShaderMaterialParameterAlbedoColor.html) -->

<!-- Unity Manual > Graphics > Graphics Overview > Materials, Shaders & Textures > Standard Shader > Material parameters > Albedo Color and Transparency -->

<!-- # Albedo Color and Transparency -->
# 漫反射颜色和透明度

![A Standard Shader material with default parameters and no values or textures assigned. The Albedo Color parameter is highlighted.](http://docs.unity3d.com/uploads/Main/StandardShaderParameterAlbedoColor.png)
<!-- > A Standard Shader material with default parameters and no values or textures assigned. The Albedo Color parameter is highlighted. -->
> 一个具有默认参数并且未分配值和纹理的标准着色器材质。参数『漫反射颜色』被突出显示。

<!-- The Albedo parameter controls the base color of the surface. -->
漫反射参数控制表面的基准颜色（底色）。

![A range of black to white albedo values](http://docs.unity3d.com/uploads/Main/StandardShaderAlbedoGraduationTable.svg)
<!-- > A range of black to white albedo values -->
> 漫反射颜色从黑到白。
> 译注：Brushed Metal 拉丝金属，Brick 砖块，Rock 岩石，Satin 绸缎，Ceramic 陶瓷。

<!-- Specifying a single color for the Albedo value is sometimes useful, but it is far more common to assign a texture map for the Albedo parameter. This should represent the colors of the surface of the object. It’s important to note that the Albedo texture should not contain any lighting, since the lighting will be added to it based on the context in which the object is seen. -->
有些情况下，为漫反射指定一个颜色值是有用的，但是，更常见的情况是，为漫反射参数指定一张纹理贴图。漫反射应该表示物体表面的颜色。需要特别注意的是，漫反射纹理不应该包含任何光照信息，因为将基于上下文（环境）添加光照到物体的纹理上。

![Two examples of typical Albedo texture maps. On the left is a texture map for a character model, and on the right is a wooden crate. Notice there are no shadows or lighting highlights.](http://docs.unity3d.com/uploads/Main/StandardShaderAlbedoTextureExamples.png)
<!-- > Two examples of typical Albedo texture maps. On the left is a texture map for a character model, and on the right is a wooden crate. Notice there are no shadows or lighting highlights. -->
> 两个典型的漫反射问题贴图示例。左边是一个角色的纹理贴图，右边是一个木板箱的纹理贴图。注意，两者都不包含阴影和光照高光（镜面高光、光斑）。

<!-- ## Transparency -->
## 透明度

<!-- The alpha value of the Albedo colour controls the transparency level for the material. This only has an effect if the Rendering Mode for the material is set to one of the transparent mode, and not Opaque. As mentioned above, picking the correct transparency mode is important because it determines whether or not you will still see reflections and specular highlights at full value, or whether they will be faded out according to the transparency values too. -->
漫反射颜色的 alpha 值控制材质的透明程度。只有在材质的渲染模型被设置为透明模式之一（除了不透明模式意外的镂空、透明或渐变模式）时才会有效果。如上所述，选择正确的透明模式非常重要，因为它决定了是否可以完整地看到反射光照和镜面高光，以及是否可以随照透明度逐渐淡出。


![A range of transparency values from 0 to 1, using the Transparent mode suitable for realistic transparent objects](http://docs.unity3d.com/uploads/Main/StandardShaderTransparencyGraduationTable.png)
<!-- > A range of transparency values from 0 to 1, using the Transparent mode suitable for realistic transparent objects -->
> 透明度的值从 0 到 1，使用透明模式，以适配真实的透明物体。

<!-- When using a texture assigned for the Albedo parameter, you can control the transparency of the material by ensuring your albedo texture image has an **alpha channel**. The alpha channel values are mapped to the transparency levels with white being fully opaque, and black being fully transparent. This will have the effect that your material can have areas of varying transparency. -->
当使用分配给漫反射参数的纹理时，如果漫反射纹理贴图含有 **alpha 通道**，那么你可以控制材质的透明度。alpha 通道的值被映射为透明度，白色映射为完全不够名，黑色映射为完全透明。这将导致材质可能具有不同透明度的区域。

![An imported texture with RGB channels and an Alpha Channel. You can click the RGB/A button as shown to toggle which channels of the image you are previewing.](http://docs.unity3d.com/uploads/Main/StandardShaderTransparencyMapRGBAlphaToggle.png)
<!-- > An imported texture with RGB channels and an Alpha Channel. You can click the RGB/A button as shown to toggle which channels of the image you are previewing. -->
> 一个被导入纹理，带有 RGB 通道和 Alpha 通道。你可以点击 RGB/A 按钮，来切换预览图的通道。

![The end result, peering through a broken window into a building. The gaps in the glass are totally transparent, while the glass shards are partially transparent and the frame is fully opaque.](http://docs.unity3d.com/uploads/Main/StandardShaderTransparencyMapBrokenWindow.png)
<!-- > The end result, peering through a broken window into a building. The gaps in the glass are totally transparent, while the glass shards are partially transparent and the frame is fully opaque. -->
> 最终效果图，光线穿过破窗户进入建筑物。玻璃中间的分析是完全透明的，而玻璃随便是部分透明，窗框则完全不透明。
