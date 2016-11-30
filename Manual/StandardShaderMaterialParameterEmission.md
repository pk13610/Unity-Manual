<!-- > [Emission](http://docs.unity3d.com/Manual/StandardShaderMaterialParameterEmission.html) -->

<!-- Unity Manual > Graphics > Graphics Overview > Materials, Shaders & Textures > Standard Shader > Material parameters > Emission -->

<!-- # Emission -->
# 自发光

![](http://docs.unity3d.com/uploads/Main/StandardShaderParameterEmission.png)

<!-- Controls colour and intensity of light emitted from the surface. When an emissive material is used in your scene, it appears to be a visible source of light itself. The object will appear “self illuminated”. -->
控制表面发射光的颜色和亮度。当场景中使用了自发光材质时，它看起来像一个可见光。物体将呈现『自发光』效果。

<!-- Emissive materials are usually used on objects where some part should appear to be lit up from inside, such as the screen of a monitor, the disc brakes of a car braking at high speed, glowing buttons on a control panel, or a monster’s eyes which are visible in the dark. -->
自发光材质通常用于某些部位应该从内部照亮的物体上，例如监视器屏幕、高速制动的汽车盘式制动器、控制面板上的发光按钮，或黑暗中仍然可见的怪物眼睛。

<!-- Simple emissive materials can be defined using a single colour and emission level. If you set the emission level to a value higher than the default zero, the emission colour and strength field will appear: -->
简单的自发光材质可以通过一个颜色和亮度来定义。如果设置为自发光亮度设置一个大于 0 的值，物体将呈现自发光颜色和亮度：

![A material with a red emission colour, and an emission brightness of 0.5](http://docs.unity3d.com/uploads/Main/StandardShaderEmissiveFlatMaterialInspector.png)
<!-- > A material with a red emission colour, and an emission brightness of 0.5 -->
> 材质自身发射红色光，亮度为 0.5。

<!-- Objects using these materials will appear to remain bright even when in dark areas in your scene. -->
使用了自发光材质的物体，即使在场景的黑暗区域，也会保持亮度。

![Red, Green and Blue spheres using emissive materials. Even though they are in a dark scene, they appear lit from an internal light source.](http://docs.unity3d.com/uploads/Main/StandardShaderEmissiveFlatColour.png)
<!-- > Red, Green and Blue spheres using emissive materials. Even though they are in a dark scene, they appear lit from an internal light source. -->
> 使用了自发光材质的红球、绿球和篮球。即使它们位于一个黑暗的场景中，看起来让然像是被内部光源照亮了。

<!-- As well as simple control over emission using a flat colour and brightness setting, you can assign an emission map to this parameter. As with the other texture map parameters, this gives you much finer control over which areas of your material appear to emit light. -->
除了使用单一颜色和亮度简单地控制自发光外，还可以为这个参数指定一张自发光贴图。与其他纹理贴图参数一样，这种方式可以更好地控制材质的发光区域。

<!-- If a texture map is assigned, the full colour values of the texture are used for the emission colour and brightness. The emission value numeric field remains, which you can use as a multiplier to boost or reduce the overall emission level of your material. -->
如果指定了纹理贴图，纹理中的全部颜色值被用于定义自发光颜色和亮度。亮度数值输入框被保留了下来，可以把它作为一个乘数，提高或降低材质的整体亮度。

![Shown in the inspector, Left: An emission map for a computer terminal. It has two glowing screens and glowing keys on a keyboard. Right: The emissive material using the emission map. The material has both emissive and non-emissive areas.](http://docs.unity3d.com/uploads/Main/StandardShaderEmissiveMaterialInspector.png)
<!-- > Shown in the inspector, Left: An emission map for a computer terminal. It has two glowing screens and glowing keys on a keyboard. Right: The emissive material using the emission map. The material has both emissive and non-emissive areas. -->
> 检视视图截图。左边：一张计算机终端的自发光贴图，含有两个发光屏幕和两个背光键盘。右边：使用这张自发光贴图的自发光材质。这个材质同时含有自发光和不发光区域。

![In this image, there are areas of high and low levels of light, and shadows falling across the emissive areas which gives a full representation of how emissive materials look under varying light conditions.](http://docs.unity3d.com/uploads/Main/StandardShaderEmissiveInLightAndShadow.png)
<!-- > In this image, there are areas of high and low levels of light, and shadows falling across the emissive areas which gives a full representation of how emissive materials look under varying light conditions. -->
> 在这张图中，存在了明亮和昏暗区域，以及投射在发光区域的阴影，完美呈现了自发光材质在不同光照条件下的视觉效果。

<!-- As well as the emission colour and brightness, the Emission parameter has a Global Illumination setting, allowing you to specify how the apparent light emitted from this material will affect the contextual lighting of other nearby objects. There are three options -->
自发光参数带有一个全局光照设置，允许你指定该材质发射的光对附近物体的上下文光照的影响方式。提供了 3 个选项：

<!-- 
* **None** - The object will appear emissive, but the lighting of nearby objects will not be affected.
* **Realtime** - The emissive light from this material will be added to the realtime global illumination calculations for the scene, so the lighting of nearby objects, even moving objects, will be affected by the emitted light.
* **Baked** - The emissive light from this material will be baked into the static lightmaps for the scene, so other nearby static objects will appear to be lit by this material, but dynamic objects will not be affected.
 -->
* **None** - 该物体将呈现为自发光，但是附近物体的光照不会受到影响。
* **Realtime** - 该材质的自发光将被添加到场景全局光照计算中，因此，附近物体甚至是移动物体将会受到自发光的影响。
* **Baked** - 该材质的自发光将被烘培到场景的静态光照贴图中，所以，附近物体将被该材质照亮，但是动态物体不会受到影响。

![Baked emissive values from the computer terminals emission map light up the surrounding areas in this dark scene](http://docs.unity3d.com/uploads/Main/StandardShaderEmissiveBakedEffect.png)
<!-- > Baked emissive values from the computer terminal’s emission map light up the surrounding areas in this dark scene -->
> 烘培计算终端的自发光贴图后，照亮了周围的黑暗区域。
