> [Constant Force](https://docs.unity3d.com/Manual/class-ConstantForce.html)

Unity Manual > Physics > 3D Physics Reference > Constant Force

# Constant Force

[SWITCH TO SCRIPTING](https://docs.unity3d.com/ScriptReference/ConstantForce.html)

**Constant Force** is a quick utility for adding constant forces to a Rigidbody. This works great for one shot objects like rockets, if you don’t want it to start with a large velocity but instead accelerate.


## Properties

Property:   Function:
Force   The vector of a force to be applied in world space.
Relative Force  The vector of a force to be applied in the object’s local space.
Torque  The vector of a torque, applied in world space. The object will begin spinning around this vector. The longer the vector is, the faster the rotation.
Relative Torque The vector of a torque, applied in local space. The object will begin spinning around this vector. The longer the vector is, the faster the rotation.
Details

To make a rocket that accelerates forward set the Relative Force to be along the positive z-axis. Then use the Rigidbody’s Drag property to make it not exceed some maximum velocity (the higher the drag the lower the maximum velocity will be). In the Rigidbody, also make sure to turn off gravity so that the rocket will always stay on its path.

## Hints

To make an object flow upwards, add a Constant Force with the Force property having a positive Y value.
To make an object fly forwards, add a Constant Force with the Relative Force property having a positive Z value.