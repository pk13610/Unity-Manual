<!-- ## Image effects overview -->
## 屏幕特效概述

<!-- Image effects are [Standard Assets] that provide a quick, simple way to change the look of your game. It’s easiest to think of them like an image-editing application that adds filters to your images (such as Photoshop or even Instagram). -->

屏幕特效是 [标准资源] 的一部分，可以快速简单地改变游戏的视觉效果。最简单的理解方式是，把它们看作是图像编辑程序（例如 Photoshop 或 Instagram），为图像提供了各种过滤器。

[Standard Assets]: http://docs.unity3d.com/Manual/HOWTO-InstallStandardAssets.html
[标准资源]: http://docs.unity3d.com/Manual/HOWTO-InstallStandardAssets.html

<!-- Image effects in Unity work by providing an extra post-processing pass per frame, manipulating the pixel content to alter the image. For this reason, image effects can be resource-intensive, and this should be taken into consideration when adding them to your build. The more image effects you add, and the more heavily you process your images, the lower your framerate is likely to be as a result. -->

Unity 中的屏幕特效为每桢提供额外的后处理通道，通过操纵每个像素来改变图像。因此屏幕特效是资源密集型的，添加它们时应该考虑到这一点。添加的屏幕特效越多，处理图像的任务就越繁重，可能导致帧率越低。

<!-- A number of image effects ship with the Unity Editor; many more are available on the Asset Store and elsewhere online. To learn more about the image effects available in the Unity Editor, see the [Image effect reference] guide. -->

Unity 编辑器提供了许多屏幕特效；更多的屏幕特效在资源商店 Asset Store 和其他在线服务中。要了解 Unity 编辑中可用的屏幕特效，请参阅 [屏幕特效参考页]。

[Image effect reference]: http://docs.unity3d.com/Manual/comp-ImageEffects.html
[屏幕特效参考页]: http://docs.unity3d.com/Manual/comp-ImageEffects.html

<!-- ### See also -->
### 参考

<!-- 
* [Image effect reference](http://docs.unity3d.com/Manual/comp-ImageEffects.html)
* [Writing image effects](http://docs.unity3d.com/Manual/WritingImageEffects.html)
* Tutorial: [Image Effects](http://unity3d.com/learn/tutorials/modules/beginner/live-training-archive/imageeffects-overview?playlist=17102)
 -->
* [屏幕特效参考页](http://docs.unity3d.com/Manual/comp-ImageEffects.html)
* [编写屏幕特效](http://docs.unity3d.com/Manual/WritingImageEffects.html)
* [教程：屏幕特效](http://unity3d.com/learn/tutorials/modules/beginner/live-training-archive/imageeffects-overview?playlist=17102)