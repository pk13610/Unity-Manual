> 原文：[GameObject](http://docs.unity3d.com/Manual/class-GameObject.html)

<!-- Unity Manual > Working In Unity > Creating Gameplay > GameObjects -->
Unity 手册 <i class="fa fa-angle-right"/> 使用 Unity <i class="fa fa-angle-right"/> 创建游戏 <i class="fa fa-angle-right"/> 游戏对象 <i class="fa fa-angle-right"/> 游戏对象

<!-- # GameObject -->
# 游戏对象 GameObject

<!-- GameObjects are the fundamental objects in Unity that represent characters, props and scenery. They do not accomplish much in themselves but they act as containers for **Components**, which implement the real functionality. -->
在 Unity 中，游戏对象 GameObject 是表示角色、道具和场景的基本对象。GameObject 并不实现这些功能，而是作为 **组件 Component** 的容器，真正的功能由组件 Component 实现。

<!-- For example, a Light object is created by attaching a [Light](http://docs.unity3d.com/Manual/class-Light.html) component to a GameObject. -->
例如，通过向一个游戏对象 GameObject 绑定一个 [Light](http://docs.unity3d.com/Manual/class-Light.html) 组件，就创建了一个 Light 对象。

![](http://docs.unity3d.com/uploads/Main/GameObjectLightExample.png)

<!-- A solid cube object has a Mesh Filter and Mesh Renderer component, to draw the surface of the cube, and a Box Collider component to represent the object’s solid volume in terms of physics. -->
一个立方体对象含有一个 Mesh Filter 和 Mesh Renderer 组件，用来绘制立方体的表面，还有一个 Box Collider 组件，用于表示该对象各个面的物理效果。

![](http://docs.unity3d.com/uploads/Main/GameObjectCubeExample.png)

<!-- ## Details -->
## 详细说明

<!-- A GameObject always has a [Transform](http://docs.unity3d.com/Manual/class-Transform.html) component attached (to represent position and orientation) and it is not possible to remove this. The other components that give the object its functionality can be added from the editor’s **Component** menu or from a script. There are also many useful pre-constructed objects (primitive shapes, Cameras, etc) available on the **GameObject > 3D Object** menu, see [Primitive Objects](http://docs.unity3d.com/Manual/PrimitiveObjects.html). -->
一个游戏对象 GameObjects 总是会绑定一个 Transform 组件，用来表示位置和方向，并且不可能被移除。赋予 GameObjects 功能的其他组件，可以通过编辑器的 **Component** 菜单或一个脚本文件来添加。在菜单 **GameObject > 3D Object** 中，还有许多预先构建好的有用对象，例如，基本形状、摄像机等。

<!-- Since GameObjects are a very important part of Unity, there is a [GameObjects](http://docs.unity3d.com/Manual/GameObjects.html) section in the manual with extensive detail about them. You can find out more about controlling GameObjects from scripts on the [GameObject scripting reference page](http://docs.unity3d.com/ScriptReference/GameObject.html). -->
因为游戏对象 GameObject 是 Unity 中非常重要的一个部分，手册中专门有一章 [GameObjects](http://docs.unity3d.com/Manual/GameObjects.html) 介绍更多细节。你可以在 [GameObject scripting reference page](http://docs.unity3d.com/ScriptReference/GameObject.html) 中找到用脚本控制游戏对象 GameObject 的内容。
