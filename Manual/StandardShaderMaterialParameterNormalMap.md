<!-- > [Normal map (Bump mapping)](http://docs.unity3d.com/Manual/StandardShaderMaterialParameterNormalMap.html) -->

<!-- Unity Manual > Graphics > Graphics Overview > Materials, Shaders & Textures > Standard Shader > Material parameters > Normal map (Bump mapping) -->

<!-- # Normal map (Bump mapping) -->
# 法线贴图（凹凸贴图）

![](http://docs.unity3d.com/uploads/Main/StandardShaderParameterNormalMap.png)

<!-- Normal maps are a type of **Bump Map**. They are a special kind of texture that allow you to add surface detail such as bumps, grooves, and scratches to a model which catch the light as if they are represented by real geometry. -->
法线贴图是 **凹凸贴图** 的一种。凹凸贴图是一种特殊的纹理，允许为模型添加表面细节，例如凸起、凹槽和划痕光，这些细节将捕获光线，就像真实的几何体一样。

<!-- For example, you might want to show a surface which has grooves and screws or rivets across the surface, like an aircraft hull. One way to do this would be to model these details as geometry, as shown below. -->
举个例子，你可能想要显示一个具有凹槽、螺丝钉或铆钉的表面，例如飞机机身。一种实现方式是为这些细节进行几何建模，如下所示。

![A sheet of aircraft metal with details modeled as real geometry.](http://docs.unity3d.com/uploads/Main/StandardShaderNormalMapBadGeometry.png)
<!-- > A sheet of aircraft metal with details modeled as real geometry. -->
> 一张飞机金属板，以真实的几何形状为细节建模。

<!-- Depending on the situation it is not normally a good idea to have such tiny details modelled as “real” geometry. On the right you can see the polygons required to make up the detail of a single screwhead. Over a large model with lots of fine surface detail this would require a very high number of polygons to be drawn. To avoid this, we should use a normal map to represent the fine surface detail, and a lower resolution polygonal surface for the larger shape of the model. -->
以真实几何形状为如此细微的细节建模通常不是一个好主意。在上图右侧， 你可以看到组成单个螺丝头细节所需的多边形。带有大量清晰细节的大型模型，将需要绘制非常多数量的多边形。为了避免这种情况，应该使用法线贴图来表示清晰的表面细节，较大形状的模型使用较低分辨率的多边形表面。

<!-- If we instead represent this detail with a bump map, the surface geometry can become much simpler, and the detail is represented as a texture which modulates how light reflects off the surface. This is something modern graphics hardware can do extremely fast. Your metal surface can now be a low-poly flat plane, and the screws, rivets, grooves and scratches will catch the light and appear to have depth because of the texture. -->
如果使用一张凹凸贴图来呈现细节，表面的几何形状可以变得更加简单，用细节纹理调制光从表面反射的方式。现代图形硬件可以非常快地执行这个个过程。现在，金属表面是一个低面数（低多边形）的平面，螺丝、铆钉和划痕将捕获光线，并且因为纹理贴图，它们看起来似乎有了深度。

![The screws, grooves and scratches are defined in a normalmap, which modifies how light reflects off the surface of this low-poly plane, giving the impression of 3D detail. As well as the rivets and screws, a texture allows us to include far more detail like subtle bumps and scratches.](http://docs.unity3d.com/uploads/Main/StandardShaderNormalMapAircraftSurface.png)
<!-- > The screws, grooves and scratches are defined in a normalmap, which modifies how light reflects off the surface of this low-poly plane, giving the impression of 3D detail. As well as the rivets and screws, a texture allows us to include far more detail like subtle bumps and scratches. -->
> 法线贴图中定义了螺钉、凹槽和划痕，修改了从低面数平面外表反射光线的方式，从而使这些细节呈现出 3D 效果。除了铆钉和螺丝，纹理支持更多的细节，例如微小的凸起和划痕。

<!-- In modern game development art pipelines, artists will use their 3D modelling applications to generate normal maps based on very high resolution source models. The normal maps are then mapped onto a lower-resolution game-ready version of the model, so that the original high-resolution detail is rendered using the normalmap. -->
在现代游戏开发流程中，设计师将使用 3D 建模软件，基于非常高分辨率的原始模型生成法线贴图。然后，将法线贴图映射到较低分辨率的模型（游戏中实际使用的模型）上，这样，通过法线贴图，原始的高分率细节就被渲染了。

<!-- # How to create and use Bump Maps -->
# 如何创建和使用凹凸贴图

<!-- Bump mapping is a relatively old graphics technique, but is still one of the core methods required to create detailed realistic realtime graphics. Bump Maps are also commonly referred to as **Normal Maps** or **Height Maps**, however these terms have slightly different meanings which will be explained below. -->
凹凸贴图是一种相对古老的图形技术，但仍然是创建细节逼真的实时图形所需的核心方法之一。凹凸贴图通常也被称为 **法线题图** 或 **高度图**，不过这些术语的含义略有不同，将会在下面解释。

<!-- ## What are Surface Normals? -->
## 什么是表面法线？

<!-- To really explain how normal mapping works, we will first describe what a **“normal”** is, and how it is used in realtime lighting. Perhaps the most basic example would be a model where each surface polygon is lit simply according to the surface angles relative to the light. The surface angle can be represented as a line protruding in a perpendicular direction from the surface, and this direction (which is a vector) relative to the surface is called a **“surface normal”**, or simply, a **normal**. -->
为了真正理解法线贴图的工作原理，需要先清楚什么是 **法线**，以及如何在实时光照中使用法线。也许最基本的例子是，一个模型的多边形表面根据表面相对于光线的角度简单地被点亮。表面角度可以表示为一条垂直于表面并向上突出的线，是一个向量，这条线成为 **表面法线**，或者简单地称为 **法线**。

![Two 12-sided cylinders, on the left with flat shading, and on the right with smoothed shading](http://docs.unity3d.com/uploads/Main/BumpMap2Cylinders.png)
<!-- > Two 12-sided cylinders, on the left with flat shading, and on the right with smoothed shading -->
> 两个 12 面圆柱体，左边是平面着色，右边是平滑着色。


<!-- In the image above, the left cylinder has basic flat shading, and each polygon is shaded according to its relative angle to the light source. The lighting on each polygon is constant across the polygon’s area because the surface is flat. Here are the same two cylinders, with their wireframe mesh visible: -->
在上面的图像中，左边的圆柱体具有基本的平面着色，每个多边形按照其相对于光源的角度被着色。因为表面是平坦的，每个多边形区域大小一样，所以，每个多边形上的光照是恒定的。下面是这两个圆柱体的线框网格：

![Two 12-sided cylinders, on the left with flat shading, and on the right with smoothed shading](http://docs.unity3d.com/uploads/Main/BumpMap2CylindersWire.png)
<!-- > Two 12-sided cylinders, on the left with flat shading, and on the right with smoothed shading -->
> 两个 12 面圆柱体，左边是平面着色，右边是平滑着色。

<!-- The model on the right has the same number of polygons as the model on the left, however the shading appears smooth - the lighting across the polygons gives the appearance of a curved surface. Why is this? The reason is that the **surface normal** at each point used for reflecting light gradually varies across the width of the polygon, so that for any given point on the surface, the light bounces as if that surface was curved and not the flat constant polygon that it really is. -->
右边的模型具有与左边模型相同数量的多边形，但是着色看起来是平滑的 — 覆盖多边形的光照呈现为一张曲线表面。为什么会这样？原因是，沿着多边形，每个点用于反射光线的**表面法线**逐渐变化，因此，对于表面上的任意给定点，就好像它的表面真的弯曲了，而不是平坦的恒定多边形，

<!-- Viewed as a 2D diagram, three of the surface polygons around the outside of the flat-shaded cylinder would look like this: -->
平面着色圆柱体表面上相邻 3 个多边形的 2D 图看起来像下面这样：

![Flat shading on three polygons, viewed as a 2D diagram](http://docs.unity3d.com/uploads/Main/BumpMapFlatShadingDiagram.svg)
<!-- > Flat shading on three polygons, viewed as a 2D diagram -->
> 3 个平面着色多边形的 2D 图。

<!-- The surface normals are represented by the orange arrows. These are the values used to calculate how light reflects off the surface, so you can see that light will respond the same across the length of each polygon, because the surface normals point in the same direction. This gives the “flat shading”, and is the reason the left cylinder’s polygons appear to have hard edges. -->
表面法线用橙色剪头表示。它们的值用于计算表面如何反射光线。在每个多边形上，因为表面法线的方向相同，所以反射同样的光线。所以左侧圆柱体呈现出平面着色，并且具有硬边缘。

<!-- For the smooth shaded cylinder however, the surface normals vary across the flat polygons, as represented here: -->
然而，对于平滑着色圆柱体，表面法线沿着平面多边形逐渐变化，如下所示：

![Smooth shading on three polygons, viewed as a 2D diagram](http://docs.unity3d.com/uploads/Main/BumpMapSmoothShadingDiagram.svg)
<!-- > Smooth shading on three polygons, viewed as a 2D diagram -->
> 3 个平滑着色多边形的 2D 图。


<!-- The normal directions gradually change across the flat polygon surface, so that the shading across the surface gives the impression of a smooth curve (as represented by the greeen line). This does not affect the actual polygonal nature of the mesh, only how the lighting is calculated on the flat surfaces. This apparent curved surface is not really present, and viewing the faces at glancing angles will reveal the true nature of the flat polygons, however from most viewing angles the cylinder appears to have a smooth curved surface. -->
法线方向沿着平面多边形表面逐渐变化，所以看起来像是平滑曲面（用绿线表示）。这并不会影响网格的多边形特质，只会影响表面的光照计算。这种视觉上的曲线表面并不是真正存在，在掠射角观察时将显示平面多边形的本质，尽管如此，从大多数视角查看，这个圆柱体看起来具有平滑的曲线表面。

<!-- Using this basic smooth shading, the data determining the normal direction is actually only stored **per vertex**, so the changing values across the surface are interpolated from one vertex to the next. In the diagram above, the red arrows indicate the stored normal direction at each vertex, and the orange arrows indicate examples of the interpolated normal directions across the area of the polygon. -->
使用这种基本的平滑着色时，决定法线方向的数据实际上只存储**每个定点**，所以，沿着表面变化的法线数据其实是相邻两个定点之间的插值。在上图中，红色剪头表示每个顶点存储的法线方向，黄色剪头表示多边形区域的法线方向插值示例。

<!-- ## What is Normal mapping? -->
## 什么是法线贴图？

<!-- Normal mapping takes this modification of surface normals one step further, by using a texture to store information about how to modify the surface normals across the model. A normal map is an image texture mapped to the surface of a model, similar to regular colour textures, however each pixel in the texture of the normal map (called a **texel**) represents a deviation in surface normal direction away from the “true” surface normal of the flat (or smooth interpolated) polygon. -->
更进一步，用法线贴图表示表面法线的这种变化。法线贴图通过通过一张纹理来存储如何改变表面法线的信息。法线贴图是一张映射到模型表面的图像纹理。有些类似于常规的颜色纹理，不同的是，法线贴图中每个顶点（称为**纹素**）还表示了在表面法线方向上离开平面（或平滑）多边形真实表面的距离。

![Normal mapping across three polygons, viewed as a 2D diagram](http://docs.unity3d.com/uploads/Main/BumpMapBumpShadingDiagram.svg)
<!-- > Normal mapping across three polygons, viewed as a 2D diagram -->
> 3 个相邻多边形的法线贴图的 2D 图。

<!-- In this diagram, which is again a 2D representation of three polygons on the surface of a 3D model, each orange arrow corresponds to a pixel in the normalmap texture. Below, is a single-pixel slice of a normalmap texture. In the centre, you can see the normals have been modified, giving the appearance of a couple of bumps on the surface of the polygon. These bumps would only be apparent due to the way lighting appears on the surface, because these modified normals are used in the lighting calculations. -->
在这张 3D 模型表面的 3 个相邻多边形的 2D 示意图中，每个橙色剪头对应法线贴图中的一个像素。下面是法线贴图的每个像素切片。在中间位置，你可以看到法线被改变了，在多边形表面上呈现出多个凸起。只在当光照出现在表面上时，这些凸起才会显示，因为这些被改变的法线只用于光照计算。

<!-- The colours visible in a raw normal map file typically have a blueish hue, and don’t contain any actual light or dark shading - this is because the colours themselves are not intended to be displayed as they are. Instead, the RGB values of each texel represent the X,Y & Z values of a direction vector, and are applied as a modification to the basic interpolated smooth normals of the polygon surfaces. -->
原始法线贴图文件中的可见颜色呈现蓝色色调，并且不含有任何光照或阴影着色 — 这是因为这些颜色本身并不会显示。相反，每个纹素的 RGB 值表示的是一个方向矢量的 X、Y、Z 值，用于修改多边形表面平滑法线的插值。

![An example normal map texture](http://docs.unity3d.com/uploads/Main/BumpMapTexturePreview.png)
<!-- > An example normal map texture -->
> 一个法线贴图示例。

<!-- This is a simple normal map, containing the bump information for some raised rectangles and text. This normal map can be imported into Unity and placed into Normal Map slot of the Standard Shader. When combined in a material with a colour map (the Albedo map) and applied to the surface of of the cylinder mesh above, the result looks like this: -->
这是一张简单的法线贴图，包含了一些矩形和文本的凹凸信息。这张发现贴图可以导入 Unity，并放入标准着色器的法线贴图插槽。把把它和颜色贴图（即漫反射贴图）一起应用在圆柱体网格的表面上时，效果如下所示：

![The example normal map applied to the surface of the cylinder mesh used above](http://docs.unity3d.com/uploads/Main/BumpMapLitExample.png)
<!-- > The example normal map applied to the surface of the cylinder mesh used above -->
> 把这张法线贴图应用到上面的圆柱体网格表面。

<!-- Again, this does not affect the actual polygonal nature of the mesh, only how the lighting is calculated on the surfaces. This apparent raised lettering and shapes on the surface are not really present, and viewing the faces at glancing angles will reveal the true nature of the flat surface, however from most viewing angles the cylinder now appears to have embossed detail raised off the surface. -->
同样不会影响网格的多边形特质，只是用于计算表面的光照。这种视觉上的字符和形状凸起并不真正存在，在掠射角观察时讲现实平坦表面的本质，尽管如此，在大多数视角查看，这个圆柱体表面呈现出凸起的浮雕细节。

<!-- ## How do I get or make normal maps? -->
## 如何获取或制作法线贴图？

<!-- Commonly, Normal Maps are produced by 3D or Texture artists in conjunction with the model or textures they are producing, and they often mirror the layout and contents of the Albedo map. Sometimes they are produced by hand, and sometimes they are rendered out from a 3D application. -->
通常情况下，法线贴图是同 3D 或纹理设计师制作的模型或纹理一起生成的，通常反应了漫反射贴图的结构和内容。有时也会手工制作，有时由 3D 软件渲染生成。

<!-- How to render normal maps from a 3D application is beyond the scope of this documentation, however the basic concept is that a 3D artist would produce two versions of a model - a very high resolution model containing all detail as polygons, and a lower-res “game ready” model. The high res model would be too detailed to run optimally in a game (too many triangles in the mesh), but it is used in the 3D modelling application to generate the normal maps. The lower-res version of model can then omit the very fine level of geometry detail that is now stored in the normal maps, so that it can be rendered using the normal mapping instead. A typical use case for this would be to show the bumped detail of creases, buttons, buckles and seams on a characters clothing. -->
3D 软件如何渲染法线贴图超出了本文档的范围，但是基本的概念是，3D 设计师会为一个模型生成两个版本 — 一个包含了所有多边形细节的超高分率模型，和一个程序用的低分辨率模型。在游戏中，高分辨率模型含有太多细节（网格中有太多的三角形），以至于不适合在游戏中运行，但是用于在 3D 模型软件中生成法线贴图。低分辨率模型则可以运行在游戏中，并且忽略那些存储在法线贴图中的非常清晰的几何细节，几何细节则用法线贴图渲染。一个典型的用例是，在角色服饰上现实折痕、纽扣、带扣和接缝。

<!-- There are some software packages which can analyse the lighting in a regular photographic texture, and extract a normalmap from it. This works by assuming the original texture is lit from a constant direction, and the light and dark areas are analysed and assumed to correspond with angled surfaces. However, when actually using a bump map, you need to make sure that your Albedo texture does not have lighting from any particular direction in the image - ideally it should represent the colours of the surface with no lighting at all - because the lighting information will be calculated by Unity according to the light direction, surface angle and bump map information. -->
有些软件包可以分析普通摄影纹理中的光照信息，并从中提取法线贴图。工作原理是，假设一束平行光照射到原始纹理上，然后分析浅色和暗色区域，作为法线的角度。不过，在真正使用凹凸贴图时，你需要确保漫反射纹理中不含有任何方向的光照 — 理想情况下，它应该呈现完全无光情况下的表面颜色 — 因为光照信息由 Unity 根据光照角度、表面角度和凹凸贴图计算。

<!-- Here are two examples, one is a simple repeating stone wall texture with its corresponding normal map, and one is a character’s texture atlas with its corresponding normal map: -->
下面是两个示例，一个是简单重复的石墙问题以及对应的法线贴图，一个是角色的纹理图集以及对应的法线贴图。

![A stone wall texture and its corresponding normal map texture](http://docs.unity3d.com/uploads/Main/BumpMapColourMapStoneWallExample.png)
<!-- > A stone wall texture and its corresponding normal map texture -->
> 一个石墙纹理及其对应的法线贴图。

![A character texture atlas, and its corresponding normal map texture atlas](http://docs.unity3d.com/uploads/Main/BumpMapColourMapAstrellaExample.png)
<!-- > A character texture atlas, and its corresponding normal map texture atlas -->
> 一个角色纹理图集及其对应的法线贴图集。

<!-- ## What’s the difference between Bump Maps, Normal Maps and Height Maps? -->
## 凹凸贴图、法线贴图和高度图有什么区别？

<!-- **Normal Maps** and **Height Maps** are both types of Bump Map. They both contain data for representing apparent detail on the surface of simpler polygonal meshes, but they each store that data in a different way. -->
**法线贴图**和**高度图**都属于凹凸贴图类型。它们都含有用于简化多面性网格的表面视觉细节，但是以不同的方式存储数据。

![On the left, a height map for bump mapping a stone wall. On the right, a normal map for bump mapping a stone wall.](http://docs.unity3d.com/uploads/Main/BumpMapHeightMapNormalMapComparison.png)
<!-- > On the left, a height map for bump mapping a stone wall. On the right, a normal map for bump mapping a stone wall. -->
> 左边是映射石墙凹凸信息的高度图，右边是映射石墙凹凸信息的法线贴图。

<!-- Above, on the left, you can see a height map used for bump mapping a stone wall. A height map is a simple black and white texture, where each pixel represents the amount that point on the surface should appear to be raised. The whiter the pixel colour, the higher the area appears to be raised. -->
在左图中，可以看到一张映射石墙凹凸信息的高度图。高度图是一张简单的黑白纹理，每个像素代表了表面上该点应该凸起的高度，像素点颜色越白，该区域看起来更高。

<!-- A normal map is an RGB texture, where each pixel represents the difference in direction the surface should appear to be facing, relative to its un-modified surface normal. These textures tend to have a bluey-purple tinge, because of the way the vector is stored in the RGB values. -->
法线贴图是一张 RGB 纹理，每个像素代表了表面相对于真实法线（垂直）的朝向（夹角）。这些纹理往往是蓝紫色调，因为矢量用 RGB 值存储。

<!-- Modern realtime 3D graphics hardware rely on Normal Maps, because they contain the vectors required to modify how light should appear to bounce of the surface. Unity can also accept Height Maps for bump mapping, but they must be converted to Normal Maps on import in order to use them. -->
现代实时 3D 图形硬件更信赖（依赖）法线贴图，因为法线贴图包含了表面应该如何弹射光线所需的矢量信息。Unity 的凹凸贴图也可以接受高度图，但导入必须转换为法线贴图才能使用。

<!-- ## Why the bluey-purple colours? -->
## 为什么是蓝紫色？

<!-- Understanding this is not vital for using normal maps! It’s ok to skip this paragraph. However if you really want to know: The RGB colour values are used to store the X,Y,Z direction of the vector, with Z being “up” (contrary to Unity’s usual convention of using Y as “up”). In addition, the values in the texture are treated as having been halved, with 0.5 added. This allows vectors of all directions to be stored. Therefore to convert an RGB colour to a vector direction, you must multiply by two, then subtract 1. For example, an RGB value of (0.5, 0.5, 1) or #8080FF in hex results in a vector of (0,0,1) which is “up” for the purposes of normal-mapping - and represents no change to the surface of the model. This is the colour you see in the flat areas of the “example” normal map earlier on this page. -->
对于使用法线贴图，理解为什么并不重要！跳过这一段也没关系。但是，如果你真的想知道的话：RGB 颜色值用于存储矢量的 X、Y、Z，并且 Z 轴向上（与 Unity 使用的 Y 轴向上惯例相关）。此外，纹理中的值被减半处理，并加了 0.5。这样可以存储所有方向的矢量。所以，要将 RGB 值转换为矢量方向，必须乘以 2 然后减 1。例如，RGB 值 (0.5, 0.5, 1) 或者十进制 #8080FF 转换后是 (0,0,1)，表示垂直的法线贴图 — 表示模型表面无变化。这是本页前面演示法线贴图平坦区域时的颜色。

![A normal map using only #8080FF, which translates to a normal vector of 0,0,1 or straight up. This applies no modification to the surface normal of the polygon, and therefore produces no change to the lighting. Any pixels which are different to this colour results in a vectors that point in a different direction - which therefore modify the angle that is used to calculate light bounce at that point.](http://docs.unity3d.com/uploads/Main/BumpMapFlatColour.png)
<!-- > A normal map using only #8080FF, which translates to a normal vector of 0,0,1 or “straight up”. This applies no modification to the surface normal of the polygon, and therefore produces no change to the lighting. Any pixels which are different to this colour results in a vectors that point in a different direction - which therefore modify the angle that is used to calculate light bounce at that point. -->
> 一张只使用 #8080FF 的法线贴图，转换为矢量是 0,0,1，即垂直向上。这张贴图不会改变多边形的表面向量，因此光照不会变化。任何与该颜色不同的像素点，都会导致矢量指向不同的方向 — 改变后的角度用于计算该像素点上反射光的角度。

<!-- A value of (0.43, 0.91, 0.80) gives a vector of (–0.14, 0.82, 0.6), which is quite a steep modification to the surface. Colours like this can be seen in the bright cyan areas of the stone wall normal map at the top of some of the stone edges. The result is that these edges catch the light at a very different angle to the flatter faces of the stones. -->
RGB 值 (0.43, 0.91, 0.80) 给出一个矢量 (–0.14, 0.82, 0.6)，表示表面非常的陡峭。可以在石墙法线贴图的亮青色区域看到这种颜色，对应于一些石头的边缘。相对于石头上较平坦的表面，这些边缘以非常不同的角度捕获光线。

> 译注：rgb(110,232,204)

![The bright cyan areas in the normalmap for these stones show a steep modification to the polygons surface normals at the top edge of each stone, causing them to catch the light at the correct angle.](http://docs.unity3d.com/uploads/Main/BumpMapColourMapStoneWallExample.png)
<!-- > The bright cyan areas in the normalmap for these stones show a steep modification to the polygon’s surface normals at the top edge of each stone, causing them to catch the light at the correct angle. -->
> 这些石头的法线贴图中的亮青色区域显示了对每个石头顶部边缘的多边形表面法线的陡峭修改，使得它们以正确的角度捕获光线。
> 在这些石头的法线图中，亮青色区域对每个石头顶部边缘的多边形表面法线进行了陡峭的修改，使得它们以正确的角度捕获光线。

<!-- Normal maps -->
法线贴图

![A stone wall with no bumpmap effect. The edges and facets of the rock do not catch the directional sun light in the scene.](http://docs.unity3d.com/uploads/Main/BumpMapStoneExampleNoBumps.png)
<!-- > A stone wall with no bumpmap effect. The edges and facets of the rock do not catch the directional sun light in the scene. -->
> 一堵没有凹凸效果的石墙。岩石的边缘和表面不会捕捉场景中的平行太阳光。

![The same stone wall with bumpmapping applied. The edges of the stones facing the sun reflect the directional sun light very differently to the faces of the stones, and the edges facing away.](http://docs.unity3d.com/uploads/Main/BumpMapStoneExampleDay.png)
<!-- > The same stone wall with bumpmapping applied. The edges of the stones facing the sun reflect the directional sun light very differently to the faces of the stones, and the edges facing away. -->
> 应用了凹凸贴图的同一堵石墙。岩石面向太阳的边缘反射的平行太阳光，与岩石的表面和不朝向太阳的边缘，非常不同。

![The same bumpmapped stone wall, in a different lighting scenario. A point light torch illuminates the stones. Each pixel of the stone wall is lit according to how the light hits the angle of the base model (the polygon), adjusted by the vectors in the normal maps. Therefore pixels facing the light are bright, and pixels facing away from the light are darker, or in shadow.](http://docs.unity3d.com/uploads/Main/BumpMapStoneExampleNightTorch.png)
<!-- > The same bumpmapped stone wall, in a different lighting scenario. A point light torch illuminates the stones. Each pixel of the stone wall is lit according to how the light hits the angle of the base model (the polygon), adjusted by the vectors in the normal maps. Therefore pixels facing the light are bright, and pixels facing away from the light are darker, or in shadow. -->
> 不同光照情况下，应用了凹凸贴图的同一堵石墙。一个火把点光源照亮了石头。光线撞击基础模型（多边形）的角度，被法线贴图中的矢量所调整，然后点亮石头的每个像素。因此，面向光源的像素是亮的，背光的像素较暗或在阴影中。

<!-- ## How to import and use Normal Maps and Height Maps -->
## 如何导入和使用法线贴图和高度图

<!-- A normal map can be imported by placing the texture file in your assets folder, as usual. However, you need to tell Unity that this texture is a normal map. You can do this by changing the “Texture Type” setting to “Normal Map” in the import inspector settings. -->
像平常一样，把纹理文件放入 Assets 文件夹，就可以导入法线贴图。不过，你需要告诉 Unity 这个纹理是一张法线贴图。可以在导入资源的检视视图中，把改变『纹理类型』为『法线贴图』。

![](http://docs.unity3d.com/uploads/Main/BumpMapImportInspectorWindow.png)

<!-- To import a black and white heightmap as a normal map, the process is almost identical, except you need to check the “Create from Greyscale” option. -->
把黑白高度图导入为法线贴图的过程，与直接导入法线贴图几乎完全相同，除了需要选中复选框『Create From Greyscale』。

![](http://docs.unity3d.com/uploads/Main/BumpMapImportInspectorGreyscale.png)

<!-- With “Create From Greyscale” selected, a Bumpiness slider will appear in the inspector. You can use this to control how steep the angles in the normalmap are, when being converted from the heights in your heightmap. A low bumpiness value will mean that even sharp contrast in the heightmap will be translated to gentle angles and bumps. A high value will create exaggerated bumps and very high contrast lighting responses to the bumps. -->
选中『Create From Greyscale』后，将出现一个凹凸度滑动器。你可以使用使用这个滑动器，来控制高度图的高度转换为法线贴图中的角度时的陡峭程度。低凹凸度将意味着，即使是高度图中的强烈对比，也将被转换为平缓的角度和凹凸。高凹凸度将创建夸张的凹凸，产生高对比度的光照响应。

![Low and High Bumpiness settings when importing a height map as a normal map, and the resulting effect on the model.](http://docs.unity3d.com/uploads/Main/BumpMapLowAndHighBumpiness.png)
<!-- > Low and High Bumpiness settings when importing a height map as a normal map, and the resulting effect on the model. -->
> 把高度图导入为法线贴图时，凹凸度高低对模型的影响。

<!-- Once you have a normalmap in your assets, you can place it into the Normal Map slot of your Material in the inspector. The Standard Shader has a normal map slot, and many of the older legacy shaders also support normal maps. -->
Assets 文件夹中有了法线贴图后，就可以在检视视图中把它放入材质的法线贴图插槽。标准着色具有一个法线贴图插槽，许多旧的传统着色器也支持法线贴图。

![Placing a normal map texture into the correct slot in a material using the Standard Shader](http://docs.unity3d.com/uploads/Main/BumpMapPutIntoShader.png)
<!-- > Placing a normal map texture into the correct slot in a material using the Standard Shader -->
> 把一张法线法线贴图放入标准着色器材质的正确插槽中。

<!-- If you imported a normalmap or heightmap, and did not mark it as a normal map (By selecting **Texture Type: Normal Map** as described above), the Material inspector will warn you about this and offer to fix it, as so: -->
如果导入了一张法线贴图或高度图，但是没有把它标记为法线贴图（选择**纹理类型：法线贴图**），材质的检视视图将提醒你修正它，像这样：

![The Fix Now warning appears when trying to use a normalmap that has not been marked as such in the inspector.](http://docs.unity3d.com/uploads/Main/BumpMapPutIntoShaderFixNow.png)
<!-- > The “Fix Now” warning appears when trying to use a normalmap that has not been marked as such in the inspector. -->
> 当尝试在法线贴图插槽上使用未标记为法线贴图的纹理时，将显示『立即修复』警告。

<!-- Clicking “Fix Now” has the same effect as selecting **Texture Type: Normal Map** in the texture inspector settings. This will work if your texture really is a normal map. However if it is a greyscale heightmap, it will not automatically detect this - so for heightmaps you must always select the “Create from Greyscale” option in the texture’s inspector window. -->
点击『立即修复』，与在纹理检视视图中选择**纹理类型：法线贴图**，具有相同的效果。如果纹理是一张法线贴图，这么做是有效的。但是，如果它其实是一张灰阶高度图，就无法自动检测到 — 所以对于高度图，你必须总是在纹理的检视视图中选中『Create from Greyscale』。

<!-- ## Secondary Normal Maps -->
## 辅助法线贴图

<!-- You may also notice that there is a second Normal Map slot further down in the Material inspector for the Standard Shader. This allows you to use an additional normal map for creating extra detail. You can add a normal map into this slot in the same way as the regular normal map slot, but the intention here is that you should use a different scale or frequency of tiling so that the two normal maps together produce a high level of detail at different scales. For example, your regular normal map could define the details of panelling on a wall or vehicle, with groves for the panel edges. A secondary normal map could provide very fine bump detail for scratches and wear on the surface which may be tiled at 5 to 10 times the scale of the base normal map. These details could be so fine as to only be visible when examined closely. To have this amount of detail on the base normal map would require the base normal map to be incredibly large, however by combining two at different scales, a high overall level of detail can be achieved with two relatively small normal map textures. -->
你可能还注意到，在标准着色器材质的底部有一个辅助法线贴图插槽。它允许你再使用一张法线贴图来创建额外的细节。你可以把一张法线贴图添加到这个插槽中，就像常规法线贴图的插槽一样，但是，你应该使用不同的尺寸或平铺频率，这样，两张法线贴图在不同的尺度上，共同产生高级细节。例如，常规法线贴图可以定义墙壁或车辆上的镶板细节和镶板边缘的凹槽。辅助贴图可以为表面上划痕和磨损提供非常精细的凸起细节，平铺次数可能是基础法线贴图的 5 到 10 倍。这些细节可能非常惊喜，只有贴脸检查才能看到。为了在基础法线贴图上达到这个量级的细节，基础法线贴图需要非常大才行，尽管如此，通过两张不同尺寸但相对较小的法线贴图，可是实现高级细节。
