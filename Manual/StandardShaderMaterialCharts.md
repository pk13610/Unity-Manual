<!-- > [Material charts](http://docs.unity3d.com/Manual/StandardShaderMaterialCharts.html) -->

<!-- Unity Manual > Graphics > Graphics Overview > Materials, Shaders & Textures > Standard Shader > Material charts -->

<!-- # Material charts -->
# 材质图表

<!-- ## Use these charts as reference for realistic settings: -->
## 使用这些图表作为实际设置的参考：

![Reference Chart for Metallic settings](http://docs.unity3d.com/uploads/Main/StandardShaderCalibrationChartMetallic.png)
<!-- > Reference Chart for Metallic settings -->
> 金属设置的参考图表。
>
> 译注：下面是图表中的中英文对照：
> 
> SHADER CALIBRATION SCENE
> 
> 着色器校准场景
> 
> METALLIC VALUE CHARTS
> 
> 金属度图表
> 
> ALBEDO RGB
> 
> 漫反射颜色
> 
> ALBEDO DEFINES THE OVERALL COLOUR OF AN OBJECT
> 
> 漫反射定义了物体的总体颜色
> 
> VALUES USUALLY MATCH THE PERCEIVED COLOR OF AN OBJECT
> 
> 通常值与感知到物体颜色一致
> 
> MEDIAN LUMINOSITY
> 
> 平均亮度
> 
> COAL     煤炭
> RUBBER   橡胶
> MUD      泥
> GRASS    草
> BRICK    砖
> WOOD     木
> CONCRETE 混凝土
> GOLD     黄金
> BRASS    黄铜
> COPPER   铜
> IRON     铁
> PLATIUM  铂
> ALUMINUM 铝
> SLIVER   银
> 
> METELLIC R 
> 
> 金属度
> 
> METALLIC DEFINES WHETHER A SURFACE APPEARS TO BE METAL OR NON-METAL
> 
> 金属度定义了表面是否呈现为金属或非金属
> 
> WHILST PURE SURFACES WILL BE EITHER 0.0 OR 1.0. BEAR IN MIND FEW PURE, CLEAN, UNWEATHERED MATERIALS EXIST IN REAL LIFE.
> 
> 尽管纯粹的的表面要么是 0.0 要么是 1.0。但是记住，现实生活中几乎不存在纯粹的、干净的材质。
> 
> WHEN TEXTURING A METALLIC MAP. THIS VALUE WILL ALWAYS BE GREYSCALE AND IS STORED IN THE R CHANNEL OF AN RGB FILE.
> 
> 设置金属贴图纹理时，该值总是灰色的，并且存储在 RGB 文件的 R 通道中。
> 
> SMOOTHNESS A
> 平滑度
> 
> SMOOTHNESS DEFINES THE PERCEIVED GLOSSINESS OR ROUGHNESS OF A SURFACE FOR TEXTTURES. THIS IS STORED AS THE ALPHA CHANNEL OF THE METALLIC MAP
> 
> 平滑度定义了表面纹理可感知的光泽度和粗糙度。该值存在金属贴图的 ALPHA 通道中。

![Reference Chart for Specular settings](http://docs.unity3d.com/uploads/Main/StandardShaderCalibrationChartSpecular.png)
<!-- > Reference Chart for Specular settings -->
> 镜面设置的参考图表。
> 
> 译注：从前面的文档看，镜面模式使用起来不够友好，就不翻译了。

<!-- There are also hints on how to make realistic materials in these charts. In essence it is about choosing a workflow (default or metallic) and obtaining relevant values for your maps or colour pickers. For instance, if we wanted to make shiny white plastic, we would want a white Albedo. Since it is not a metal we would want a dark Specular (or a very low Metallic value) and finally a very high Smoothness. -->

在这些图表中的，还有一些如何创建真实材料的提示。本质上，是选择一个工作流程（金属模式或镜面模式），然后为纹理或颜色选择器设置相应的值。举个例子，如果想要制作闪亮的白色塑料，我们需要设置漫反射为白色。因为它不是金属，我们需要一个非常低的 Metallic 值（或深色的 Specular），和一个非常高的平滑度。
