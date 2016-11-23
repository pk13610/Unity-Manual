> [Height Tools](http://docs.unity3d.com/Manual/terrain-Height.html)

Unity Manual > Graphics > Graphics Overview > Terrain Engine > Height Tools

# Height Tools

The first three tools on the terrain inspector toolbar are used to paint changes in height onto the terrain.

![](http://docs.unity3d.com/uploads/Main/TerrainHeightTools.png)

From the left, the first button activates the —— tool. When you paint with this tool, the height will be increased as you sweep the mouse over the terrain. The height will accumulate if you hold the mouse in one place, similar to the effect of the airbrush tools in image editors. If you hold down the shift key, the height will be lowered. The different brushes can be used to create a variety of effects. For example, you can create rolling hills by increasing the height with a soft-edged brush and then cut steep cliffs and valleys by lowering with a hard-edged brush.

![Rolling hills cut by a steep valley](http://docs.unity3d.com/uploads/Main/TerrainRaiseLower.png)
> Rolling hills cut by a steep valley

The second tool from the left, _Paint Height_ is similar to the _Raise/Lower_ tool except that it has an additional property to set the target height. When you paint on the object, the terrain will be lowered in areas above that height and raised in areas below it. You can use the _Height_ property slider to set the height manually or you can shift-click on the terrain to sample the height at the mouse position (rather like the “eyedropper” tool in an image editor). Next to the _Height_ property is a _Flatten_ button that simply levels the whole terrain to the chosen height. This is useful to set a raised ground level, say if you want the landscape to include both hills above the level and valleys below it. _Paint Height_ is handy for creating plateaux in a scene and also for adding artificial features like roads, platforms and steps.

![Hillside with a flat road](http://docs.unity3d.com/uploads/Main/TerrainPaintHeight.png)
>Hillside with a flat road

The third tool from the left, _Smooth Height_ does not significantly raise or lower the terrain height but rather averages out nearby areas. This softens the landscape and reduces the appearance of abrupt changes, somewhat like the blur tool in an image editor. You might use this, for example, when you have painted detail using one of the noisier brushes in the available set. These brush patterns will tend to introduce sharp, jagged rocks into a landscape, but these can be softened using _Smooth Height_.

## Working with Heightmaps

As noted above, the height tools are reminiscent of painting tools available in image editors. In fact, the terrain is implemented using a texture behind the scenes and so the tools are ultimately acting as texture painting tools.

The height of each point on the terrain is represented as a value in a rectangular array. This array can be represented using a grayscale image known as a **heightmap**. It is sometimes useful to work on a heightmap image in an external editor, such as Photoshop, or obtain existing geographical heightmaps for use in your game. Unity provides the option to import and export heightmaps for a terrain; if you click on the _Settings_ tool (the rightmost button in the toolbar) you will find buttons labelled _Import RAW_ and _Export RAW_. These allow the heightmap to be read from or written to the standard RAW format, which is a 16-bit grayscale format compatible with most image and landscape editors.

