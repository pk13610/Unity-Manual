> 原文：[Creating Gameplay](http://docs.unity3d.com/Manual/Attributes.html)

<!-- Unity Manual > Working In Unity > Creating Gameplay > GameObjects -->
Unity 手册 <i class="fa fa-angle-right"/> 使用 Unity <i class="fa fa-angle-right"/> 创建游戏 <i class="fa fa-angle-right"/> 游戏对象

<!-- # GameObjects -->
# 游戏对象 GameObject

<!-- The **GameObject** is the most important type of object in Unity. It is very important to understand what a GameObject is, and how it can be used. -->
**游戏对象 GameObject** 是 Unity 中最重要的对象类型。理解游戏对象是什么和如何使用非常重要。

<!-- ## What are GameObjects? -->
## 游戏对象 GameObject 是什么？

<!-- Every object in your game is a GameObject. However, GameObjects don’t do anything on their own. They need special properties before they can become a character, an environment, or a special effect. But each of these objects do very different things. If every object is a GameObject, how do we differentiate an interactive power-up object from a static room? What makes these GameObjects different from each other? -->
游戏中的每个对象都是一个 GameObject。不过，一个游戏对象自身无法做任何事情。在成为一个角色、一个环境或一个特效之前，需要为 GameObject 设置特殊的属性。但是，这些对象的行为差异那么大，如果每个对象都是一个 GameObject，我们如何从一个静态房间里区分出一个可交互的电源开源呢？是什么让这些 GameObject 各不相同的呢？

![](http://docs.unity3d.com/uploads/Main/GameObjectsExamples.png)

<!-- > Four different Game Objects, an animated character, a light, a tree and an audio source -->
> 四种不同的游戏对象，一个可动的角色，一盏灯，一棵树，一个声音资源。

<!-- The answer to this question is that GameObjects are containers. They can hold the different pieces that are required to make up a character, a light, a tree, a sound, or whatever else you would like to build. So to really understand GameObjects, you have to understand these pieces which are called **Components**. -->
这个问题的答案是：游戏对象 GameObject 是容器。他们可以持有不同的零件，这些零件用于构建一个角色、一盏灯、一棵树、一个声音或者任何你想构建的东西。所以，为了真正理解游戏对象 GameObject，你必须理解这些零件。这些零件在 Untiy 中称为**组件 Component**。

<!-- Depending on what kind of object you want to create, you will add different combinations of Components to the GameObject. Think of a GameObject as an empty cooking pot, and Components as different ingredients that make up your recipe of gameplay. Unity has lots of different built-in component types, and you can also make your own Components using Scripts. -->
你向 Gameplay 中添加的组件组合，取决于你想创建的对象类型。如果把一个 GameObject 想象成一个空锅，组件就是各种食材，构成了游戏的菜谱。Unity 内置了大量不同类型的组件，你也可以使用脚本 Script 创建自己的组件。

<!-- This section explains how Game Objects, Components and Scripts fit together, and how to create and use them. -->
这一章将介绍游戏对象 GameObject、组件 Component 和脚本 Script 是如何组合在一起的，以及如何创建和使用它们。

