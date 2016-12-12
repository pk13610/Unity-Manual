<!-- # Cookies -->
# 灯光纹理

<!-- In theatre and film, lighting effects have long been used to create an impression of objects that don’t really exist in the set. Jungle explorers may appear to be covered in shadows from an imaginary tree canopy. A prison scene often shows the light coming through the barred window, even though the window and indeed the wall are not really part of the set. Though very atmospheric, the shadows are created very simply by placing a shaped mask in between the light source and the action. The mask is known as a cucoloris or cookie for short. Unity lights allow you to add cookies in the form of textures; these provide an efficient way to add atmosphere to a scene. -->

在戏剧和电影中，照明效果被长期用于表现不存在于场景中的物体。丛林探险家可能被覆盖在假想树冠的阴影中。监狱场景经常显示从铁栅栏窗透进来的光，即使窗户和墙壁并不真实存在于场景中。虽然非常有气氛，但是阴影的创建非常之简单，只需要在光源和目标对象之间放置某种形状的遮罩。这个遮罩简称为剪影或 Cookie。Unity 灯光支持以纹理的形式添加 Cookie，从而有效地增强场景气氛。

> 译注：剪影比 Cookie 更直观易懂，不过译者认为更合适的翻译是『灯光纹理』。因此，下文统一使用『灯光问题』。

![A directional light cookie simulating light from a window](https://docs.unity3d.com/uploads/Main/CookieExample.png)
<!-- > A directional light cookie simulating light from a window -->
> 平行光纹理，模拟从窗户透进来的光

<!-- ## Creating a Cookie -->
## 创建灯光纹理

<!-- A cookie is just an ordinary texture but only the alpha/transparency channel is relevant. When you import a cookie, Unity gives you the option to convert the brightness of the image to alpha so it is often easier to design your cookie as a grayscale texture. You can use any available image editor to create a cookie and save it to your project’s Assets folder. -->

灯光纹理只是一张普通的纹理，不过只和 alpha/transparency 通道有关系。当导入一张灯光纹理时，Unity 提供了将图像的亮度转换为 alpha 的选项，因此通常将灯光纹理简单地设计为一张灰度纹理。你可以使用任意图像编辑器生成一张灯光纹理，并保存到项目的 Assets 文件夹下。

![A simple cookie for a window light](https://docs.unity3d.com/uploads/Main/Cookie.png)
<!-- > A simple cookie for a window light -->
> 简单的窗户灯光纹理

<!-- When the cookie is imported into Unity, select it from the Project view and set the Texture Type to Cookie in the inspector. You should also enable Alpha From Grayscale unless you have already designed the image’s alpha channel yourself. -->

导入灯光纹理到 Unity 中时，在项目视图中选中它，并在检视视图中把贴图类型设置为 Cookie。你还应该开启 Alpha From Grayscale，除非你已经设计好了图像的 alpha 通道。

![](https://docs.unity3d.com/uploads/Main/CookieImportSettings.png)

<!-- The Light Type affects the way the cookie is projected by the light. Since a point light projects in all directions, the cookie texture must be in the form of a Cubemap. A spot light should use a cookie with the type set to Spotlight but a directional light can actually use either the Spotlight or Directional options. A directional light with a directional cookie will repeat the cookie in a tiled pattern all over the scene. When a spotlight cookie is used, the cookie will appear just once in the direct path of the “beam” of the light; this is the only case where the position of a directional light is important. -->

选项 Light Type 会影响投射纹理的方式。因为点光源向所有方向发射光，所以纹理贴图必须是 Cubemap 类型。如上图所示，聚光灯使用的纹理类型应该被设置为 Spotlight，而平行光实际上可以使用 Spotlight 或 Directional 类型。使用了 Directional 纹理的平行光将在整个场景上重复平铺纹理。如果使用 Spotlight 类型，则只会在『光束』直线路径上显示一次；唯有在这种情况下，平行光的位置才显得如此重要。

![The window cookie tiled in directional mode](https://docs.unity3d.com/uploads/Main/CookieDirectional.png)
<!-- > The window cookie “tiled” in directional mode -->
> 在平行光模式下『平铺』窗口纹理

<!-- ## Applying a Cookie to a light -->
## 应用纹理到灯光

<!-- When the texture is imported, drag it to the Light’s Cookie property in the inspector to apply it. -->

导入纹理后，在检视视图中，把它拖动到灯光的 Cookie 属性，以应用它。

<!-- The spot light and point light simply scale the cookie according to the size of the cone or sphere. The directional light has an additional option Cookie Size that lets you scale the cookie yourself; the scaling works with both Spotlight and Directional cookie types. -->

聚光灯和点光源按照圆锥体或球体的尺寸简单地缩放灯光纹理。平行光额外提供了一个 Cookie Size 选项，允许你缩放纹理；类型为聚光灯和平行光的灯光纹理都支持缩放。

<!-- ## Uses of Cookies -->
## 使用灯光纹理

<!-- Cookies are often used to change the shape of a light so it matches a detail “painted” in the scene. For example, a dark tunnel may have striplights along the ceiling. If you use standard spot lights for illumination then the beams will have an unexpected round shape but you could use cookies to restrict the lights to a thin rectangle. A monitor screen may cast a green glow onto the face of the character using it but the glow should be restricted to a small box shape. -->

灯光纹理通常用于改变灯光的形状，使之与场景中绘制的某些细节相匹配。例如，黑暗的隧道可能具有沿着天花板的条形灯。如果使用标准的聚光灯模拟，光束将呈现为意想不到的圆形，但是可以使用灯光纹理约束光线，使之呈现为细长的矩形。正在使用监视器屏幕的角色，脸部可能会被投射绿色荧光，但是这种荧光应该被限制为小盒子形状。

<!-- Note that a cookie need not be completely black and white but can also incorporate any grayscale level. This can be useful for simulating dust or dirt in the path of the light. For example, if a game scene takes place in a long abandoned house, you could add atmosphere by using “dirty” cookies with noise on the windows and other light sources. Similarly, car headlight glass usually contains ridges that create “caustic” patterns of slightly lighter and darker areas in the beam; another good use for a cookie. -->

注意，灯光纹理不需要完全是黑白的，它可以包含任意灰度级。这可以用于模拟光线路径上的尘埃和污垢。例如，如果游戏场景位于长期废弃的房间内，可以在窗户和灯光上使用带有噪点的、肮脏的灯光纹理，来营造气氛。类似的，汽车前灯玻璃通常含有脊线（不平整），产生还有较亮和较暗区域的焦散图案；使用灯光纹理可以很好地模拟这种效果。

> 译注：『焦散』是指当光线穿过一个透明物体时，由于对象表面的不平整，使得光线折射并没有平行发生，出现漫折射，投影表面出现光子分散。—— [百度百科](http://baike.baidu.com/view/1252562.htm)
