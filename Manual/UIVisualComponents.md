<!-- # Visual Components -->
# 视觉组件

<!-- With the introduction of the UI system, new Components have been added that will help you create GUI specific functionality. This section will cover the basics of the new Components that can be created. -->

随着 UI 系统被引入，Unity 增加了一些新组件，用于帮助创建特定功能的 GUI。这节将介绍可以这些新组件的基础知识。

<!-- ## Text -->
## 文本 Text

![](https://docs.unity3d.com/uploads/Main/UI_TextInspector.png)

<!-- The **Text** component, which is also known as a Label, has a Text area for entering the text that will be displayed. It is possible to set the font, font style, font size and whether or not the text has rich text capability. -->

**文本 Text** 组件（也称为标签 Label）具有一个文本区域，用于输入将要显示的文本。可以设置字体、字体样式、字体大小，以及是否具有富文本功能。

<!-- There are options to set the alignment of the text, settings for horizontal and vertical overflow which control what happens if the text is larger than the width or height of the rectangle, and a Best Fit option that makes the text resize to fit the available space. -->

提供了用于设置文本对齐的选项，用于水平或垂直溢出的设置（控制了文本大于矩形的宽度或高度时如何显示），和 `Best Fit` 选项（调整文本大小以适配可用空间）。

<!-- ## Image -->
## 图像 Image

![](https://docs.unity3d.com/uploads/Main/UI_ImageInspector.png)

<!-- An Image has a Rect Transform component and an **Image** component. A sprite can be applied to the Image component under the Target Graphic field, and its colour can be set in the Color field. A material can also be applied to the Image component. The Image Type field defines how the applied sprite will appear, the options are: -->

图像 Image 具有一个矩形变换组件 Rect Transform 和一个 **图像 Image** 组件。图片精灵可以被应用于图像组件的 `Target Graphic` 域，颜色可以在 `Color` 域设置。材质也可以应用于图像组件。`Image Type` 域定义了图像精灵的显示方式，选项如下：

<!-- 
* Simple - Scales the whole sprite equally.
* Sliced - Utilises the 3x3 sprite division so that resizing does not distort corners and only the center part is stretched.
* Tiled - Similar to Sliced, but tiles (repeats) the center part rather than stretching it. For sprites with no borders at all, the entire sprite is tiled.
* Filled - Shows the sprite in the same way as Simple does except that it fills in the sprite from an origin in a defined direction, method and amount.
 -->
* 简单 `Simple` - 等比缩放整个图像精灵。
* 分割 `Sliced` - 使用 3x3 精灵分割，调整大小不会使边角变形，只会伸展中心部分。
* 平铺 `Tiled` - 类似于 `Sliced`，但是平铺（重复）中心部分，而不是伸展。对于没有边框的图像精灵，整个图像精灵被平铺。
* 填充 `Filled` - 以与 `Simple` 相同的方式显示图像精灵，但是从一个远点开发，以定义好的方向、方法和数量，填充图像精灵。

<!-- The option to Set Native Size, which is shown when Simple or Filled is selected, resets the image to the original sprite size. -->

当选中 `Simple` 或 `Filled` 时，显示选项 `Set Native Size`，重置图像为原始大小。

<!-- Images can be imported as **UI sprites** by selecting Sprite( 2D / UI) from the ‘Texture Type’ settings. Sprites have extra import settings compared to the old GUI sprites, the biggest difference is the addition of the sprite editor. The sprite editor provides the option of **9-slicing** the image, this splits the image into 9 areas so that if the sprite is resized the corners are not stretched or distorted. -->

导入图像时，为选项 `Texture Type` 选择 `Sprite( 2D / UI)`，图像将作为 **UI 精灵** 导入。相对于旧版的 GUI 精灵，UI 精灵具有额外的导入设置，最大的不同是增加了图像精灵编辑器。图像精灵编辑器提供了 **9-slicing** 选项，将图像分割成 9 个区域，当图像调整大小时，边角不会拉升或变形。

<!-- ## Raw Image -->
## 原始图像 Raw Image

<!-- The Image component takes a sprite but **Raw Image** takes a texture (no borders etc). Raw Image should only be used if necessary otherwise Image will be suitable in the majority of cases. -->

图像组件 Image 接受一张图像精灵，而 **原始图像 Raw Image** 接受一张纹理（无边框等）。原始图像只应该在必要时使用，大多数情况下，图像更适合。

<!-- ## Mask -->
## 遮罩 Mask


<!-- A Mask is not a visible UI control but rather a way to modify the appearance of a control’s child elements. The mask restricts (ie, “masks”) the child elements to the shape of the parent. So, if the child is larger than the parent then only the part of the child that fits within the parent will be visible. -->

遮罩 Mask 不是可见的 UI 控件，而是一种修改控件子元素外观的方法。遮罩限制（则遮盖）子元素为父元素形状。因此，如果子元素大于父元素，那么只有位于父元素中的部分将是可见的。

<!-- ## Effects -->
## 特效 Effects

<!-- Visual components can also have various simple effects applied, such as a simple drop shadow or outline. See the [Effects] reference page for more information. -->

视觉组件还可以具有各种简单特效，例如简单的阴影或轮廓。更多信息请参阅 [Effects] 参考页。

[Effects]: https://docs.unity3d.com/Manual/comp-Effects.html