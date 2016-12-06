<!-- > [Joints](https://docs.unity3d.com/Manual/Joints.html) -->

<!-- Unity Manual > Physics > Physics Overview > Joints -->

<!-- # Joints -->
# 连接

<!-- You can attach one rigidbody object to another or to a fixed point in space using a **Joint** component. Generally, you want a joint to allow at least some freedom of motion and so Unity provides different Joint components that enforce different restrictions. -->

通过 **连接 Joint** 组件，你可以把一个刚体对象附加到另一个对象上，从而建立固定连接。一般来说，你想要的是一个自由度有限的连接，因为 Unity 提供了不同的连接组件来实施不同的限制。

<!-- For example, a [Hinge Joint](https://docs.unity3d.com/Manual/class-HingeJoint.html) allows rotation around a specific point and axis while a [Spring Joint](https://docs.unity3d.com/Manual/class-SpringJoint.html) keeps the objects apart but lets the distance between them stretch slightly. -->

例如，一个 [链条连接 Hinge Joint] 允许围绕特定点和轴线旋转，而一个 [弹簧连接 Spring Joint] 则保持物体分离并稍微拉开距离。

[链条连接]: https://docs.unity3d.com/Manual/class-HingeJoint.html)
[弹簧连接]: https://docs.unity3d.com/Manual/class-SpringJoint.html)

<!-- 2D joint components have **2D** at the end of the name, eg, [Hinge Joint 2D](https://docs.unity3d.com/Manual/class-HingeJoint2D.html). See [Joints 2D](https://docs.unity3d.com/Manual/Joints2D.html) for a summary of the 2D joints and useful background information. -->

2D 连接组件的在名字的末尾带有 **2D**，例如 [Hinge Joint 2D]。2D 连接的概述和背景信息请参考 [Joints 2D]。

[Hinge Joint 2D]: https://docs.unity3d.com/Manual/class-HingeJoint2D.html
[Joints 2D]: https://docs.unity3d.com/Manual/Joints2D.html

<!-- Joints also have other options that can enabled for specific effects. For example, you can set a joint to break when the force applied to it exceeds a certain threshold. Some joints also allow a **drive force** to occur between the connected objects to set them in motion automatically. -->

连接还有其他可以实现特定效果的选项。例如，可以为连接设置断开效果，当施加到连接的作用力超过某个特定阀值时，连接将断开。某些连接还允许相连物体之间产生驱动力，从而自动地运动。

<!-- See each joint reference page for the Joint classes and for further information about their properties. -->

有关连接属性的更多信息，请参考 Joint 类的参考页。
