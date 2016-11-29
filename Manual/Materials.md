<!-- > [Creating and Using Materials](http://docs.unity3d.com/Manual/Materials.html) -->

<!-- Unity Manual > Graphics > Graphics Overview > Materials, Shaders & Textures > Creating and Using Materials -->

<!-- # Creating and Using Materials -->
# 创建和使用材质

<!-- To create a new Material, use **Assets->Create->Material** from the main menu or the Project View context menu. -->
通过主菜单 **Assets->Create->Material**，或者项目视图的上下文菜单，可以创建一个新材质。

<!-- By default, new materials are assigned the Standard Shader, with all map properties empty, like this: -->
默认情况下，新建材质会分配到标准着色器，并且所有属性都空着，就像这样：

![](http://docs.unity3d.com/uploads/Main/StandardShaderNewEmptyMaterial.png)

<!-- Once the Material has been created, you can apply it to an object and tweak all of its properties in the **Inspector**. To apply it to an object, just drag it from the **Project View** to any object in the **Scene** or **Hierarchy**. -->
一旦材质被创建，你就可以把它应用到一个对象，并且可以在**检视试图**中修改它所有的属性。想把材质应用到一个对象上，只需要把材质从**项目视图**拖动到**场景是图**或**层级视图**中的任意对象上。

<!-- ## Setting Material Properties -->
## 设置材质属性

<!-- You can select which Shader you want any particular Material to use. Simply expand the **Shader** drop-down in the Inspector, and choose your new Shader. The Shader you choose will dictate the available properties to change. The properties can be colors, sliders, textures, numbers, or vectors. If you have applied the Material to an active object in the **Scene**, you will see your property changes applied to the object in real-time. -->
你可以为材质选择任意着色器。操作非常简单，在检视试图中展开**着色器**下单框，选择新着色器。你选择的着色器将决定可改变的有效属性。属性可以是颜色、滑动器、数值或向量。如果你已经把材质应用到**场景试图**中的某个激活对象上，属性改变就会实时应用到该对象上。

<!-- There are two ways to apply a **Texture** to a property. -->
把纹理应用到某个属性有两种方式。

<!-- 
* Drag it from the Project View on top of the Texture square
* Click the **Select** button, and choose the texture from the drop-down list that appears
 -->
* 从项目视图拖动纹理资源到检视试图的纹理方框上。
* 点击**选择**按钮，从弹出的下拉列表中选择纹理资源。

<!-- ## Built-in Shaders -->
## 内置着色器

<!-- In addition to the [Standard Shader](http://docs.unity3d.com/Manual/shader-StandardShader.html), there are a number of other categories of built-in shaders for specialised purposes: -->
除了[标准着色器](http://docs.unity3d.com/Manual/shader-StandardShader.html)，还是许多其他类型的内置着色器，用于不同的用途：

<!-- 
* **FX**: Lighting and glass effects.
* **GUI** and **UI**: For user interface graphics.
* **Mobile**: Simplified high-performance shader for mobile devices.
* **Nature**: For trees and terrain.
* **Particles**: Particle system effects.
* **Skybox**: For rendering background environments behind all geometry
* **Sprites**: For use with the 2D sprite system
* **Toon**: Cartoon-style rendering.
* **Unlit**: For rendering that entirely bypasses all light & shadowing
* **Legacy**: The large collection of older shaders which were superseded by the * Standard Shader
 -->
* **FX**：用于光照和玻璃效果。
* **GUI** 和 **UI**：用于用户图形界面。
* **Mobile**：用于移动设备的高性能着色器。
* **Nature**：用于树木和地形.
* **Particles**：用于粒子系统效果.
* **Skybox**：用于渲染位于所有几何图形之后的背景环境。
* **Sprites**：用于 2D 精灵系统。
* **Toon**：用于渲染卡通风格。
* **Unlit**：用于绕开所有光照和阴影的渲染。
* **Legacy**：大量老版本着色器的集合，已经被标准着色器取代。

<!-- ## Shader technical details -->
## 着色器技术细节

<!-- A Shader is a script which contains mathematical calculations and algorithms for how the pixels on the surface of a model should look. The standard shader performs complex and realistic lighting calculations. Other shaders may use simpler or different calculations to show different results. Within any given Shader are a number of properties which can be given values by a Material using that shader. These properties can be numbers, colours definitions or textures, which appear in the inspector when viewing a Material. Materials are then used by Renderer components attached to Game Objects, to render each Game Object’s mesh. -->
一个着色器是一段包含了数学计算和算法的脚本，用于决定模型表层的外观。标准着色器执行复杂而逼真的光照计算。其他着色器可能采用简化或不同的计算方式，从而现实不同的结果。任意一个着色器都带有一组可改变的属性。这些属性可能是数值、颜色或纹理，当你查看材质时，属性会显示在检视试图中。材质被绑定到游戏对象的 Renderer 组件所使用，用于选择游戏对象的网格。

<!-- It is possible and often desirable to have several different Materials which may reference the same textures. These materials may also use the same or different shaders, depending on the requirements. -->
多个不同的材质可以引用同一个纹理。这些材质可以使用相同或不同的着色器，完全取决于需求。

<!-- Below is an example of a possible set-up combination using three materials, two shaders and one texture. -->
下面是一套设置组合的示例，用到了 3 个材质、2 个着色器和 1 个纹理。

![](https://docs.unity3d.com/550/Documentation/uploads/Main/material_diagram.png)
<!-- > In the diagram we have a red car and a blue car. Both models use a separate material for the bodywork, “Red car material” and “Blue car material” respectively. -->
> 在上图中，有一辆红车和蓝车。两个模型的车身使用不同的材质，红车材质和蓝车材质。

<!-- Both these bodywork materials use the same custom shader, “Carbody Shader”. A custom shader may be used because the shader adds extra features specifically for the cars, such as metallic sparkly rendering, or perhaps has a custom damage masking feature. -->
两个车身材质使用同一个自定义着色器 — 车身着色器。使用自定义着色器，是因为它可以为汽车提供额外的功能，例如金属反光渲染，或者可能提供自定义的损伤变形功能。

<!-- Each car body material has a reference to the “Car Texture”, which is a texture map containing all the details of the bodywork, without a specific paint colour. -->
每个车身材质都引用了汽车纹理，一张包含了车身所有细节的纹理图，其中，但是没有指定绘制颜色。

<!-- The Carbody shader also accepts a tint colour, which is set to a different colour for the red and blue cars, giving each car a different look while using a single texture for both of them. -->
车身着色器还可以接受一个色调，用于为红车和蓝车设置不同的色调，从而让两辆车拥有不同的外观，而我们只使用了一张纹理。

<!-- The car wheel models use a separate material again, but this time both cars share the same material for their wheels, as the wheels do not differ on each car. The wheel material uses the Standard Shader, and has a reference again to the Car Texture. -->
车轮使用一个独立的材质，但是两辆车的车轮共享这个材质，因为两辆车的车轮并没有什么不同。车轮材质使用标准着色器，，并再次引用汽车纹理。

<!-- Notice how the car texture contains details for the bodywork _and wheels_ - this is a _texture atlas_, meaning different parts of the texture image are explicitly mapped to different parts of the model. -->
需要注意到，汽车纹理同时包含了车身和_轮胎_的细节 — 称为_纹理集_，纹理贴图的不同部分可以明确地映射到模型的不同部位。

<!-- Even though the bodywork materials are using a texture that also contains the wheel image, the wheel does not appear on the body because that part of the texture is not mapped to the bodywork geometry. -->
尽管车身材质引用了一个包含车轮图像的纹理，但是车轮不会显示在车上上，因为问题车轮部分没有映射到车身结构。

<!-- Similarly, the wheel material is using the same texture, which has bodywork detail in it. The bodywork detail does not appear on the wheel, because only the portion of the texture showing the wheel detail is mapped to the wheel geometry. -->
同样的，车轮材质也使用了同一个材质，其中包含了车身细节。但是车身细节不会显示在车轮，因为只有贴图的车轮细节被映射到了车轮结构。

<!-- This mapping is done by the 3D artist in an external 3d application, and is called “UV mapping”. -->
映射关系由外部 3D 应用程序制作，称为 UV 映射。

<!-- To be more specific, a Shader defines: -->
更具体地说，一个着色器定义了：

<!-- 
* The method to render an object. This includes code and mathematical calculations that may include the angles of light sources, the viewing angle, and any other relevant calculations. Shaders can also specify different methods depending on the graphics hardware of the end user.
* The parameters that can be customised in the material inspector, such as texture maps, colours and numeric values.
 -->
* 渲染游戏对象的方法。包括代码和数学计算，数学计算包括光源角度、视角和其他所有相关计算。着色器也可以基于终端用户的图形硬件指定不同的方法。
* 在材质检视试图中可以自定义参数，例如纹理映射、色彩和数值。

<!-- A Material defines: -->
一个材质定义了：

<!-- 
* Which shader to use for rendering this material.
* The specific values for the shader’s parameters - such as which texture maps, the colour and numeric values to use.
 -->
* 使用哪种着色器来渲染材质。
* 该着色器参数的具体值 — 例如使用哪个纹理映射、色彩值和数值。

<!-- Custom Shaders are meant to be written by graphics programmers. They are created using the **ShaderLab** language, which is quite simple. However, getting a shader to work well on a variety graphics cards is an involved job and requires a fairly comprehensive knowledge of how graphics cards work. -->
自定义着色器由图形程序员编写。使用 **ShaderLab** 语言，非常简单。不过，让一个着色器在各种各样的图形显卡上运行正常，是一项复杂的工作，并且要求对显卡运行原理有相当全面的知识。

<!-- A number of shaders are built into Unity directly, and some more come in the [Standard Assets](http://docs.unity3d.com/Manual/HOWTO-InstallStandardAssets.html) Library. -->
一些着色器直接内置在 Unity 中，更多着色器在 [标准资源](http://docs.unity3d.com/Manual/HOWTO-InstallStandardAssets.html) 库中。