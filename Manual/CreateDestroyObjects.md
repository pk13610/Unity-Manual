<!-- > 原文：[Creating and Destroying GameObjects](http://docs.unity3d.com/Manual/CreateDestroyObjects.html) -->

<!-- Unity Manual > Scripting > Scripting Overview > Creating and Destroying GameObjects -->
<!-- Unity 手册 <i class="fa fa-angle-right"/> 脚本 <i class="fa fa-angle-right"/> 脚本概述 <i class="fa fa-angle-right"/> 创建和销毁游戏对象 -->

<!-- # Creating and Destroying GameObjects -->
# 创建和销毁游戏对象

<!-- Some games keep a constant number of objects in the scene, but it is very common for characters, treasures and other object to be created and removed during gameplay. In Unity, a GameObject can be created using the [Instantiate] function which makes a new copy of an existing object: -->
某些游戏在场景中维护恒定数量的对象，但是在游戏过程中，创建和移除人物、物品以及其他对象也非常普遍。在 Unity 中，一个游戏对象可以通过 [Instantiate] 函数创建一个已有对象的新副本。

[Instantiate]: http://docs.unity3d.com/ScriptReference/Object.Instantiate.html

```c#
public GameObject enemy;

void Start() {
    for (int i = 0; i < 5; i++) {
        Instantiate(enemy);
    }
}
```

<!-- Note that the object from which the copy is made doesn’t have to be present in the scene. It is more common to use a prefab dragged to a public variable from the Project panel in the editor. Also, instantiating a GameObject will copy all the Components present on the original. -->
需要注意的是，被复制的原始对象不一定必须是场景中的对象。比较常见的是，将一个预知对象拖动到编辑器 Project 面板的一个公共变量上。而且，初始化一个游戏对象将复制原始对象上的所有组件。

<!-- There is also a [Destroy] function that will destroy an object after the frame update has finished or optionally after a short time delay: -->
还有一个 Destroy 函数用于在桢更新完成之后或者一段可选的短暂延迟之后销毁对象：

[Destroy]: http://docs.unity3d.com/ScriptReference/Object.Destroy.html

```c#
void OnCollisionEnter(Collision otherObj) {
    if (otherObj.gameObject.tag == "Missile") {
        Destroy(gameObject,.5f);
    }
}
```

<!-- Note that the Destroy function can destroy individual components without affecting the GameObject itself. A common mistake is to write something like: -->
请注意，Destroy 函数可以单独销毁某些组件而不影响游戏对象本身。下面是一个常见的错误：

```c#
Destroy(this);
```

<!-- …which will actually just destroy the script component that calls it rather than destroying the GameObject the script is attached to. -->
上面这行代码实际上只是销毁被调用的脚本组件，而不是绑定了该脚本组件的游戏对象。
