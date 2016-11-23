> 原文：[Introduction to Components](http://docs.unity3d.com/Manual/Components.html)

<!-- Unity Manual > Working In Unity > Creating Gameplay > GameObjects > Introduction to Components -->
Unity 手册 <i class="fa fa-angle-right"/> 使用 Unity <i class="fa fa-angle-right"/> 创建游戏 <i class="fa fa-angle-right"/> 游戏对象 <i class="fa fa-angle-right"/> 组件 Component 简介

<!-- # Introduction to Components -->
# 组件 Component 简介

As described previously in [GameObjects](http://docs.unity3d.com/Manual/GameObjects.html), a GameObject contains Components. We’ll explore this relationship by discussing a GameObject and its most common Component – the Transform Component. With any Unity Scene open, create a new GameObject (using **Shift-Control-N** on Windows or **Shift-Command-N** on Mac), select it and take a look at the **Inspector**.

就像之前在 [GameObjects](http://docs.unity3d.com/Manual/GameObjects.html) 中描述的，一个游戏对象包含多个组件。

![](http://docs.unity3d.com/uploads/Main/EmptyGO.png)

> The Inspector of an Empty GameObject

Notice that an empty GameObject still contains a Name, a [Tag](http://docs.unity3d.com/Manual/Tags.html), and a [Layer](http://docs.unity3d.com/Manual/Layers.html). Every GameObject also contains a [Transform Component](http://docs.unity3d.com/Manual/class-Transform.html).

## The Transform Component

It is impossible to create a GameObject in Unity without a Transform Component. The Transform Component is one of the most important Components, since all of the GameObject’s Transform properties are enabled by its use of this Component. It defines the GameObject’s position, rotation, and scale in the game world/Scene View. If a GameObject did not have a Transform Component, it would be nothing more than some information in the computer’s memory. It effectively would not exist in the world.

The Transform Component also enables a concept called Parenting, which is utilized through the Unity Editor and is a critical part of working with GameObjects. To learn more about the Transform Component and Parenting, read the Transform Component Reference page.

## Other Components

The Transform Component is critical to all GameObjects, so each GameObject has one. But GameObjects can contain other Components as well.

The Main Camera, added to each scene by default
The Main Camera, added to each scene by default
Looking at the Main Camera GameObject, you can see that it contains a different collection of Components. Specifically, a Camera Component, a GUILayer, a Flare Layer, and an Audio Listener. All of these Components provide additional functionality to the GameObject. Without them, there would be nothing rendering the graphics of the game for the person playing! Rigidbodies, Colliders, Particles, and Audio are all different Components (or combinations of Components) that can be added to any given GameObject.