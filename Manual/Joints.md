> [Joints](https://docs.unity3d.com/Manual/Joints.html)

Unity Manual > Physics > Physics Overview > Joints

# Joints

You can attach one rigidbody object to another or to a fixed point in space using a **Joint** component. Generally, you want a joint to allow at least some freedom of motion and so Unity provides different Joint components that enforce different restrictions.

For example, a [Hinge Joint](https://docs.unity3d.com/Manual/class-HingeJoint.html) allows rotation around a specific point and axis while a [Spring Joint](https://docs.unity3d.com/Manual/class-SpringJoint.html) keeps the objects apart but lets the distance between them stretch slightly.

2D joint components have **2D** at the end of the name, eg, [Hinge Joint 2D](https://docs.unity3d.com/Manual/class-HingeJoint2D.html). See [Joints 2D](https://docs.unity3d.com/Manual/Joints2D.html) for a summary of the 2D joints and useful background information.

Joints also have other options that can enabled for specific effects. For example, you can set a joint to break when the force applied to it exceeds a certain threshold. Some joints also allow a **drive force** to occur between the connected objects to set them in motion automatically.

See each joint reference page for the Joint classes and for further information about their properties.

Colliders
