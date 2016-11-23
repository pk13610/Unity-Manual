> [SpeedTree](http://docs.unity3d.com/Manual/SpeedTree.html)

Unity Manual > Graphics > Graphics Overview > Terrain Engine > Trees > SpeedTree

# SpeedTree

![](http://docs.unity3d.com/uploads/Main/SpeedTreeView.png)

SpeedTree Assets (.spm files saved by Unity version of SpeedTree Modeler) are recognized and imported by Unity just like other Assets. Ensure Textures are reachable in the Project folder, and Materials for each [LOD](http://docs.unity3d.com/Manual/LevelOfDetail.html) are generated automatically. There are import settings when you select .spm Assets for you to tweak the generated GameObject and attached Materials. Materials are not generated again on reimporting, unless you hit the **Generate Materials**, or **Apply & Generate Materials** button. Therefore any customisations to the Materials can be preserved.

The SpeedTree importer in the end generates a Prefab with [LODGroup component](http://docs.unity3d.com/Manual/class-LODGroup.html) configured. The Prefab can both be instantiated in a Scene as a common Prefab instance, or be selected as a tree prototype on the terrain and be “painted” across it. Additionally, terrain accepts any GameObject with an LODGroup component as a tree prototype, and put no limitation on the mesh size or number of Materials being used (in contrast to the [Tree Creator](http://docs.unity3d.com/Manual/class-Tree.html) trees). But, be aware that SpeedTree trees usually use 3–4 different Materials, which results in a number of draw-calls being issued every frame, so you should try to avoid heavy use of LOD trees on platforms that are sensible to draw-call numbers.

## Casting and receiving real-time shadows

To make billboards cast shadows correctly, during the shadow caster pass, billboards are rotated to face the light direction (or light position in the case of point light) instead of facing the camera.

To enable these options, select the **Billboard LOD** level in the Inspector of an .spm Asset, tick **Cast Shadows** or **Receive Shadows** in **Billboard Options**, and click **Apply Prefab**.

![](http://docs.unity3d.com/uploads/Main/speedtreeimportsettings_light.png)

To change billboard shadow options of instantiated SpeedTree GameObjects, select the billboard GameObject in the Hierarchy window, and tweak these options in the Inspector of the Billboard Renderer, just as you would with a normal Mesh Renderer.

![](http://docs.unity3d.com/uploads/Main/BillboardRendererInspector_Light.png)

Trees painted on the terrain inherit billboard shadow options from the Prefab.

You can use `BillboardRenderer.shadowCastingMode` and `BillboardRenderer.receiveShadows` to alter these options at runtime.

**Known Issues:** As with any other renderer, the **Receive Shadows** option has no effect while using deferred rendering. Billboards always receive shadows in deferred path.

## Performance Improvements in 5.3

Billboard batching performance is improved in 5.3. Multiple cores are utilized for executing the dynamic batching code of billboards.

Batching logic is simplified. Now a batch draws one type of billboard because in real-world cases billboards can hardly share one batch. Refer to `SpeedTreeBillboard.shader` for the change. If you have a customized billboard Shader, depending on the previous behavior, you might need to amend your Shaders.
