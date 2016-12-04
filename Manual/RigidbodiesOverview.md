<!-- > [Rigidbody overview](http://docs.unity3d.com/Manual/RigidbodiesOverview.html) -->

<!-- Unity Manual > Physics > Physics Overview > Rigidbody overview -->

<!-- # Rigidbody overview -->
# 刚体概述

<!-- A **Rigidbody** is the main component that enables physical behaviour for a GameObject. With a Rigidbody attached, the object will immediately respond to gravity. If one or more **Collider** components are also added, the GameObject is moved by incoming collisions. -->

**刚体 Rigidbody** 是为游戏对象赋予物理行为的主要组件。绑定组件后，游戏对象将立即响应重力。如果还添加了一个或多个 **碰撞器组件 Collider**，游戏对象将被即将到来的碰撞所移动。

<!-- Since a Rigidbody component takes over the movement of the GameObject it is attached to, you shouldn’t try to move it from a script by changing the [Transform](http://docs.unity3d.com/Manual/class-Transform.html) properties such as position and rotation. Instead, you should apply **forces** to push the GameObject and let the physics engine calculate the results. -->

由于刚体组件接管了游戏对象的移动，所以不应该尝试通过修改 [Transform](http://docs.unity3d.com/Manual/class-Transform.html) 的位置或旋转属性来移动游戏对象。相反，你应该用 **作用力** 来推动物体，并让物理引擎来计算结果。

<!-- There are some cases where you might want a GameObject to have a Rigidbody without having its motion controlled by the physics engine. For example, you may want to control your character directly from script code but still allow it to be detected by triggers (see _Triggers_ below). This kind of non-physical motion produced from a script is known as _kinematic_ motion. The Rigidbody component has a property called **Is Kinematic** which removes it from the control of the physics engine and allow it to be moved kinematically from a script. It is possible to change the value of **Is Kinematic** from a script to allow physics to be switched on and off for an object, but this comes with a performance overhead and should be used sparingly. -->

在某些情况下，你可能希望一个游戏对象具有刚体组件，但是不要物理引擎控制它的运动。例如，你可以想要通过脚本代码直接控制角色，同时允许触发器进行碰撞检测（请参见下面的触发器 Triggers）。这种由脚本产生的非物理运动称为 _动力学_ 运动。刚体组件有一个 **Is Kinematic** 属性，它可以把游戏对象从物理引擎中移除，并用脚本来移动。可以用脚本控制 **Is Kinematic** 的值，从而开始或关闭对象的物理行为，但这会带来性能开始，应该谨慎使用。

<!-- See the [Rigidbody](http://docs.unity3d.com/Manual/class-Rigidbody.html) and [Rigidbody 2D](http://docs.unity3d.com/Manual/class-Rigidbody2D.html) reference pages for further details about the settings and scripting options for these components. -->

有关这些组件的设置和脚本选项的更多细节，请参阅 [Rigidbody](http://docs.unity3d.com/Manual/class-Rigidbody.html) 和 [Rigidbody 2D](http://docs.unity3d.com/Manual/class-Rigidbody2D.html)  的参考页。

[Rigidbody]: http://docs.unity3d.com/Manual/class-Rigidbody.html
[Rigidbody 2D]: http://docs.unity3d.com/Manual/class-Rigidbody2D.html

<!-- ## Sleeping -->
## 休眠

<!-- When a Rigidbody is moving slower than a defined minimum linear or rotational speed, the physics engine assumes it has come to a halt. When this happens, the GameObject does not move again until it receives a collision or force, and so it is set to “sleeping” mode. This optimisation means that no processor time is spent updating the Rigidbody until the next time it is “awoken” (that is, set in motion again). -->

当刚体以低于定义的最小线性速度或最小旋转角度运动时，物理引擎会认为该刚体已经停止。此时，游戏对象被设置为『休眠』模式，不再移动，直到它接收到碰撞或作用力。这个优化意味着，在刚体被再次『唤醒』（再次处于运动中）之前，不会消耗处理器时间来更新刚体。

当刚体移动速度低于定义的最小线性或旋转速度时，物理引擎假定它已经停止。当这种情况发生时，GameObject不再移动，直到它接收到碰撞或力，因此它被设置为“睡眠”模式。此优化意味着在下一次“唤醒”（即，再次设置为运动）时，不更新刚体的处理器时间。

<!-- For most purposes, the sleeping and waking of a Rigidbody component happens transparently. However, a GameObject might fail to wake up if a Static Collider (that is, one without a Rigidbody) is moved into it or away from it by modifying the **Transform** position. This might result, say, in the Rigidbody GameObject hanging in the air when the floor has been moved out from beneath it. In cases like this, the GameObject can be woken explicitly using the WakeUp function. See the [Rigidbody](http://docs.unity3d.com/Manual/class-Rigidbody.html) and [Rigidbody 2D](http://docs.unity3d.com/Manual/class-Rigidbody2D.html) component pages for more information about sleeping. -->

对于大多数场景，刚体组件的休眠和唤醒是显而易见的。但是，如果通过修改静态碰撞器（非刚体）的 **Transform** 位置，使进入或离开一个休眠中的游戏对象，该游戏对象可能无法唤醒。例如，当游戏对象下面的地板移走时，这可能导致游戏对象悬挂在空中。在这种情况下，可以使用 WakeUp 函数来显式地唤醒游戏对象。关于休眠的更多信息参阅 [Rigidbody] 和 [Rigidbody 2D] 组件页面。

[Rigidbody]: http://docs.unity3d.com/Manual/class-Rigidbody.html
[Rigidbody 2D]: http://docs.unity3d.com/Manual/class-Rigidbody2D.html
