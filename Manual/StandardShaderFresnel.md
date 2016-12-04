<!-- Unity Manual > Graphics > Graphics Overview > Materials, Shaders & Textures > Standard Shader > Material parameters > The Fresnel Effect -->

<!-- # The Fresnel Effect -->
# 菲涅耳效应

<!-- One important visual cue of objects in the real world has to do with how they become more reflective at grazing angles (illustrated below). This is called the Fresnel effect. -->
在现实世界中，物体的一个重要视觉暗示是，在掠射角处变得更具反射性（如下图所示）。这辈称为菲涅耳效应。

![The fresnel effect visible at grazing angles in relation to the viewer is increasingly apparent as the surface of a material becomes smoother](https://docs.unity3d.com/uploads/Main/StandardShaderFresnelGraduationTable.png)
<!-- > The fresnel effect visible at grazing angles in relation to the viewer is increasingly apparent as the surface of a material becomes smoother -->
> 随着材质表面变得更加光滑，观察者在掠射角处看到的非涅尔效应越来越明显。

<!-- There are two things to note in this example; firstly, these reflections only appear around the edges of the sphere (that’s when its surface is at a grazing angle), and also that they become more visible and sharper as the smoothness of the material goes up. -->
在这个例子中有两点需要注意：首先，这些反射仅仅出现在球体的边缘（此时表面处于掠射角），并且，随着材质平滑度的提升，它们变得更加清晰和尖锐。

<!-- In the Standard shader there is no direct control over the Fresnel effect. Instead it is indirectly controlled through the smoothness of the material. Smooth surfaces will present a stronger Fresnel, totally rough surfaces will have no Fresnel. -->
在标准着色器中没有对菲涅耳效应的直接控制。相反，需要通过材质的平滑度来间接控制。平滑的表面将呈现更强烈的菲涅耳效应，完全粗糙的表面不会有菲涅耳效应。
