> [Emission](http://docs.unity3d.com/Manual/StandardShaderMaterialParameterEmission.html)

Unity Manual > Graphics > Graphics Overview > Materials, Shaders & Textures > Standard Shader > Material parameters > Emission

# Emission

![](http://docs.unity3d.com/uploads/Main/StandardShaderParameterEmission.png)

Controls colour and intensity of light emitted from the surface. When an emissive material is used in your scene, it appears to be a visible source of light itself. The object will appear “self illuminated”.

Emissive materials are usually used on objects where some part should appear to be lit up from inside, such as the screen of a monitor, the disc brakes of a car braking at high speed, glowing buttons on a control panel, or a monster’s eyes which are visible in the dark.

Simple emissive materials can be defined using a single colour and emission level. If you set the emission level to a value higher than the default zero, the emission colour and strength field will appear:

![A material with a red emission colour, and an emission brightness of 0.5](http://docs.unity3d.com/uploads/Main/StandardShaderEmissiveFlatMaterialInspector.png)
> A material with a red emission colour, and an emission brightness of 0.5

Objects using these materials will appear to remain bright even when in dark areas in your scene.

![Red, Green and Blue spheres using emissive materials. Even though they are in a dark scene, they appear lit from an internal light source.](http://docs.unity3d.com/uploads/Main/StandardShaderEmissiveFlatColour.png)
> Red, Green and Blue spheres using emissive materials. Even though they are in a dark scene, they appear lit from an internal light source.

As well as simple control over emission using a flat colour and brightness setting, you can assign an emission map to this parameter. As with the other texture map parameters, this gives you much finer control over which areas of your material appear to emit light.

If a texture map is assigned, the full colour values of the texture are used for the emission colour and brightness. The emission value numeric field remains, which you can use as a multiplier to boost or reduce the overall emission level of your material.

![Shown in the inspector, Left: An emission map for a computer terminal. It has two glowing screens and glowing keys on a keyboard. Right: The emissive material using the emission map. The material has both emissive and non-emissive areas.](http://docs.unity3d.com/uploads/Main/StandardShaderEmissiveMaterialInspector.png)
> Shown in the inspector, Left: An emission map for a computer terminal. It has two glowing screens and glowing keys on a keyboard. Right: The emissive material using the emission map. The material has both emissive and non-emissive areas.

![In this image, there are areas of high and low levels of light, and shadows falling across the emissive areas which gives a full representation of how emissive materials look under varying light conditions.](http://docs.unity3d.com/uploads/Main/StandardShaderEmissiveInLightAndShadow.png)
> In this image, there are areas of high and low levels of light, and shadows falling across the emissive areas which gives a full representation of how emissive materials look under varying light conditions.

As well as the emission colour and brightness, the Emission parameter has a Global Illumination setting, allowing you to specify how the apparent light emitted from this material will affect the contextual lighting of other nearby objects. There are three options

* **None** - The object will appear emissive, but the lighting of nearby objects will not be affected.
* **Realtime** - The emissive light from this material will be added to the realtime global illumination calculations for the scene, so the lighting of nearby objects, even moving objects, will be affected by the emitted light.
* **Baked** - The emissive light from this material will be baked into the static lightmaps for the scene, so other nearby static objects will appear to be lit by this material, but dynamic objects will not be affected.

![Baked emissive values from the computer terminals emission map light up the surrounding areas in this dark scene](http://docs.unity3d.com/uploads/Main/StandardShaderEmissiveBakedEffect.png)
> Baked emissive values from the computer terminal’s emission map light up the surrounding areas in this dark scene
