<!-- # Shadows -->
# 阴影

<!-- Unity’s lights can cast Shadows from an object onto other parts of itself or onto other nearby objects. Shadows add a degree of depth and realism to a scene since they bring out the scale and position of objects that can otherwise look “flat”. -->

Unity 的灯光可以将 **阴影** 从一个游戏对象投射到自身的其他部分或附近的其他游戏对象上。阴影以『扁平』的方式体现游戏对象的尺寸和位置，因此可以为场景添加一定程度的深度和真实感。

![Scene with objects casting shadows](https://docs.unity3d.com/uploads/Main/ShadowIntro.png)
<!-- > Scene with objects casting shadows -->
> 场景视图中的游戏对象正在投射阴影

<!-- ## How do shadows work? -->
## 阴影如何工作？

<!-- Consider the simplest case of a scene with a single light source. Light rays travel in straight lines from that source and may eventually hit objects in the scene. Once a ray has hit an object, it can’t travel any further to illuminate anything else (ie, it “bounces” off the first object and doesn’t pass through). The shadows cast by the object are simply the areas that are not illuminated because the light couldn’t reach them. -->

考虑一种最简单的情况，在场景中只有单个光源。光线从光源出发并沿着直线传播，最终可能会碰撞到场景中的游戏对象。一旦光线碰撞到某个游戏对象，光线将无法继续传播和照亮前方的任何其他游戏对象（例如，光线无法通过第一个游戏对象，并从该游戏对象上反射离开）。游戏对象投射的阴影不过是一些不被照亮的区域，因为光线无法到达这些区域。

![](https://docs.unity3d.com/uploads/Main/ShadowMapIntro.svg)

<!-- Another way to look at this is to imagine a camera at the same position as the light. The areas of the scene that are in shadow are precisely those areas that the camera can’t see. -->

观察阴影的另一个方式是，想象在光源位置处有一个摄像机。场景中的阴影区域恰好是摄像机无法看到的区域。

![A lights eye view of the same scene](https://docs.unity3d.com/uploads/Main/ShadowLightsEyeView.svg)
<!-- > A “light’s eye view” of the same scene -->
> 同一场景中，光源位置的眼睛所看到的视图

<!-- In fact, this is exactly how Unity determines the positions of shadows from a light. The light uses the same principle as a camera to “render” the scene internally from its point of view. A depth buffer system, as used by scene cameras, keeps track of the surfaces that are closest to the light; surfaces in a direct line of sight receive illumination but all the others are in shadow. The depth map in this case is known as a **Shadow Map** (you may find the [Wikipedia Page] on shadow mapping useful for further information). -->

事实上，这正是 Unity 确定阴影位置的方式。光源使用与摄像机相同的原理，来『渲染』光源视角范围内的场景。光源像摄像机一样使用一个深度缓存系统，保持对面向光源的表面的跟踪；只有位于视线中的表面接受光照，所有其他表面则都在阴影中。这里的深度映射称为 **阴影映射**（你可以在阴影映射的 [维基百科页] 中找到更多信息）。

[Wikipedia Page]: http://en.wikipedia.org/wiki/Shadow_mapping
[维基百科页]: http://en.wikipedia.org/wiki/Shadow_mapping

<!-- The sections below give details on casting shadows from Unity’s Light objects. -->

下面的章节将详细介绍 Unity 灯光对象投射阴影的细节。
