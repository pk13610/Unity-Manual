<!-- > [Physics](http://docs.unity3d.com/Manual/PhysicsSection.html) -->

<!-- Unity Manual > Physics -->

<!-- # Physics -->
# 物理系统

![](http://docs.unity3d.com/uploads/Main/PhysicsIntroPic.jpg)

<!-- To have convincing physical behaviour, an object in a game must accelerate correctly and be affected by collisions, gravity and other forces. Unity’s built-in physics engines provide components that handle the physical simulation for you. With just a few parameter settings, you can create objects that behave passively in a realistic way (ie, they will be moved by collisions and falls but will not start moving by themselves). By controlling the physics from scripts, you can give an object the dynamics of a vehicle, a machine, or even a piece of fabric. This section gives an overview of the main physics components in Unity, with links for further reading. -->

为了实现逼真的物理行为，游戏中的对象必须被正确地加速，并且被碰撞、重力和其他力所影响。Unity 的内置物理引擎提供了处理物理模拟的组件。只需设置几个参数，就可以创建具有真实行为的对象（例如，对象被碰撞后将开始移动和掉落，但是它们不会自己移动）。通过脚本控制物理行为，你可以提供动态的车辆、机器，甚至是一片布料。本章概述了 Unity 中的主要物理组件，并提供扩展阅读的链接。


<!-- **Note:** there are actually two separate physics engines in Unity: one for 3D physics, and one for 2D physics. The main concepts are identical between the two engines (except for the extra dimension in 3D), but they are implemented using different components. For example, there is Rigidbody component for 3D physics and an analogous Rigidbody 2D for 2D physics. -->
**注意：** Unity 中实际上有两个独立的物理引擎：一个用于 3D 物理，一个用于 2D 物理。两个引擎的主要概念是相同的（除了 3D 中的额外纬度），但是它们的实现使用了不同的组件。例如，刚体组件 Rigidbody 用于 3D 物理，与之类似的 Rigidbody 2D 则用于 2D 物理。

<!-- **Related tutorials:** [Physics](https://unity3d.com/learn/tutorials/topics/physics); [Physics Best Practices](http://unity3d.com/learn/tutorials/modules/intermediate/physics/physics-best-practices?playlist=30089) -->

**相关教程：** [物理引擎]，[物理引擎最佳实践]

[物理引擎]: https://unity3d.com/learn/tutorials/topics/physics
[物理引擎最佳实践]: http://unity3d.com/learn/tutorials/modules/intermediate/physics/physics-best-practices?playlist=30089

<!-- See the [Knowledge Base Physics section](https://support.unity3d.com/hc/en-us/sections/201851913-Physics) for troubleshooting, tips and tricks. -->

有关故障排除、提示和技巧，请参阅 [物理引擎知识库]。

[物理引擎知识库]: https://support.unity3d.com/hc/en-us/sections/201851913-Physics