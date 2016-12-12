<!-- # Using Lights -->
# 使用灯光

<!-- Lights are very easy to use in Unity - you simply need to create a light of the desired type (eg, from the menu **GameObject > Light > Point Light**) and place it where you want it in the scene. If you enable scene view lighting (the “sun” button on the toolbar) then you can see a preview of how the lighting will look as you move light objects and set their parameters. -->

Unity 中的灯光非常容易使用 —— 你只需要创建一个所需类型的灯光（例如，通过菜单 **GameObject > Light > Point Light**），并将其放置在场景中合适的位置。如果开启了场景视图光照（工具栏上的『太阳』按钮），当移动灯光对象和设置它们的参数时，就可以预览光照的效果。

![](http://docs.unity3d.com/uploads/Main/LightUsageSceneView.svg)

<!-- A directional light can generally be placed anywhere in the scene (except when it is using a Cookie) with the forward/Z axis indicating the direction. A spot light also has a direction but since it has a limited range, its position does matter. The shape parameters of spot, point and area lights can be adjusted from the inspector or by using the lights’ Gizmos directly in the scene view. -->

平行光通常可以放置在场景中的任意位置（除非使用了灯光纹理），并且使用 Z 轴作为它的方向。聚光灯也具有方向，但是范围有限，而且它的位置很重要。可以在检视视图中调整聚光灯、点光源和区域光的形状，或者，直接在场景视图中调整灯光的线框。

![A spot light with Gizmos visible](http://docs.unity3d.com/uploads/Main/LightUsageSpotGizmo.png)
<!-- > A spot light with Gizmos visible -->
> 点光源的线框

<!-- ## Guidelines for Placing Lights -->
## 灯具放置指南

<!-- A directional light often represents the sun and has a significant effect on the look of a scene. The direction of the light should point slightly downwards but you will usually want to make sure that it also makes a slight angle with major objects in the scene. For example, a roughly cubic object will be more interestingly shaded and appear to “pop” out in 3D much more if the light isn’t coming head-on to one of the faces. -->

平行光通常代表太阳，对场景的外观具有显著影响。平行光的方向应该稍微朝下，但是通常需要确保它与场景中的主要对象成微小的角度。例如，一个粗糙的立方体对象，如果光线不是正面直射到某个面上，立方体的阴影将更加有趣，在 3D 中看起来更加突出。

<!-- Spot lights and point lights usually represent artificial light sources and so their positions are usually determined by scene objects. One common pitfall with these lights is that they appear to have no effect at all when you first add them to the scene. This happens when you adjust the range of the light to fit neatly within the scene. The range of a light is the limit at which the light’s brightness dims to zero. If you set, say, a spot light so the base of the cone neatly lands on the floor then the light will have little or no effect unless another object passes underneath it. If you want the level geometry to be illuminated then you should expand point and spot lights so they pass through the walls and floors. -->

聚光灯和点光源通常代表人造光源，所以它们的位置通常由场景对象决定。一个常见陷阱是，当把这些灯光第一次添加到场景中时，它们似乎没有任何效果。当你调整灯光的范围以覆盖整个场景时，才会有有效果。在灯光范围的边界位置，灯光亮度衰减为 0。例如，如果把聚光灯的椎体底部设置在天花板上，那么这个灯光将很少有或没有效果，除非另一个物体从它下面经过。如果想要照亮水平物体，你需要扩大点光源和聚光灯，使它们的范围穿过墙壁和地板。

<!-- ## Color and Intensity -->
## 颜色和强度

<!-- A light’s color and intensity (brightness) are properties you can set from the inspector. The default intensity and white color are fine for “ordinary” lighting that you use to apply shading to objects but you might want to vary the properties to produce special effects. For example, a glowing green forcefield might be bright enough to bathe surrounding objects in intense green light; car headlights (especially on older cars) typically have a slight yellow color rather than brilliant white. These effects are most often used with point and spot lights but you might change the color of a directional light if, say, your game is set on a distant planet with a red sun. -->

灯光具有颜色和强度属性，可以在检视视图中设置。默认的强度和白色适用于普通照明，可以为对象着色，不过为了生成特殊效果，你可能需要改变这些属性。例如，一个发光的绿色力场可能非常明亮，让周围的对象沐浴在绿色光芒中；汽车前灯（特别是在旧车上）的光通常具有轻微的黄色，而不是亮白色。这些效果最常见于点光源和聚光灯，但是，如果游戏被设置在一个有红色太阳的遥远星球上，你可能会改变平行光的颜色。
