Unity Manual > Graphics > Graphics Overview > Lighting > Directional Light Shadows

# Directional Light Shadows

A directional light typically simulates sunlight and a single light can illuminate the whole of a scene. This means that the shadow map will often cover a large portion of the scene at once and this makes the shadows susceptible to a problem called “perspective aliasing”. Simply put, perspective aliasing means that shadow map pixels seen close to the camera look enlarged and “chunky” compared to those farther away.

![Shadows close to camera show perspective aliasing](http://docs.unity3d.com/uploads/Main/DirShadowAliasing.svg)
> Shadows close to camera show perspective aliasing

Perspective aliasing is less noticeable when you are using soft shadows and a high resolution for the shadow map. However, using these features will increase demands on the graphics hardware and so framerate might suffer.

## Shadow Cascades

The reason perspective aliasing occurs is that different areas of the shadow map are scaled disproportionately by the camera’s perspective. The shadow map from a light needs to cover only the part of the scene visible to the camera, which is defined by the camera’s [view frustum](http://docs.unity3d.com/Manual/UnderstandingFrustum.html). If you imagine a simple case where the directional light comes directly from above, you can see the relationship between the frustum and the shadow map.

![](http://docs.unity3d.com/uploads/Main/ShadMapFrustumDiagram.svg)

The distant end of the frustum is covered by 20 pixels of shadow map while the near end is covered by only 4 pixels. However, both ends appear the same size onscreen. The result is that the resolution of the map is effectively much less for shadow areas that are close to the camera. (Note that in reality, the resolution is much higher than 20x20 and the map is usually not perfectly square-on to the camera.)

Using a higher resolution for the whole map can reduce the effect of the “chunky” areas but this uses up more memory and bandwidth while rendering. You will notice from the diagram, though, that a large part of the shadow map is “wasted” at the near end of the frustum because it will never be seen; also shadow resolution far away from the camera is likely to be too high. It is possible to split the frustum area into two zones based on distance from the camera. The zone at the near end can use a separate shadow map at a reduced size (but with the same resolution) so that the number of pixels is evened out somewhat.

![](http://docs.unity3d.com/uploads/Main/ShadMapCascadeDiagram.svg)

These staged reductions in shadow map size are known as **cascaded shadow maps** (sometimes called “Parallel Split Shadow Maps”). From the [Quality Settings](http://docs.unity3d.com/Manual/class-QualitySettings.html), you can set zero, two or four cascades for a given quality level.

![](http://docs.unity3d.com/uploads/Main/ShadCascadeQualSettings.svg)

The more cascades you use, the less your shadows will be affected by perspective aliasing, but increasing the number does come with a rendering overhead. However, this overhead is still less than it would be if you were to use a high resolution map across the whole shadow.

![Shadow from the earlier example with four cascades](http://docs.unity3d.com/uploads/Main/ShadCascade4.png)

> Shadow from the earlier example with four cascades

**Note:** on mobile platforms, shadow cascades are not available for directional lights.

## Shadow Distance

Shadows from objects tend to become less noticeable the farther the objects are from the camera; they appear smaller onscreen and also, distant objects are usually not the focus of attention. Unity lets you take advantage of this effect by providing a Shadow Distance property in the [Quality Settings](http://docs.unity3d.com/Manual/class-QualitySettings.html). Objects beyond this distance (from the camera) cast no shadows at all, while the shadows from objects approaching this distance gradually fade out.

Setting the shadow distance as low as possible will help improve rendering performance since distant objects will not need to be rendered into the shadow map at all. Additionally, the scene will often actually look better with distant shadows removed. Getting the shadow distance right is especially important for performance on mobile platforms since they don’t support shadow cascades.

## Visualising Shadow Parameter Adjustments

The Scene view has a [draw mode](http://docs.unity3d.com/Manual/ViewModes.html) called Shadow Cascades that uses coloration to show the parts of the scene using the different cascade levels. You can use this to help you get the shadow distance, cascade count and cascade split ratios just right.

![Shadow Cascades draw mode in the Scene view](http://docs.unity3d.com/uploads/Main/ShadCascade4Visualization.png)
> Shadow Cascades draw mode in the Scene view