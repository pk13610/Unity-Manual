<!-- > [Metallic mode: Metallic Parameter](http://docs.unity3d.com/Manual/StandardShaderMaterialParameterMetallic.html) -->

<!-- Unity Manual > Graphics > Graphics Overview > Materials, Shaders & Textures > Standard Shader > Material parameters > Metallic mode: Metallic Parameter -->

<!-- # Metallic mode: Metallic Parameter -->
# 金属模式：金属参数

![](http://docs.unity3d.com/uploads/Main/StandardShaderMetallicMode.png)

<!-- When working in the **Metallic workflow** (as opposed to the Specular workflow), the the reflectivity and light response of the surface are modified by the Metallic level and the [Smoothness](http://docs.unity3d.com/Manual/StandardShaderMaterialParameterSmoothness.html) level. -->
当使用 **金属工作流程**（相对于镜面工作流程）时，表面的发射率和光照通过金属度和平滑度修改。

[平滑度]: http://docs.unity3d.com/Manual/StandardShaderMaterialParameterSmoothness.html

![](http://docs.unity3d.com/uploads/Main/StandardShaderParameterMetallic.png)

<!-- Specular reflections are still generated when using this workflow but they arise naturally depending on the settings you give for the Metallic and Smoothness levels, rather than being explicitly defined. -->
当使用这种流程时，仍然会生成镜面反射，但是看起来是否真实，取决于设置的金属度和平滑度，而不是一个明确定义的开关。

<!-- **Metallic mode is not just for materials which are supposed to look metallic!** This mode is known as metallic because of the way you have control over how metallic or non-metallic a surface is. -->
**金属模式不仅仅适用于看起来有金属质感的材质！**这种模式之所以为称为金属模式，是因为你可以通过它控制物体表面的金属或非金属程度（译注：是否是金属或非金属，以及程度）。

<!-- ### Metallic parameter -->
### 金属参数

<!-- The metallic parameter of a material determines how “metal-like” the surface is. When a surface is more metallic, it reflects the environment more and its albedo colour becomes less visible. At full metallic level, the surface colour is entirely driven by reflections from the environment. When a surface is less metallic, its albedo colour is more clear and any surface reflections are visible on top of the surface colour, rather than obscuring it. -->
材质的金属参数决定了物体表面的金属度。当表面更像金属时，将反射更多的环境光照，散射颜色变得不可见。当表面是全属性时，表面颜色完全由环境光照驱动。当表面不像金属时，它的散射颜色更加清晰，并且，表面反射的光照更弱，不会使散射颜色模糊。

![A range of metallic values from 0 to 1 (with smoothness at a constant 0.8 for all samples)](http://docs.unity3d.com/uploads/Main/StandardShaderMetallicGraduationTable.png)
<!-- > A range of metallic values from 0 to 1 (with smoothness at a constant 0.8 for all samples) -->
> 金属度的范围从 0 到 1（平滑度固定为 0.8）。

<!-- By default, with no texture assigned, the Metallic and Smoothness parameters are controlled by a slider each. This is enough for some materials. However if your model’s surface has areas with a mixture of surface types in the albedo texture, you can use a texture map to control how the metallic and smoothness levels vary across the surface of the material. For instance if your texture contains a character’s clothing including some metal buckles and zips. You would want the buckles and zips to have a higher metallic value than the fabric of the clothes. To achieve this, instead of using a single slider value, a texture map can be assigned which contains lighter pixel colours in the areas of the buckles and zips, and darker values for the fabric. -->
默认情况下是没有指定文理的，金属度和平滑度参数由一个滑动器控制。这对于某些材质已经足够。但是，如果模型表面是由散射纹理中的多种表面类型混合而成，则可以使用一张纹理贴图来控制整个材质表面的金属度和光滑度。例如，一个角色服饰的散射纹理包含了金属纽扣和拉链。你会希望纽扣和拉链比服饰的布料具有更高金属度。为了实现这一点，不能使用滑动器的值，而是指定一张纹理贴图，其中，在纽扣和拉链区域包含更亮的像素颜色，在布料区域包含较暗的像素颜色。

<!-- With a texture assigned to the Metallic parameter, both the Metallic and Smoothness sliders will disappear. Instead, the Metallic levels for the material are controlled by the values in the Red channel of the texture, and the [Smoothness](http://docs.unity3d.com/Manual/StandardShaderMaterialParameterSmoothness.html) levels for the material are controlled by the Alpha channel of the texture. (This means the Green and Blue channels are ignored). This means you have a single texture which can define areas as being rough or smooth, and metallic or non-metallic, which is very useful when working texture maps that cover many areas of a model with varying requirements - for example a single character texture map often includes multiple surface requirements - leather shoes, cloth clothes, skin for the hands and face and metal buckles. -->
指定一张纹理后，金属度和平滑度的滑动器将消失。此时，材质的金属度将由纹理的红色通道控制，材质的平滑度将由纹理的 Alpha 通道控制。（这意味着，绿色和蓝色通道被忽略。）这意味着，通过一张纹理，就可以定义粗糙区域、平滑区域、金属区域和非金属区域，当遇到纹理贴图覆盖的区域有不同的需求时 — 皮鞋，布衣，手和脸的皮肤，金属纽扣 — 这种方式非常有用。

![This image shows a case model with no metallic map](http://docs.unity3d.com/uploads/Main/StandardShaderNoMetallicMap.png)
<!-- > This image shows a case model with no metallic map -->
> 这张图像演示了没有金属贴图的情况。

<!-- In the example above, the case has an albedo map, but no texture for Metallic. This means the whole object has a single metallic and smoothness value, which is not ideal. The leather straps, the metal buckles, the sticker and the handle should all appear to have different surface properties. -->
在上面的例子中，材质拥有一个散射贴图，但是没有金属贴图。这意味着，整个物体只有一种金属度和平滑度，显然不理想。皮带、金属带扣、帖子和提手应该呈现不同的表面特性。

![This image shows a case model with a metallic map applied](http://docs.unity3d.com/uploads/Main/StandardShaderMetallicMap.png)
<!-- > This image shows a case model with a metallic map applied -->
> 这张图像演示了拥有金属贴图的情况。

<!-- In this example, a Metal/Smoothness texture map has been assigned. The buckle now has a high metallic value and responds to light accordingly. The leather straps are shinier than the leather body of the box, however they have a low “Metallic” value, so it appears to be shiny non-metal surface. The black and white map on the far right shows the lighter areas for metal, and mid to low greys for the leather. -->
在这个例子中，指定了一张金属度/平滑度贴图。带扣的金属度更高，响应的光照相应更亮。皮带比皮箱更光亮，尽管它们的金属度都比较低，但是仍然呈现出有光泽的非金属表面，最右侧贴图中的黑色和白色区域用于显示更亮的金属区域，低灰度区域用于显示皮革。
