> ! [Accessing and Modifying Material parameters via script](http://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html)

Unity Manual > Graphics > Graphics Overview > Materials, Shaders & Textures > Accessing and Modifying Material parameters via script

# Accessing and Modifying Material parameters via script

All the parameters of a Material that you see in the inspector when viewing a material are accessible via script, giving you the power to change or animate how a material works at runtime.

This allows you to modify numeric values on the Material, change colours, and swap textures dynamically during gameplay. Some of the most commonly used functions to do this are:

> Function Name   Use

[SetColor](http://docs.unity3d.com/ScriptReference/Material.SetColor.html)    Change the color of a material (Eg. the albedo tint color)

[SetFloat](http://docs.unity3d.com/ScriptReference/Material.SetFloat.html)    Set a floating point value (Eg. the normal map multiplier)

[SetInt](http://docs.unity3d.com/ScriptReference/Material.SetInt.html)  Set an integer value in the material

[SetTexture](http://docs.unity3d.com/ScriptReference/Material.SetTexture.html)  Assign a new texture to the material

The full set of functions available for manipulating materials via script can be found on the [Material class scripting reference](http://docs.unity3d.com/ScriptReference/Material.html).

One important note is that these functions **only set properties that are available for the current shader** on the material. This means that if you have a shader that doesn’t use any textures, or if you have no shader bound at all, calling [SetTexture](http://docs.unity3d.com/ScriptReference/Material.SetTexture.html) will have no effect. This is true even if you later set a shader that needs the texture. For this reason it is recommended to set the shader you want before setting any properties, however once you’ve done that you can switch from one shader to another that use the same textures or properties and values will be preserved.

These functions work as you would expect for all _simple_ shaders such as the legacy shaders, and the built-in shaders _other than the Standard Shader_ (for example, the particle, sprite, UI and unlit shaders). For a material using the _Standard Shader_ however, there are some further requirements which you must be aware of before being able to fully modify the Material.

## Special requirements for Scripting with the Standard Shader

The Standard Shader has some extra requirements if you want to modify Materials at runtime, because - behind the scenes - it is actually many different shaders rolled into one.

These different types of shader are called [Shader Variants](http://docs.unity3d.com/Manual/SL-MultipleProgramVariants.html) and can be thought of as all the different possible combinations of the shader’s features, when activated or not activated.

For example, if you choose to assign a [Normal Map](http://docs.unity3d.com/Manual/StandardShaderMaterialParameterNormalMap.html) to your material, you activate that _variant_ of the shader which supports Normal Mapping. If you subsequently also assign a [Height Map](http://docs.unity3d.com/Manual/StandardShaderMaterialParameterHeightMap.html) then you activate the variant of the shader which supports Normal Mapping and Height Mapping.

This is a good system, because it means that if you use the Standard Shader, but do not use a Normal Map in a certain Material, you are not incurring the performance cost of running the Normal Map shader code - because you are running a variant of the shader with that code omitted. It also means that if you never use a certain feature combination (such as HeightMap & Emissive together), that variant is completely omitted from your build - and in practice you will typically only use a very small number of the possible variants of the Standard Shader.

Unity avoids simply including every possible shader variant in your build, because this would be a very large number, some tens of thousands! This high number is a result not only of each possible combination of features available in the material inspector, but also there are variants of each feature combination for differing rendering scenarios such as whether or not HDR is being used, lightmaps, GI, fog, etc. Including all of these would cause slow loading, high memory consumption, and increase your build size and build time.

Instead, Unity tracks which variants you’ve used by examining the material assets used in your project. Whichever variants of the Standard Shader you have included in your project, those are the variants which are included in the build.

This presents two separate problems when accessing materials via script that use the Standard Shader.

### 1. You must enable the correct Keywords for your required Standard Shader variant

If you use scripting to change a Material that would cause it to use a different variant of the Standard Shader, you must **enable that variant by using the [EnableKeyword](http://docs.unity3d.com/ScriptReference/Material.EnableKeyword.html) function**. A different variant would be required if you start using a shader feature that was not initially in use by the material. For example assigning a Normal Map to a Material that did not have one, or setting the Emissive level to a value greater than zero, when it was previously zero.

The specific Keywords required to enable the Standard Shader features are as follows:

> Keyword Feature

\_NORMALMAP  [Normal Mapping](http://docs.unity3d.com/Manual/StandardShaderMaterialParameterNormalMap.html)

\_ALPHATEST\_ON   [“Cut out” Transparency](http://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html) Rendering Mode

\_ALPHABLEND\_ON  [“Fade” Transparency](http://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html) Rendering Mode

\_ALPHAPREMULTIPLY\_ON    “[Transparent” Transparency](http://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html) Rendering Mode

\_EMISSION   [Emission Colour](http://docs.unity3d.com/Manual/StandardShaderMaterialParameterEmission.html) or [Emission Mapping](http://docs.unity3d.com/Manual/StandardShaderMaterialParameterEmission.html)

\_PARALLAXMAP    [Height Mapping](http://docs.unity3d.com/Manual/StandardShaderMaterialParameterHeightMap.html)

\_DETAIL_MULX2   [Secondary “Detail” Maps](http://docs.unity3d.com/Manual/StandardShaderMaterialParameterDetail.html) (Albedo & Normal Map)

\_METALLICGLOSSMAP   [Metallic/Smoothness Mapping](http://docs.unity3d.com/Manual/StandardShaderMaterialParameterMetallic.html) in Metallic Workflow

\_SPECGLOSSMAP   [Specular/Smoothness Mapping](http://docs.unity3d.com/Manual/StandardShaderMaterialParameterSpecular.html) in Specular Workflow

Using the keywords above is enough to get your scripted Material modifications working while running in the editor.

However, because Unity only checks for Materials used in your project to determine which variants to include in your build, it will not include variants that are _only_ encountered via script at runtime.

This means if you enable the _PARALLAXMAP keyword for a Material in your script, but you do not have a Material used in your project matching that same feature combination, the parallax mapping will not work in your final build - even though it appears to work in the editor. This is because that variant will have been omitted from the build because it seemed to not be required.

### 2. You must make sure Unity includes your required shader variants in the build

To do this, you need to make sure Unity knows that you want to use that shader variant by including at least one Material of that type in your Assets. The material **must be used in a scene** or alternatively be placed in your [Resources Folder](http://docs.unity3d.com/Manual/LoadingResourcesatRuntime.html) - otherwise Unity will still omit it from your build, because it appeared unused.

By completing both of the above steps, you have the full ability to modify your Materials using the Standard Shader at runtime.

If you are interested in learning more about the details of shader variants, and how to write your own, read about [Making multiple shader program variants here](http://docs.unity3d.com/Manual/SL-MultipleProgramVariants.html).
