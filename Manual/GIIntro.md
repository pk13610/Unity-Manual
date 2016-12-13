<!-- # Global Illumination -->
# 全局光照

<!-- **Global Illumination** (GI) is a system that models how light is bounced off of surfaces onto other surfaces (indirect light) rather than being limited to just the light that hits a surface directly from a light source (direct light). Modelling indirect lighting allows for effects that make the virtual world seem more realistic and connected, since objects affect each other’s appearance. One classic example is ‘color bleeding’ where, for example, sunlight hitting a red sofa will cause red light to be bounced onto the wall behind it. Another is when sunlight hits the floor at the opening of a cave and bounces around inside so the inner parts of the cave are illuminated too. -->

**全局光照**（Global Illumination，GI）是一套模拟系统，不仅模拟光线如何直接照射到表面（直接光），还可以模拟光线如何从一个表面弹射到其他表面（间接光）。对间接光的模拟使虚拟世界的效果看起来更加真实和连贯，因为对象彼此之间会相互影响外观。一个典型的例子是『色溢』（颜色溢出），例如，太阳光照射到红色沙发上，红色光将被弹射到后面的墙上。另一个例子是，当太阳光照射到洞穴口的地板上时，光线将在洞穴的内部弹射，所以洞穴的内部也被照亮。

![](https://docs.unity3d.com/uploads/Main/GIExamplePic.png)

<!-- Global illumination in the Scene View. Note the subtle effect of indirect lighting. -->

场景视图中的全局光照。注意微妙的间接光照效果。

<!-- ## GI concepts -->
## GI 概念

<!-- Traditionally, video games and other realtime graphics applications have been limited to direct lighting, while the calculations required for indirect lighting were too slow so they could only be used in non-realtime situations such as CG animated films. A way for games to work around this limitation is to calculate indirect light only for objects and surfaces that are known ahead of time to not move around (that are static). That way the slow computation can be done ahead of time, but since the objects don’t move, the indirect light that is pre-calculated this way will still be correct at runtime. Unity supports this technique, called Baked GI (also known as Baked Lightmaps), which is named after “the bake” - the process in which the indirect light is precalculated and stored (baked). In addition to indirect light, Baked GI also takes advantage of the greater computation time available to generate more realistic soft shadows from area lights and indirect light than what can normally be achieved with realtime techniques. -->

传统的视频游戏和其他实时图形应用程序仅限于直接光照，因为间接光照所需的计算太慢了，因此它们只能用于非实时情况，例如电影动画 CG。饶过这个限制的方法是，只为提前就知道不会移动（静态）的对象和表面计算间接光照。这样，慢速计算被提前进行计算，因为这些对象不会移动，所以预计算的间接光照在运行时仍然是正确的。Unity 支持这种技术，称为烘培 GI（也被称为烘培光照贴图），预先计算间接光照并存储的过程称为『烘培』。烘培 GI 利用大量计算时间，可以有效地生成来自区域光和间接光的柔和阴影，并且比通常用实时技术生成的更加逼真。

<!-- Additionally, Unity 5.0 adds support for a new technique called Precomputed Realtime GI. It still requires a precomputation phase similar to the bake mentioned above, and it is still limited to static objects. However it doesn’t just precompute how light bounces in the scene at the time it is built, but rather it precomputes all possible light bounces and encodes this information for use at runtime. So essentially for all static objects it answers the question “if any light hits this surface, where does it bounce to?” Unity then saves this information about which paths light can propagate by for later use. The final lighting is done at runtime by feeding the actual lights present into these previously computed light propagation paths. -->

此外，Unity 5.0 增加了一种名为预计算实时 GI 的新技术。它仍然需要类似上述烘培的预计算阶段，并且仍然仅限于静态对象。不过，它不仅仅预计算光线如何在场景中弹射，而且预计算所有可能的光线弹射，并对这些信息进行编码，以便在运行时使用。所以，对于所有静态对象，它回答了『如果任意光线照射到表面，将向哪里弹射？』这一问题。然后，Unity 保存光线传播路径的信息，供以后使用。在运行时，通过反馈真实存在的灯光到之前计算的光线传播路径中，完成最终的光照。

<!-- This means that the number and type of lights, their position, direction and other properties can all be changed and the indirect lighting will update accordingly. Similarly it’s also possible to change material properties of objects, such as their color, how much light they absorb or how much light they emit themselves. -->

这意味，灯光的数量、类型、位置、方向和其他属性都可以改变，并且间接照明将相应地改变。类似地，可以改变对象的材质属性，例如颜色、反射光的数量或自发光的数量。

<!-- While Precomputed Realtime GI also results in soft shadows, they will typically have to be more coarse-grained than what can be achieved with Baked GI unless the scene is very small. Also note that while Precomputed Realtime GI does the final lighting at runtime, it does so iteratively over several frames, so if a big a change is done in the lighting, it will take more frames for it to fully take effect. And while this is fast enough for realtime applications, if the target platform has very constrained resources it may be better to to use Baked GI for better runtime performance. -->

虽然预计算实时 GI 也可以产生柔和阴影，但是通常比烘培 GI 实现的更粗糙，除非场景非常小。还需要注意的是，尽管预计算实时 GI 在运行时完成最终光照，但是它需要在多个桢上迭代地执行，所以，如果光照场景中发生了大量改变，将需要更多的桢才能完全生效。虽然这对于实时应用程序来说已经足够快了，但是如果目标平台的计算资源非常有限，最好使用烘培 GI 来获得更好的运行时性能。

<!-- ## Limitations of GI -->
## GI 的局限性

<!-- Both Baked GI and Precomputed Realtime GI have the limitation that only static objects can be included in the bake/precomputation - so moving objects cannot bounce light onto other objects and vice versa. However they can still pick up bounce light from static objects using Light Probes. Light Probes are positions in the scene where the light is measured (probed) during the bake/precomputation, and then at runtime the indirect light that hits non-static objects is approximated using the values from the probes that the object is closest to at any given moment. So for example a red ball that rolls up next to a white wall would not bleed its color onto the wall, but a white ball next to a red wall could pick up a red color bleed from the wall via the light probes. -->

烘培 GI 和预计算实时 GI 都有其局限性，即只有静态对象才能被包含在烘培和预计算过程中 —— 因此移动的对象不能弹射光线到其他对象上，反之亦然。不过，移动对象仍然可以接收使用了光照探针的静态对象的弹射光。在烘培和预计算过程中，会测量（探测）探针位置的光照，并且，在运行时的任意时刻，照射到非静态对象的间接光用最靠近它的探针的值近似模拟。因此，一个靠近白色墙壁的红球，不会溢出它的颜色到墙壁上，但是，一个靠近红色墙壁的白球，可以通过光照探针接收墙壁溢出的红光。

> 译注：球体是运动对象，墙壁是静态对象。

<!-- ## Examples of GI effects -->
## GI 效果示例

<!-- 
* Changing the direction and color of a directional light to simulate the effect of the sun moving across the sky. By modifying the skybox along with the directional light it is possible to create a realistic time-of-day effect that is updated at runtime. (In fact the new built-in procedural skybox makes it easy to do this).
* As the day progresses the sunlight streaming in through a window moves across the floor, and this light is realistically bounced around the room and onto the ceiling. When the sunlight reaches a red sofa, the red light is bounced onto the wall behind it. Changing the color of the sofa from red to green will result in the color bleed on the wall behind it turning from red to green too.
* Animating the emissiveness of a neon sign’s material so it starts glowing onto its surroundings when it is turned on.
 -->
* 通过改变平行光的方向和颜色，以模拟太阳在天空中移动的效果。同时修改天空盒和平行光，可以逼真地创建在运行时更新的昼夜效果。（事实上，内置新增的过程式天空盒很容易做到这种效果。）
* 随着一天时间的流逝，穿过窗户的阳光在地板上移动，并且光线在房间内和天花板上逼真地弹射。当阳光到达红色沙发时，红光被弹射到它后面的墙壁上。把沙发的颜色从红色改为绿色，将导致它后面的墙壁也从红色变为绿色。
* 为霓虹灯材质的自发光属性添加动画，这样当它被打开时，将照亮周围的环境。

<!-- The following sections go into detail about how to use this feature. -->
下面的章节详细介绍了如何使用全局光照功能。
