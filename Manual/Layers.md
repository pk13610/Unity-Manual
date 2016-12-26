<!-- # Layers -->
# 图层

<!-- **Layers** are most commonly used by **Cameras** to render only a part of the scene, and by **Lights** to illuminate only parts of the scene. But they can also be used by raycasting to selectively ignore colliders or to create [collisions]. -->

**图层** 最常用于 **摄像机** 只渲染场景的一部分，和 **光线** 只照亮场景的一部分。此外，射线投射也可以用它们选择性地忽略碰撞器或创建 [碰撞]。

[collisions]: https://docs.unity3d.com/Manual/LayerBasedCollision.html
[碰撞]: https://docs.unity3d.com/Manual/LayerBasedCollision.html

<!-- ## Creating Layers -->
## 创建图层

<!-- The first step is to create a new layer, which we can then assign to a **GameObject**. To create a new layer, open the Edit menu and select **Project Settings->Tags and Layers**. -->

第一步是创建一个图层，稍后可以将其分配给一个 **游戏对象 GameObject**。要创建图层，请打开菜单并选择 **Project Settings->Tags and Layers**。

<!-- We create a new layer in one of the empty User Layers. We choose layer 8. -->

我们在空着的 User Layers 中新建一个图层。选择第 8 图层 `User Player 8`。

![](https://docs.unity3d.com/uploads/Main/Layer-CreateNewLayer.png)

<!-- ## Assigning Layers -->
## 分配图层

<!-- Now that you have created a new layer, you have to assign the layer to one of the game objects. -->

现在，你已经新建了一个图层，必须将该图层分配给一个游戏对象。

![](https://docs.unity3d.com/uploads/Main/Layer-ChooseLayer.png)

<!-- In the tag manager we assigned the Player layer to be in layer 8. -->

在标签管理器中，指定图层 `Layer` 为 Player。

<!-- ## Drawing only a part of the scene with the camera’s culling mask -->
## 使用摄像机的剔除遮罩仅绘制部分场景

<!-- Using the camera’s culling mask, you can selectively render objects which are in one particular layer. To do this, select the camera that should selectively render objects. -->

使用摄像机的剔除遮罩，你可以选择性地渲染特定图层中的对象。为此，请选中负责选择性渲染对象的摄像机。

<!-- Modify the culling mask by checking or unchecking layers in the culling mask property. -->

在剔除遮罩 `culling mask` 属性中，通过选中或取消图层来修改。

![](https://docs.unity3d.com/uploads/Main/Layer-CullingMask.png)

<!-- ## Casting Rays Selectively -->
## 选择性地投射射线

<!-- Using layers you can cast rays and ignore colliders in specific layers. For example you might want to cast a ray only against the player layer and ignore all other colliders. -->

通过使用图层，你可以在投射射线时选择性地忽略特定图层中的碰撞器。例如，你可能想要投射只针对玩家的射线，而忽略所有其他碰撞器。

<!-- The Physics.Raycast function takes a bitmask, where each bit determines if a layer will be ignored or not. If all bits in the layerMask are on, we will collide against all colliders. If the layerMask = 0, we will never find any collisions with the ray. -->

函数 `Physics.Raycast` 接受一个位掩码 `layerMask`，其中每一个比特决定了一个图形是否将被忽略。如果 layerMask 中的所有比特位都为 1，那么该射线将和所有碰撞器发生碰撞。如果 layerMask 等于 0，那么该射线永远不会和任意对象发生碰撞。

```js
// JavaScript example.

// bit shift the index of the layer to get a bit mask
var layerMask = 1 << 8;
// Does the ray intersect any objects which are in the player layer.
if (Physics.Raycast (transform.position, Vector3.forward, Mathf.Infinity, layerMask))
    print ("The ray hit the player");
```

```cs
// C# example.

int layerMask = 1 << 8;
        
// Does the ray intersect any objects which are in the player layer.
if (Physics.Raycast(transform.position, Vector3.forward, Mathf.Infinity, layerMask))
    Debug.Log("The ray hit the player");
```

<!-- In the real world you want to do the inverse of that however. We want to cast a ray against all colliders except those in the Player layer. -->

而在现实世界中，你想要做的恰好与之相反。我们想要向所有碰撞器投射射线，除了 Player 图层中的碰撞器。

```js
// JavaScript example.
function Update () {
  // Bit shift the index of the layer (8) to get a bit mask
  var layerMask = 1 << 8;
  // This would cast rays only against colliders in layer 8.
  // But instead we want to collide against everything except layer 8. The ~ operator does this, it inverts a bitmask.
  layerMask = ~layerMask;

  var hit : RaycastHit;
  // Does the ray intersect any objects excluding the player layer
  if (Physics.Raycast (transform.position, transform.TransformDirection (Vector3.forward), hit, Mathf.Infinity, layerMask)) {
    Debug.DrawRay (transform.position, transform.TransformDirection (Vector3.forward) * hit.distance, Color.yellow);
    print ("Did Hit");
  } else {
    Debug.DrawRay (transform.position, transform.TransformDirection (Vector3.forward) *1000, Color.white);
    print ("Did not Hit");
  }
}
```

```cs
// C# example.
void Update () {
    // Bit shift the index of the layer (8) to get a bit mask
    int layerMask = 1 << 8;
        
    // This would cast rays only against colliders in layer 8.
    // But instead we want to collide against everything except layer 8. The ~ operator does this, it inverts a bitmask.
    layerMask = ~layerMask;
    
    RaycastHit hit;
    // Does the ray intersect any objects excluding the player layer
    if (Physics.Raycast(transform.position, transform.TransformDirection (Vector3.forward), out hit, Mathf.Infinity, layerMask)) {
        Debug.DrawRay(transform.position, transform.TransformDirection (Vector3.forward) * hit.distance, Color.yellow);
        Debug.Log("Did Hit");
    } else {
        Debug.DrawRay(transform.position, transform.TransformDirection (Vector3.forward) *1000, Color.white);
        Debug.Log("Did not Hit");
    }
}
```

<!-- When you don’t pass a layerMask to the Raycast function, it will only ignore colliders that use the IgnoreRaycast layer. This is the easiest way to ignore some colliders when casting a ray. -->

如果调用 `Raycast` 函数时没有传入 `layerMask`，将只会忽略使用了 `IgnoreRaycast` 图层的碰撞器。这是投射射线时忽略某些碰撞器的最简单方式。
