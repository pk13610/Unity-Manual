> [Terrain Settings](http://docs.unity3d.com/Manual/terrain-OtherSettings.html)

Unity Manual > Graphics > Graphics Overview > Terrain Engine > Terrain Settings

# Terrain Settings

The final tool on the terrain toolbar is for settings:

![](http://docs.unity3d.com/uploads/Main/TerrainSettingsTool.png)

## Settings Inspector

Settings are provided for a number of overall usage and rendering options as described below:

![](http://docs.unity3d.com/uploads/Main/TerrainSettingsInsp.png)

### Base Terrain

> Property:   Function:

*  **Draw**    Toggle the rendering of terrain on / off.
* **Pixel Error** The accuracy of the mapping between the terrain maps (heightmap, textures, etc) and the generated terrain; higher values indicate lower accuracy but lower rendering overhead.
* **Base Map Distance**   The maximum distance at which terrain textures will be displayed at full resolution. Beyond this distance, a lower resolution composite image will be used for efficiency.
** **Cast Shadows**    Does the terrain cast shadows?
* **Material**    The material used to render the terrain. This will affect how the color channels of a terrain texture are interpreted. See Enabling Textures for details. Available options are:
    * Built In Standard   This is the PBR (Physically-Based Rendering) material introduced in Unity 5.0. For each splat layer, you can use one texture for albedo and smoothness, one texture for normal and one scalar value to tweak the metalness. For more information on PBR and the Standard shader, see Standard Shader.
    * Built In Legacy Diffuse This is the legacy built-in terrain material from Unity 4.x and before. It uses Lambert (diffuse term only) lighting model and has optional normal map support.
    * Built In Legacy Specular    This built-in material uses BlinnPhong (diffuse and specular term) lighting model and has optional normal map support. You can specify the overall specular color and shininess for the terrain.
    * Custom  Use a custom material of your choice to render the terrain. This material should use a shader that is specialised for terrain rendering (e.g. it should handle texture splatting properly). We suggest you get a look at the source code of our built-in terrain shaders and make modifications on top of them.
* **Reflection Probes**   How reflection probes are used on terrain. Only effective when using built-in standard material or a custom material which supports rendering with reflection. Available options are:
    * Off Reflection probes are disabled, skybox will be used for reflection.
        Blend Probes    Reflection probes are enabled. Blending occurs only between probes. Default reflection will be used if there are no reflection probes nearby, but no blending between default reflection and probe will occur.
    * Blend Probes And Skybox Reflection probes are enabled. Blending occurs between probes or probes and default reflection.
    * Simple  Reflection probes are enabled, but no blending will occur between probes when there are two overlapping volumes.
* **Thickness**   How much the terrain collision volume should extend along the negative Y-axis. Objects are considered colliding with the terrain from the surface to a depth equal to the thickness. This helps prevent high-speed moving objects from penetrating into the terrain without using expensive continuous collision detection.

### Tree and Detail Objects

> Property:   Function:

* **Draw**    Should trees, grass and details be drawn?
* **Detail Distance** The distance (from camera) beyond which details will be culled.
* **Detail Density**  The number of detail/grass objects in a given unit of area. The value can be set lower to reduce rendering overhead.
* **Tree Distance**   The distance (from camera) beyond which trees will be culled.
* **Billboard Start** The distance (from camera) at which 3D tree objects will be replaced by billboard images.
* **Fade length** Distance over which trees will transition between 3D objects and billboards.
* **Max Mesh Trees**  The maximum number of visible trees that will be represented as solid 3D meshes. Beyond this limit, trees will be replaced with billboards.

### Wind Settings

> Property:   Function:

* **Speed**   The speed of the wind as it blows grass.
* **Size**    The size of the “ripples” on grassy areas as the wind blows over them.
* **Bending** The degree to which grass objects are bent over by the wind.
* **Grass Tint**  Overall color tint applied to grass objects.

### Resolution

> Property:   Function:

* **Terrain Width**   Size of the terrain object in its X axis (in world units).
* **Terrain Length**  Size of the terrain object in its Z axis (in world units).
* **Terrain Height**  Difference in Y coordinate between the lowest possible heightmap value and the highest (in world units).
* **Heightmap Resolution**    Pixel resolution of the terrain’s heightmap (should be a power of two plus one, eg, 513 = 512 + 1).
* **Detail Resolution**   Resolution of the map that determines the separate patches of details/grass. Higher resolution gives smaller and more detailed patches.
* **Detail Resolution Per Patch** Length/width of the square of patches renderered with a single draw call.
* **Control Texture Resolution**  Resolution of the “splatmap” that controls the blending of the different terrain textures.
* **Base Texture Resolution** Resolution of the composite texture used on the terrain when viewed from a distance greater than the Basemap Distance (see above).

### Heightmap Import/Export Buttons

The _Import Raw_ and _Export Raw_ buttons allow you to set or save the terrain’s heightmap to an image file in the RAW grayscale format. RAW format can be generated by third party terrain editing tools (such as Bryce) and can also be opened, edited and saved by Photoshop. This allows for sophisticated generation and editing of terrains outside Unity.