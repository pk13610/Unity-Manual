<!-- > [StandardShaderMaterialParameterDetail](http://docs.unity3d.com/Manual/StandardShaderMaterialParameterDetail.html) -->

<!-- Unity Manual > Graphics > Graphics Overview > Materials, Shaders & Textures > Standard Shader > Material parameters > Secondary Maps (Detail Maps) & Detail Mask -->

<!-- # Secondary Maps (Detail Maps) & Detail Mask -->
# 辅助贴图（细节贴图）和细节蒙板

<!-- Secondary Maps (or Detail maps) allow you to overlay a second set of textures on top of the main textures listed above. You can apply a second Albedo colour map, and a second Normal map. Typically, these would be mapped on a much smaller scale repeated many times across the object’s surface, compared with the main Albedo and Detail maps. -->
辅助贴图（或细节贴图）允许你在主纹理上叠加第二层纹理。你可以应用一张辅助漫反射贴图和辅助法线贴图。相对于主纹理，辅助贴图通常以非常小的尺寸在物体表面上重复多次。

<!-- The reason for this is to allow the material to have sharp detail when viewed up close, while also having a normal level of detail when viewed from further away, without having to use a single extremely high texture map to achieve both goals. -->
设计辅助贴图的目的，是为了使材质在近距离观察时具有清晰的细节，在远距离观察时具有正常的细节，而不是必须使用一张极大的纹理来实现这两个目标。

<!-- Typical uses for detail textures would be: - Adding skin detail, such as pores and hairs, to a character’s skin - Adding tiny cracks and lichen growth to a brick wall - adding small scratches and scuffs to a large metal container -->
细节纹理的典型用途有：为角色的皮肤添加细节，例如毛孔和毛发；在砖墙上添加裂缝和地衣；为大型金属集装箱添加小划痕和磨损。

![This character has a skin texture map, but no detail texture yet. We will add skin pores as a detail texture.](http://docs.unity3d.com/uploads/Main/StandardShaderDetailNotAppliedYet.png)
<!-- > This character has a skin texture map, but no detail texture yet. We will add skin pores as a detail texture. -->
> 这个角色具有一张皮肤纹理贴图，但是没有细节纹理。我们将使用细节纹理增加皮肤毛孔。


![The Albedo skin pore detail texture](http://docs.unity3d.com/uploads/Main/StandardShaderDetailSkin.png)
<!-- > The Albedo skin pore detail texture -->
> 漫反射皮肤毛孔细节纹理。


![The normal map for the skin pore detail](http://docs.unity3d.com/uploads/Main/StandardShaderDetailSkinNormal.png)
<!-- > The normal map for the skin pore detail -->
> 皮肤毛孔细节的法线贴图。

![The end result, the character now has subtle skin pore detail across her skin, at a much higher resolution than the base Albedo or Normal map layer would have allowed.](http://docs.unity3d.com/uploads/Main/StandardShaderDetailApplied.png)
<!-- > The end result, the character now has subtle skin pore detail across her skin, at a much higher resolution than the base Albedo or Normal map layer would have allowed. -->
> 最终效果，现在角色的皮肤上有细微的毛孔细节，分辨率比基础漫反射贴图或基础法线贴图层要高得多。


![Detail textures can have a subtle but striking effect on the way light hits a surface. This is the same character in a different lighting context.](http://docs.unity3d.com/uploads/Main/StandardShaderDetailDifferentContext.png)
<!-- > Detail textures can have a subtle but striking effect on the way light hits a surface. This is the same character in a different lighting context. -->
> 细节纹理可以为光照撞击表面的方式提供微妙而生动的效果。这是处于不同光照环境中的同一个角色。

<!-- If you use a single normal map do ALWAYS plug it into the primary channel. The Secondary normal map channel is more expensive than the primary one but has the exact same effect. -->
如果你只使用单个法线贴图，请务必把他插入主通道。因为，辅助法线贴图的性能开销比主法线贴图更高，但是效果相同。

<!-- ### Detail Mask -->
### 细节蒙板

<!-- The detail mask texture allows you to mask off certain areas of your model to have the detail texture applied. This means you can show the detail texture in certain areas, and hide it in others. In the example of the skin pores above, you might want to create a mask so the pores are not shown on the lips or eyebrows. -->
细节蒙板纹理允许对具有细节纹理的模型，遮盖某些特定区域。这意味着，你可以在特定区域显示细节问题，在其他区域隐藏细节纹理。在上面皮肤毛孔的例子中，你可能需要创建一个蒙板，以使毛孔不会出现在嘴唇和眉毛上。
