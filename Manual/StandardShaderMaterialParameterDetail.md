> [StandardShaderMaterialParameterDetail](http://docs.unity3d.com/Manual/StandardShaderMaterialParameterDetail.html)

Unity Manual > Graphics > Graphics Overview > Materials, Shaders & Textures > Standard Shader > Material parameters > Secondary Maps (Detail Maps) & Detail Mask

# Secondary Maps (Detail Maps) & Detail Mask

Secondary Maps (or Detail maps) allow you to overlay a second set of textures on top of the main textures listed above. You can apply a second Albedo colour map, and a second Normal map. Typically, these would be mapped on a much smaller scale repeated many times across the object’s surface, compared with the main Albedo and Detail maps.

The reason for this is to allow the material to have sharp detail when viewed up close, while also having a normal level of detail when viewed from further away, without having to use a single extremely high texture map to achieve both goals.

Typical uses for detail textures would be: - Adding skin detail, such as pores and hairs, to a character’s skin - Adding tiny cracks and lichen growth to a brick wall - adding small scratches and scuffs to a large metal container

![This character has a skin texture map, but no detail texture yet. We will add skin pores as a detail texture.](http://docs.unity3d.com/uploads/Main/StandardShaderDetailNotAppliedYet.png)
> This character has a skin texture map, but no detail texture yet. We will add skin pores as a detail texture.

![The Albedo skin pore detail texture](http://docs.unity3d.com/uploads/Main/StandardShaderDetailSkin.png)
> The Albedo skin pore detail texture

![The normal map for the skin pore detail](http://docs.unity3d.com/uploads/Main/StandardShaderDetailSkinNormal.png)
> The normal map for the skin pore detail

![The end result, the character now has subtle skin pore detail across her skin, at a much higher resolution than the base Albedo or Normal map layer would have allowed.](http://docs.unity3d.com/uploads/Main/StandardShaderDetailApplied.png)
> The end result, the character now has subtle skin pore detail across her skin, at a much higher resolution than the base Albedo or Normal map layer would have allowed.

![Detail textures can have a subtle but striking effect on the way light hits a surface. This is the same character in a different lighting context.](http://docs.unity3d.com/uploads/Main/StandardShaderDetailDifferentContext.png)
> Detail textures can have a subtle but striking effect on the way light hits a surface. This is the same character in a different lighting context.

If you use a single normal map do ALWAYS plug it into the primary channel. The Secondary normal map channel is more expensive than the primary one but has the exact same effect.

### Detail Mask

The detail mask texture allows you to mask off certain areas of your model to have the detail texture applied. This means you can show the detail texture in certain areas, and hide it in others. In the example of the skin pores above, you might want to create a mask so the pores are not shown on the lips or eyebrows.