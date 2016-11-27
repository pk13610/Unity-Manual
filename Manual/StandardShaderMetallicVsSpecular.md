Unity Manual > Graphics > Graphics Overview > Materials, Shaders & Textures > Standard Shader > Metallic vs Specular Workflow

<!-- # Metallic vs Specular Workflow -->
# 工作流程：金属 vs 镜面

<!-- ### Two workflows -->
### 两种工作流程

<!-- When creating a material using the Standard shader you will have the choice of using one of two flavours, “Standard” and “Standard (Specular setup)”. They differ in the data they take as follows: -->
使用标准着色器创建材质时，你可以选择『标准』『标准（镜面）』两种类型之一。如下所述，它们的数据不同：

<!-- **Standard:** The shader exposes a “metallic” value that states whether the material is metallic or not. In the case of a metallic material, the Albedo color will control the color of your specular reflection and most light will be reflected as specular reflections. Non metallic materials will have specular reflections that are the same color as the incoming light and will barely reflect when looking at the surface face-on. -->
**标准：** 这种着色器暴露一个金属值，用于设置材质是否是金属。在一个金属材质中，漫反射颜色将控制反射的颜色，并且高亮（亮斑）。非金属材质将反射和入射光相同的颜色，并且没有高亮（亮斑）。

<!-- **Standard (Specular setup):** Choose this shader for the classic approach. A Specular color is used to control the color and strength of specular reflections in the material. This makes it possible to have a specular reflection of a different color than the diffuse reflection for instance. -->
**标准（镜面）：** 经典着色器。镜面颜色用于控制反射的颜色和强度。可以反射与漫反射不同的颜色。

<!-- It is generally possible to achieve a good representation of most common material types using either method, so for the most part choosing one or the other is a matter of personal preference to suit your art workflow. For instance, to below is an example of a rubbery plastic material created in both Standard and Standard Specular workflows: -->
无论使用哪一种类型，通常都可以很好的呈现大多数材质类型，所以，在大多数情况下，选择哪种取决于个人偏好，以及是否适合你的美术制作流程。例如下面的橡胶塑料材质例子，分别用标准工作流程和标准（镜面）工作流程创建：

![The fresnel effect visible at grazing angles in relation to the viewer is increasingly apparent as the surface of a material becomes smoother](http://docs.unity3d.com/uploads/Main/StandardShaderRubberAsMetallicOrSpecular.png)
<!-- > The fresnel effect visible at grazing angles in relation to the viewer is increasingly apparent as the surface of a material becomes smoother -->
> 随着材质表面变得更光滑，观察者在掠射角处看到的菲涅耳效应越来越明显。

<!-- The first image represents the metallic workflow, where we are setting this material to zero (non metallic). The second setup is nearly identical but we set the specular to nearly black (so we don’t get metallic mirror-like reflections) -->
第一张图演示了金属工作流程，设置它的金属值为 0（表示非金属）。第二张图的设置与第一张几乎一样，但是把镜面颜色设置为接近黑色（所以不会得到类似金属镜面的反射）。

<!-- One might ask where do these values come from, what is “nearly black” and what makes grass different from aluminium exactly? In the world of Physically Based Shading we can use references from known real-world materials. Some of those references we have compiled into a handy set of charts you can use to create your materials. -->
有人可能会问，这些值是从哪里得来的，接近黑色是什么颜色，是什么让草与铝完全不同的？在遵循物理定律的着色过程中，我们可以参考现实世界的材质。我们已经把其中一些材质编成一张快速参照图表，你可以用它来创建材质。

> 译注：[光学现象整理](http://www.guokr.com/blog/473600/)
