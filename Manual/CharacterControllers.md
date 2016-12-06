<!-- Unity Manual > Physics > Physics Overview > Character Controllers -->

<!-- # Character Controllers -->
# 角色控制器

<!-- The character in a first- or third-person game will often need some collision-based physics so that it doesn’t fall through the floor or walk through walls. Usually, though, the character’s acceleration and movement will not be physically realistic, so it may be able to accelerate, brake and change direction almost instantly without being affected by momentum. -->

第一人称或第三人称游戏中的角色通常需要一些基于碰撞的物理特性，以使它不会穿过地板掉落下去或穿过墙壁。角色的加速度和运动通常不是物理真实的，它可以立即加速、制动和改变方向，而不会收到动量的影响。

<!-- In 3D physics, this type of behaviour can be created using a **Character Controller**. This component gives the character a simple, capsule-shaped collider that is always upright. The controller has its own special functions to set the object’s speed and direction but unlike true colliders, a rigidbody is not needed and the momentum effects are not realistic. -->

在 3D 物理中，这种类型的行为可以使用 **角色控制器** 创建。这个组件给角色提供了简单的胶囊碰撞器，并且总是直立向上。控制器有着自己的特殊功能，可以用来设置对象的速度和方向，与真正的碰撞器不同的是，它不需要刚体，动量效果也不真实。

<!-- A character controller cannot walk through static colliders in a scene, and so will follow floors and be obstructed by walls. It can push rigidbody objects aside while moving but will not be accelerated by incoming collisions. This means that you can use the standard 3D colliders to create a scene around which the controller will walk but you are not limited by realistic physical behaviour on the character itself. -->

角色控制器无法穿过场景中的静态碰撞器，因为会沿着地板行走并被墙壁阻挡。当它移动的时候，会把刚体对象推向一旁，但是自身不受碰撞影响。也就是说，你可以用标准的 3D 碰撞器来创建场景，而角色控制器可以不受真实物理行为限制地自由行走。

<!-- You can find out more about character controllers on the reference page. -->
你可以在参考页中找到有关角色控制器额更多信息。
