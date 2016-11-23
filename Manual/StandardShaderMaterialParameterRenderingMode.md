> [Rendering Mode](http://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html)

Unity Manual > Graphics > Graphics Overview > Materials, Shaders & Textures > Standard Shader > Material parameters > Rendering Mode

# Rendering Mode

![A Standard Shader material with default parameters and no values or textures assigned. The Rendering Mode parameter is highlighted.](http://docs.unity3d.com/uploads/Main/StandardShaderParameterRenderMode.png)
> A Standard Shader material with default parameters and no values or textures assigned. The Rendering Mode parameter is highlighted.

The first Material Parameter in the Standard Shader is **Rendering Mode**. This allows you to choose whether the object uses transparency, and if so, which type of blending mode to use.

* **Opaque** - Is the default, and suitable for normal solid objects with no transparent areas.
* **Cutout** - Allows you to create a transparent effect that has hard edges between the opaque and transparent areas. In this mode, there are no semi-transparent areas, the texture is either 100% opaque, or invisible. This is useful when using transparency to create the shape of materials such as leaves, or cloth with holes and tatters.
* **Transparent** - Suitable for rendering realistic transparent materials such as clear plastic or glass. In this mode, the material itself will take on transparency values (based on the texture’s alpha channel and the alpha of the tint colour), however reflections and lighting highlights will remain visible at full clarity as is the case with real transparent materials.
* **Fade** - Allows the transparency values to entirely fade an object out, including any specular highlights or reflections it may have. This mode is useful if you want to animate an object fading in or out. It iss not suitable for rendering realistic transparent materials such as clear plastic or glass because the reflections and highlights will also be faded out.

![The helmet visor in this image is rendered using the Transparent mode, because it is supposed to represent a real physical object that has transparent properties. Here the visor is reflecting the skybox in the scene. ](http://docs.unity3d.com/uploads/Main/StandardShaderTransparencySkyBoxReflection.png)
> The helmet visor in this image is rendered using the Transparent mode, because it is supposed to represent a real physical object that has transparent properties. Here the visor is reflecting the skybox in the scene.

![These windows use Transparent mode, but have some fully opaque areas defined in the texture (the window frames). The Specular reflection from the light sources reflects off the transparent areas and the opaque areas.](http://docs.unity3d.com/uploads/Main/StandardShaderTransparentWindow.png)
> These windows use Transparent mode, but have some fully opaque areas defined in the texture (the window frames). The Specular reflection from the light sources reflects off the transparent areas and the opaque areas.

![The hologram in this image is rendered using the Fade mode, because it is supposed to represent an opaque object that is partially faded out.](http://docs.unity3d.com/uploads/Main/StandardShaderFadeHologram.png)
> The hologram in this image is rendered using the Fade mode, because it is supposed to represent an opaque object that is partially faded out.

![The grass in this image is rendered using the Cutout mode. This gives clear sharp edges to objects which is defined by specifying a cut-off threshold. All parts of the image with the alpha value above this threshold are 100% opaque, and all parts below the threshold are invisible. To the right in the image you can see the material settings and the alpha channel of the texture used.](http://docs.unity3d.com/uploads/Main/StandardShaderCutoutGrassExample.png)
> The grass in this image is rendered using the Cutout mode. This gives clear sharp edges to objects which is defined by specifying a cut-off threshold. All parts of the image with the alpha value above this threshold are 100% opaque, and all parts below the threshold are invisible. To the right in the image you can see the material settings and the alpha channel of the texture used.