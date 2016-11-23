> [Creating and Editing Terrains](http://docs.unity3d.com/Manual/terrain-UsingTerrains.html)

Unity Manual > Graphics > Graphics Overview > Terrain Engine > Creating and Editing Terrains

# Creating and Editing Terrains
You can add a terrain object to your scene by selecting **GameObject > 3D Object > Terrain** from the menu (this will also add a corresponding Terrain asset to the Project view). However, the landscape will initially be nothing more than a large, flat plane. However, if you look at the inspector when the terrain object is selected, you will see that it provides a number of tools you can use to create any landscape features you like.

![Terrain Editing Tools appear in the Inspector](http://docs.unity3d.com/uploads/Main/TerrainEditingTools.png)
> Terrain Editing Tools appear in the Inspector

With the exception of the tree placement tool and the settings panel, all the tools on the toolbar provide a set of “brushes” and settings for brush size and opacity. It is no coincidence that these resemble the painting tools from an image editor because detail in the terrain is created precisely that way, by “painting” detail onto the landscape. If you select the leftmost tool on the bar (_Raise/Lower Terrain_) and move the mouse over the terrain in the scene view, you will see a cursor resembling a spotlight on the surface. When you click the mouse, you can paint gradual changes in height onto the landscape at the mouse’s position. By selecting different options from the _Brushes_ toolbar, you can paint with different shapes. The _Brush Size_ and _Opacity_ options vary the area of the brush and the strength of its effect respectively.

The details of all of the tools will be given in subsequent sections. However, all of them are based around the concept of painting detail and with the exception of the tree placement tool, all have the same options for brushes, brush size and opacity. The tools can be used to set the height of the terrain and also to add coloration, plants and other objects.

## Terrain Keyboard Shortcuts

You can use the following keyboard shortcuts in the terrain inspector:

* Pressing the keys from F1 to F6 with the shift key held down selects the corresponding terrain tool (eg, F1 selects the _Raise/Lower_ tool).
* Comma (,) and dot (.) cycle through the available brushes.
* Shift-comma (<) and Shift-dot (>) cycle through the available objects for trees, textures and details.
Additionally, the standard F keystroke works slightly differently for terrains. Normally, it frames the selection around the whole object when the mouse is over the scene view. However, since terrains are typically very large, pressing F will focus the scene view on the area of terrain where the mouse/brush is currently hovering. This provides a very quick and intuitive way to jump to the area of terrain you want to edit. If you press F when the mouse is away from the terrain object, the standard framing behaviour will return.