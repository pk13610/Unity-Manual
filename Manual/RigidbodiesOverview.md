> [Rigidbody overview](http://docs.unity3d.com/Manual/RigidbodiesOverview.html)

Unity Manual > Physics > Physics Overview > Rigidbody overview

# Rigidbody overview

A **Rigidbody** is the main component that enables physical behaviour for a GameObject. With a Rigidbody attached, the object will immediately respond to gravity. If one or more **Collider** components are also added, the GameObject is moved by incoming collisions.

Since a Rigidbody component takes over the movement of the GameObject it is attached to, you shouldn’t try to move it from a script by changing the [Transform](http://docs.unity3d.com/Manual/class-Transform.html) properties such as position and rotation. Instead, you should apply **forces** to push the GameObject and let the physics engine calculate the results.

There are some cases where you might want a GameObject to have a Rigidbody without having its motion controlled by the physics engine. For example, you may want to control your character directly from script code but still allow it to be detected by triggers (see _Triggers_ below). This kind of non-physical motion produced from a script is known as _kinematic_ motion. The Rigidbody component has a property called **Is Kinematic** which removes it from the control of the physics engine and allow it to be moved kinematically from a script. It is possible to change the value of **Is Kinematic** from a script to allow physics to be switched on and off for an object, but this comes with a performance overhead and should be used sparingly.

See the [Rigidbody](http://docs.unity3d.com/Manual/class-Rigidbody.html) and [Rigidbody 2D](http://docs.unity3d.com/Manual/class-Rigidbody2D.html) reference pages for further details about the settings and scripting options for these components.

## Sleeping

When a Rigidbody is moving slower than a defined minimum linear or rotational speed, the physics engine assumes it has come to a halt. When this happens, the GameObject does not move again until it receives a collision or force, and so it is set to “sleeping” mode. This optimisation means that no processor time is spent updating the Rigidbody until the next time it is “awoken” (that is, set in motion again).

For most purposes, the sleeping and waking of a Rigidbody component happens transparently. However, a GameObject might fail to wake up if a Static Collider (that is, one without a Rigidbody) is moved into it or away from it by modifying the Transform position. This might result, say, in the Rigidbody GameObject hanging in the air when the floor has been moved out from beneath it. In cases like this, the GameObject can be woken explicitly using the WakeUp function. See the [Rigidbody](http://docs.unity3d.com/Manual/class-Rigidbody.html) and [Rigidbody 2D](http://docs.unity3d.com/Manual/class-Rigidbody2D.html) component pages for more information about sleeping.