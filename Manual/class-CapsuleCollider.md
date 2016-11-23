> [Capsule Collider](https://docs.unity3d.com/Manual/class-CapsuleCollider.html)

Unity Manual > Physics > 3D Physics Reference > Capsule Collider

# Capsule Collider

[SWITCH TO SCRIPTING](https://docs.unity3d.com/ScriptReference/CapsuleCollider.html)

The Capsule Collider is made of two half-spheres joined together by a cylinder. It is the same shape as the Capsule primitive.

![](https://docs.unity3d.com/uploads/Main/Inspector-CapsuleCollider.png)

## Properties

> Property:   Function:

**Is Trigger**  If enabled, this Collider is used for triggering events, and is ignored by the physics engine.

**Material**    Reference to the Physics Material that determines how this Collider interacts with others.

**Center**  The position of the Collider in the object’s local space.

**Radius**  The radius of the Collider’s local width.

**Height**  The total height of the Collider.

**Direction**   The axis of the capsule’s lengthwise orientation in the object’s local space.

## Details

You can adjust the Capsule Collider’s **Radius** and **Height** independently of each other. It is used in the [Character Controller](https://docs.unity3d.com/Manual/class-CharacterController.html) and works well for poles, or can be combined with other Colliders for unusual shapes.

![A standard Capsule Collider](https://docs.unity3d.com/uploads/Main/CapsuleColliderDiagram.svg)
> A standard Capsule Collider