<!-- # Types of light -->
# 灯光类型

<!-- This section details the many different ways of creating light in Unity. -->

本节详细介绍 Unity 中创建灯光的多种不同方法。

<!-- ## Point lights -->
## 点光源

<!-- A point light is located at a point in space and sends light out in all directions equally. The direction of light hitting a surface is the line from the point of contact back to the center of the light object. The intensity diminishes with distance from the light, reaching zero at a specified range. Light intensity is inversely proportional to the square of the distance from the source. This is known as ‘inverse square law’ and is similar to how light behaves in the real world. -->

点光源位于空间中的某个点，均匀地向所有方向发射光。光击中表面的方向是一条从灯光对象中心到接触点的直线。强度随着与灯光的距离而衰减，在指定范围衰减为 0。光的强度与目标对象到光源的距离的平方成反比。这被称为『平方反比定律』，类似于光在真实世界中的行为。

![](https://docs.unity3d.com/uploads/Main/PointLightDiagram.svg)

<!-- Point lights are useful for simulating lamps and other local sources of light in a scene. You can also use them to make a spark or explosion illuminate its surroundings in a convincing way. -->

点光源可以用于模拟场景中的灯具或其他本地光源。可以使火花或爆炸以逼真的方式照亮周围的环境。

![Effect of a Point Light in the scene](https://docs.unity3d.com/uploads/Main/Light-Point.png)
<!-- > Effect of a Point Light in the scene -->
> 点光源在场景中的效果

<!-- ## Spot lights -->
## 聚光灯

<!-- Like a point light, a spot light has a specified location and range over which the light falls off. However, the spot light is constrained to an angle, resulting in a cone-shaped region of illumination. The center of the cone points in the forward (Z) direction of the light object. Light also diminishes at the edges of the spot light’s cone. Widening the angle increases the width of the cone and with it increases the size of this fade, known as the ‘penumbra’. -->

聚光灯类似于点光源，具有特定的位置和方位，并且逐渐衰减。不过，聚光灯被限制在一定的角度范围内，产生锥形的照明区域。椎体的中心指向灯光对象的前方（Z 轴）。光的强度沿着聚光灯椎体的边缘衰减。扩大角度会增加椎体的宽度，并增加渐变的幅度（即加剧衰减），被称为『半影锥』。

![](https://docs.unity3d.com/uploads/Main/SpotLightDiagram.svg)

<!-- Spot lights are generally used for artificial light sources such as flashlights, car headlights and searchlights. With the direction controlled from a script or animation, a moving spot light will illuminate just a small area of the scene and create dramatic lighting effects. -->

聚光灯通常用于人造光源，例如手电筒、汽车前灯和探照灯。通过用脚本或动画控制聚光灯的方向，一个移动的聚光灯将照亮场景的小块区域，产生戏剧性的照明效果。

![Effect of a Spot Light in the scene](https://docs.unity3d.com/uploads/Main/Light-Spot.png)
<!-- > Effect of a Spot Light in the scene -->
> 聚光灯在场景中的效果

<!-- ## Directional lights -->
## 平行光

<!-- Directional lights are very useful for creating effects such as sunlight in your scenes. Behaving in many ways like the sun, directional lights can be thought of as distant light sources which exist infinitely far away. A directional light does not have any identifiable source position and so the light object can be placed anywhere in the scene. All objects in the scene are illuminated as if the light is always from the same direction. The distance of the light from the target object is not defined and so the light does not diminish. -->

平行光用于在场景中对于创建类似阳光的效果。在许多方面与太阳相似，可以把平行光认为是位于无限遥远距离的光源。平行光没有具体的来源，因此平行光对象可以放置在场景中的任意位置。场景中的所有对象都被照亮，就好像光总是来自相同的方向。因为无法定义从目标对象到灯光对象的距离，所以光的强度不会衰减。

![](https://docs.unity3d.com/uploads/Main/DirectionalLightDiagram.svg)

<!-- Directional lights represent large, distant sources that come from a position outside the range of the game world. In a realistic scene, they can be used to simulate the sun or moon. In an abstract game world, they can be a useful way to add convincing shading to objects without exactly specifying where the light is coming from. -->

平行光代表了游戏世界之外巨大而遥远的光源。在拟真场景中，它可以用来模拟太阳或月亮。在抽象的游戏世界中，它可以为对象添加逼真的阴影，而不需要精确指定光来自哪里。

![Effect of a Directional Light in the scene](https://docs.unity3d.com/uploads/Main/Light-Direct.png)
<!-- > Effect of a Directional Light in the scene -->
> 平行光在场景中的效果


<!-- By default, every new Unity scene contains a Directional Light. In Unity 5, this is linked to the procedural sky system defined in the Environment Lighting section of the Lighting Panel (Lighting>Scene>Skybox). You can change this behaviour by deleting the default Directional Light and creating a new light or simply by specifying a different GameObject from the ‘Sun’ parameter (Lighting>Scene>Sun). Rotating the default Directional Light (or ‘Sun’) causes the ‘Skybox’ to update. With the light angled to the side, parallel to the ground, sunset effects can be achieved. Additionally, pointing the light upwards causes the sky to turn black, as if it were nighttime. With the light angled from above, the sky will resemble daylight. If the Skybox is selected as the ambient source, Ambient Lighting will change in relation to these colors. -->

每个新建的 Unity 场景默认包含一个平行光。在 Unity 5 中，平行光与天空系统相关联，定义在光照面板的环境光照部分（Lighting>Scene>Skybox）。通过删除默认的平行光并新建一个平行光，或者为 Sun 参数（Lighting>Scene>Sun）简单地指定一个不同的游戏对象，你可以改变这种默认行为。旋转默认的平行光（或 Sun）将更新『天空盒』。调整平行光的角度，使之与地面平行，可以实现日落效果。将平行光指向上方，会使天空变黑，就像是在夜间一样。倾斜平行光，天空将类似于白天。如果天空盒被选择为环境光源，环境光照将按照平行光的颜色改变。

<!-- ## Area lights -->
## 区域光

<!-- An Area Light is defined by a rectangle in space. Light is emitted in all directions uniformly across their surface area, but only from one side of the rectangle. There is no manual control for the range of an Area Light, however intensity will diminish at inverse square of the distance as it travels away from the source. Since the lighting calculation is quite processor-intensive, area lights are not available at runtime and can only be baked into lightmaps. -->

区域光由空间中的一个矩形定义。沿着它的表面，均匀地向所有方向发射光，但是只从矩形的一面发射。无法手动控制区域光的范围，不过，随着光线远离光源，强度将按照距离的平方衰减。因为光照计算需要大量的处理器资源，因此区域光在运行时是不可用的，只能烘培到光照贴图中。

![](https://docs.unity3d.com/uploads/Main/AreaLightDiagram.svg)

<!-- Since an area light illuminates an object from several different directions at once, the shading tends to be more soft and subtle than the other light types. You might use it to create a realistic street light or a bank of lights close to the player. A small area light can simulate smaller sources of light (such as interior house lighting) but with a more realistic effect than a point light. -->

区域光同时从多个不同方向照亮物体，产生的阴影往往比其他类型的灯光更加柔和细腻。可以用它创建逼真的路灯或玩家附近的一排灯。小型区域光可以模拟更小的光源（例如室内照明），但是具有比点光源更真实的效果。

![Light is emitted across the surface of an Area Light producing a diffuse light with soft shadowing.](https://docs.unity3d.com/uploads/GlobalIllumination/AreaLights.png)
<!-- > Light is emitted across the surface of an Area Light producing a diffuse light with soft shadowing. -->
> 沿着区域光的表面发射光，产生具有柔和阴影的漫射光。

<!-- ## Emissive materials -->
## 自发光材质

![](https://docs.unity3d.com/uploads/GlobalIllumination/EmissiveMaterial.png)

<!-- Like area lights, emissive materials emit light across their surface area. They contribute to bounced light in your scene and associated properties such as color and intensity can be changed during gameplay. Whilst area lights are not supported by Precomputed Realtime GI, similar soft lighting effects in realtime are still possible using emissive materials. -->

自发光材质像区域光一样沿着它的表面发射光。用于组成场景中的弹射光，并且可以在游戏过程中修改相关的属性，例如颜色和强度。尽管预计算实时 GI 不支持区域光，不过，使用自发光材质仍然可以实时渲染出类似的柔和光照效果。

<!-- ‘Emission’ is a property of the Standard Shader which allows static objects in our scene to emit light. By default the value of ‘Emission’ is set to zero. This means no light will be emitted by objects assigned materials using the Standard Shader. -->

`Emission` 是标准着色器的一个属性，允许场景中的静态对象发射光。`Emission` 默认被设置为 0。这意味着使用了该材质着色器的对象不会发射光。

<!-- There is no range value for emissive materials but light emitted will again falloff at a quadratic rate. Emission will only be received by objects marked as ‘Static’ or “Lightmap Static’ from the Inspector. Similarly, emissive materials applied to non-static, or dynamic geometry such as characters will not contribute to scene lighting. -->

自发光材质没有范围值，但是发射的光将以距离的平方衰减。发射的光只会被标记为『静态』或『静态光照贴图』的对象接收。类似地，如果自发光材质被应用到非静态对象或运动对象（例如角色）上，将不会影响环境光照。

<!-- However, materials with an emission above zero will still appear to glow brightly on-screen even if they are not contributing to scene lighting. This effect can also be produced by selecting ‘None’ from the Standard Shader’s ‘Global Illumination’ Inspector property. Self-illuminating materials like these are a useful way to create effects such as neons or other visible light sources. -->

在场景中，`Emission` 大于 0 的材质将明亮地发光，即使它并不影响环境光照。在检视视图中，为标准着色器的 `Global Illumination` 属性选择 `None`，也可以产生这样的效果。像这样的自发光材质可以用于创建诸如霓虹灯或其他可见光源等效果。

<!-- Emissive materials only directly affect static geometry in your scene. If you need dynamic, or non-static geometry - such as characters, to pick up light from emissive materials, Light Probes must be used. -->

自发光材质只会直接影响场景中的静态对象。如果需要使运动的或非静态的对象（例如角色）也接收来自自发光材质的光，必须使用光照探针。

<!-- ## Ambient light -->
## 环境光

<!-- Ambient light is light that is present all around the scene and doesn’t come from any specific source object. It can be an important contributor to the overall look and brightness of a scene. -->

环境光是指存在于整个场景中的光，不来自于任何特定光源对象。它是场景整体外观和亮度的重要贡献者。

<!-- Ambient light can be useful in a number of cases, depending upon your chosen art style. An example would be bright, cartoon-style rendering where dark shadows may be undesirable or where lighting is perhaps hand-painted into textures. Ambient light can also be useful if you need to increase the overall brightness of a scene without adjusting individual lights. -->

环境光在许多情况下是有用的，不过这取决于你选择的艺术风格。举个例子，明亮的、卡通风格的渲染可能不需要黑暗的阴影，或者光照可能被手绘成纹理。如果需要在不调整单个灯光的情况下增加场景的整体亮度，可以直接调整环境光。

<!-- Ambient light settings can be found in the [Lighting window]. -->

环境光的设置可以在 [光照视图] 中找到。

[Lighting window]: https://docs.unity3d.com/Manual/GlobalIllumination.html
[光照视图]: https://docs.unity3d.com/Manual/GlobalIllumination.html
