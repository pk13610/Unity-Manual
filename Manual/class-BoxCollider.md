> [Box Collider](https://docs.unity3d.com/Manual/class-BoxCollider.html)

Unity Manual > Physics > 3D Physics Reference > Box Collider

# Box Collider

[SWITCH TO SCRIPTING](https://docs.unity3d.com/ScriptReference/BoxCollider.html)

The Box Collider is a basic cube-shaped collision primitive.

![](https://docs.unity3d.com/uploads/Main/Inspector-BoxCollider.png)

## Properties

> Property:   Function:

**Is Trigger**  If enabled, this Collider is used for triggering events, and is ignored by the physics engine.

**Material**    Reference to the Physics Material that determines how this Collider interacts with others.

**Center**  The position of the Collider in the object’s local space.

**Size**    The size of the Collider in the X, Y, Z directions.

## Details

Box colliders are obviously useful for anything roughly box-shaped, such as a crate or a chest. However, you can use a thin box as a floor, wall or ramp. The box shape is also a useful element in a compound collider.