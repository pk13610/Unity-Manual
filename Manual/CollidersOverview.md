<!-- > [Colliders](http://docs.unity3d.com/Manual/CollidersOverview.html) -->

<!-- Unity Manual > Physics > Physics Overview > Colliders -->

<!-- # Colliders -->
# 碰撞器

<!-- **Collider** components define the shape of an object for the purposes of physical collisions. A collider, which is invisible, need not be the exact same shape as the object’s mesh and in fact, a rough approximation is often more efficient and indistinguishable in gameplay. -->

**碰撞器** 组件定义了物体用于物理碰撞的形状。碰撞器是不可见的，并且不需要与物体网格的形状完全相同。事实上，在游戏中，粗略的近似值通常更加有有效，并且微不可查。

<!-- The simplest (and least processor-intensive) colliders are the so-called _primitive_ collider types. In 3D, these are the [Box Collider](http://docs.unity3d.com/Manual/class-BoxCollider.html), [Sphere Collider](http://docs.unity3d.com/Manual/class-SphereCollider.html) and [Capsule Collider](http://docs.unity3d.com/Manual/class-CapsuleCollider.html). In 2D, you can use the [Box Collider 2D](http://docs.unity3d.com/Manual/class-BoxCollider2D.html) and [Circle Collider 2D](http://docs.unity3d.com/Manual/class-CircleCollider2D.html). Any number of these can be added to a single object to create _compound colliders_. -->

最简单（也是最小性能开销）的碰撞器是所谓的 _基本碰撞器_。在 3D 中，包括 [盒碰撞器]、[球形碰撞器]、[胶囊碰撞器]。在 2D 中，包括 [2D 盒碰撞器]、[2D 圆形碰撞器]。可以为一个物体添加任意数量的基本碰撞器，从而创建 _复合碰撞器_。

[盒碰撞器]: http://docs.unity3d.com/Manual/class-BoxCollider.html
[球形碰撞器]: http://docs.unity3d.com/Manual/class-SphereCollider.html
[胶囊碰撞器]: http://docs.unity3d.com/Manual/class-CapsuleCollider.html
[2D 盒碰撞器]: http://docs.unity3d.com/Manual/class-BoxCollider2D.html
[2D 圆形碰撞器]: http://docs.unity3d.com/Manual/class-CircleCollider2D.html

<!-- With careful positioning and sizing, compound colliders can often approximate the shape of an object quite well while keeping a low processor overhead. Further flexibility can be gained by having additional colliders on child objects (eg, boxes can be rotated relative to the local axes of the parent object). When creating a compound collider like this, there should only be one Rigidbody component, placed on the root object in the hierarchy. -->

通过灵活地调整位置和尺寸，复合碰撞器通常能够很好地近似于物体的形状，同时保持较低的处理器开销。在子元素上添加额外的碰撞器可以获得更好的灵活性（例如，盒模型可以相对于父物体的本地坐标轴旋转）。创建这样的复合碰撞器时，应该是有且仅有一个刚体组建，并且放置在层级结构的根元素上。

<!-- Note, that primitive colliders will not work correctly with shear transforms - that means that if you use a combination of rotations and non-uniform scales in the tranform hierarchy so that the resulting shape would no longer match a primitive shape, the primitive collider will not be able to represent it correctly. -->

注意，基本碰撞器不能正确运行在 剪切变换 上 —— 这意味着，如果在变换层级中组合使用旋转和非均匀缩放，将导致它的形状不再匹配基本形状，基本形状将不能正确滴表示它。

<!-- There are some cases, however, where even compound colliders are not accurate enough. In 3D, you can use [Mesh Colliders](http://docs.unity3d.com/Manual/class-MeshCollider.html) to match the shape of the object’s mesh exactly. In 2D, the [Polygon Collider 2D](http://docs.unity3d.com/Manual/class-PolygonCollider2D.html) will generally not match the shape of the sprite graphic perfectly but you can refine the shape to any level of detail you like. These colliders are much more processor-intensive than primitive types, however, so use them sparingly to maintain good performance. Also, a mesh collider will normally be unable to collide with another mesh collider (ie, nothing will happen when they make contact). You can get around this in some cases by marking the mesh collider as **Convex** in the inspector. This will generate the collider shape as a “convex hull” which is like the original mesh but with any undercuts filled in. The benefit of this is that a convex mesh collider _can_ collide with other mesh colliders so you may be able to use this feature when you have a moving character with a suitable shape. However, a good general rule is to use mesh colliders for scene geometry and approximate the shape of moving objects using compound primitive colliders. -->

但是在某些情况下，即使是复合碰撞器也不够精确。在 3D 中，你可以使用 [网格碰撞器] 来精确匹配物体的网格形状。在 2D 中，[2D 多边形碰撞器] 通常不能完美地匹配精灵图像的形状，但是可以把细节细化任意你喜欢的程度。这些碰撞器的性能开销比基本类型更高，因此请谨慎使用它们，以保持良好的性能。另外，一个网格碰撞器通常不能与另一个网格碰撞器发生碰撞（也就是说，当她们接触时不会发生任何事情）。在某些情况下，你可以把网格碰撞器标记为 **凸状** 来克服这个问题。此时，将会『凸包』状的碰撞器形状，类似于原始网格，但是没有任何填充。这样做的好处是，一个凸状网格碰撞器 _可以_ 与其他网格碰撞器发生碰撞，所以，你可以在一个具有合适形状的运动角色上使用这个功能。不过，通常好的规则是，对场景中的几何物体使用网格碰撞器，对运动物体使用近似于它形状的复合碰撞器来。

[网格碰撞器]: http://docs.unity3d.com/Manual/class-MeshCollider.html
[2D 多边形碰撞器]: http://docs.unity3d.com/Manual/class-PolygonCollider2D.html

<!-- Colliders can be added to an object without a Rigidbody component to create floors, walls and other motionless elements of a scene. These are referred to as static colliders. In general, you should not reposition static colliders by changing the Transform position since this will impact heavily on the performance of the physics engine. Colliders on an object that _does_ have a Rigidbody are known as _dynamic colliders_. Static colliders can interact with dynamic colliders but since they don’t have a Rigidbody, they will not move in response to collisions. -->

可以在没有刚体组件的对象上添加碰撞器，从而在场景中创建地板、墙壁和其他静止元素。这些元素被称为静态碰撞器。一般来说，你不应该通过修改变换组件的位置来重新定位静态碰撞器，因为这会严重影响物理引擎的性能。具有刚体组件的物体上的碰撞器碰撞器称为 _动态碰撞器_。静态碰撞器可以和动态碰撞器交互，但是因为它没有刚体组件，所以在响应碰撞时不会移动。

<!-- The reference pages for the various collider types linked above have further information about their properties and uses. -->

前文中各种碰撞器类型的参考页链接提供了有关属性和用法的更多信息。

<!-- ## Physics materials -->
## 物理材质

<!-- When colliders interact, their surfaces need to simulate the properties of the material they are supposed to represent. For example, a sheet of ice will be slippery while a rubber ball will offer a lot of friction and be very bouncy. Although the shape of colliders is not deformed during collisions, their friction and bounce can be configured using **Physics Materials**. Getting the parameters just right can involve a bit of trial and error but an ice material, for example will have zero (or very low) friction and a rubber material with have high friction and near-perfect bounciness. See the reference pages for [Physic Material](https://docs.unity3d.com/Manual/class-PhysicMaterial.html) and [Physics Material 2D](https://docs.unity3d.com/Manual/class-PhysicsMaterial2D.html) for further details on the available parameters. Note that for historical reasons, the 3D asset is actually called **Physic Material** (without the S) but the 2D equivalent is called **Physics Material 2D** (with the S). -->

当碰撞器交互时，它们的表面需要模拟材质特性。例如，一片冰将是滑的，而一个橡胶球将提供很大的摩擦力并且非常有弹性。尽管碰撞器的形状在碰撞过程中不会变形，但是可以通过 **物理材质** 来配置它们的摩擦力和弹性。可能需要一些试验和试错才能得到正确的参数，不过可以参考常识，例如，冰面材质的摩擦力为 0（或非常低），橡胶材质具有非常高的摩擦力和近乎完美的弹性。有关可用参数的更多细节请参阅 [物理材质] 和 [2D 物理材质] 的参考页。请注意，由于历史原因，物理材质称为 **Physic Material**（没有 S），2D 物理材质称为 **Physics Material 2D**（有 S）。

[物理材质]: https://docs.unity3d.com/Manual/class-PhysicMaterial.html
[2D 物理材质]:https://docs.unity3d.com/Manual/class-PhysicsMaterial2D.html

<!-- ## Triggers -->
## 触发器


<!-- The scripting system can detect when collisions occur and initiate actions using the `OnCollisionEnter` function. However, you can also use the physics engine simply to detect when one collider enters the space of another without creating a collision. A collider configured as a **Trigger** (using the **Is Trigger** property) does not behave as a solid object and will simply allow other colliders to pass through. When a collider enters its space, a trigger will call the `OnTriggerEnter` function on the trigger object’s scripts. -->

脚本系统可以检测碰撞发生的时间，并且用 `OnCollisionEnter` 函数初始化响应行为。不过，你也可以在不产生碰撞的情况下，用物理引擎简单地检测一个碰撞器何时进入另一个碰撞器的空间。一个配置为 **触发器** 的碰撞器（使用 **Is Trigger** 属性）不会具有实体对象的行为，并且允许其他碰撞器穿过它。当一个碰撞器进入触发器的空间时，将会调用触发器上脚本的 `OnTriggerEnter` 函数。

<!-- ## Script actions taken on collision -->
## 碰撞时执行的脚本操作


<!-- When collisions occur, the physics engine calls functions with specific names on any scripts attached to the objects involved. You can place any code you like in these functions to respond to the collision event. For example, you might play a crash sound effect when a car bumps into an obstacle. -->

当碰撞发生时，物理引擎将会在相关对象绑定的所有脚本上调用特定名称的函数。可以在这些函数中放置任意代码来响应碰撞事件。例如，当汽车撞到障碍物时，可能会播放一段碰撞音效。

<!-- On the first physics update where the collision is detected, the `OnCollisionEnter` function is called. During updates where contact is maintained, `OnCollisionStay` is called and finally, `OnCollisionExit` indicates that contact has been broken. Trigger colliders call the analogous `OnTriggerEnter`, `OnTriggerStay` and `OnTriggerExit` functions. Note that for 2D physics, there are equivalent functions with **2D** appended to the name, eg, `OnCollisionEnter2D`. Full details of these functions and code samples can be found on the Script Reference page for the [MonoBehaviour](https://docs.unity3d.com/ScriptReference/MonoBehaviour.html) class. -->

在检测到碰撞的第一次物理更新中，`OnCollisionEnter` 函数被调用。在连接尚未断开的期间，`OnCollisionStay` 被调用，最后调用 `OnCollisionExit`，表示连接已经断开。触发器调用类似的 `OnTriggerEnter`、`OnTriggerStay` 和 `OnTriggerExit` 函数。请注意，对于 2D 物理，提供了等价的函数，但是函数名后附加了 **2D**，例如 `OnCollisionEnter2D`。这些函数的完整信息和代码示例可以在 [MonoBehaviour](https://docs.unity3d.com/ScriptReference/MonoBehaviour.html) 类的脚本参考页中找到。

<!-- With normal, non-trigger collisions, there is an additional detail that at least one of the objects involved must have a non-kinematic Rigidbody (ie, Is Kinematic must be switched off). If both objects are kinematic Rigidbodies then `OnCollisionEnter`, etc, will not be called. With trigger collisions, this restriction doesn’t apply and so both kinematic and non-kinematic Rigidbodies will prompt a call to `OnTriggerEnter` when they enter a trigger collider. -->

对于非触发器碰撞，还有一个细节需要注意，至少一个相关对象必须具有非运动学刚体（即必须关闭 Is Kinematic）。如果两个物体都是运动学刚体，那么 `OnCollisionEnter` 等函数不会被调用。使用触发器碰撞时，则不受此限制，因为，当运动学刚体和非运动学刚体进入一个触发器时，将会调用 `OnTriggerEnter` 函数。

<!-- ## Collider interactions -->
## 碰撞器交互

<!-- Colliders interact with each other differently depending on how their [Rigidbody components](https://docs.unity3d.com/Manual/RigidbodiesOverview.html) are configured. The three important configurations are the Static Collider (ie, no Rigidbody is attached at all), the Rigidbody Collider and the Kinematic Rigidbody Collider. -->

碰撞器之间的交互行为依赖于 [刚体组件] 的配置。有三种重要配置：静态碰撞器（没有附加刚体）、刚体碰撞器和运动学刚体碰撞器。

[刚体组件]: https://docs.unity3d.com/Manual/RigidbodiesOverview.html

<!-- ### Static Collider -->
### 静态碰撞器


<!-- This is a GameObject that has a Collider but no Rigidbody. Static colliders are used for level geometry which always stays at the same place and never moves around. Incoming rigidbody objects will collide with the static collider but will not move it. -->

一个具有碰撞器但是没有刚体的游戏对象。静态碰撞器用于水平集合物体，它们总是停留在相同的位置，从不移动。刚体物体将会和静态碰撞器发生碰撞，但是不会移动静态碰撞器。

<!-- The physics engine assumes that static colliders never move or change and can make useful optimizations based on this assumption. Consequently, static colliders should not be disabled/enabled, moved or scaled during gameplay. If you do change a static collider then this will result in extra internal recomputation by the physics engine which causes a major drop in performance. Worse still, the changes can sometimes leave the collider in an undefined state that produces erroneous physics calculations. For example a raycast against an altered Static Collider could fail to detect it, or detect it at a random position in space. Furthermore, Rigidbodies that are hit by a moving static collider will not necessarily be “awoken” and the static collider will not apply any friction. For these reasons, only colliders that are Rigidbodies should be altered. If you want a collider object that is not affected by incoming rigidbodies but can still be moved from a script then you should attach a Kinematic Rigidbody component to it rather than no Rigidbody at all. -->

物理引擎假定静态碰撞器从不移动或改变，基于这一假设可以执行有效的优化。因此，在游戏过程中，不应该禁用、启动、移动或缩放静态碰撞器。如果改变了静态碰撞器，将会导致物理引擎进行额外的内部运算，从而导致性能大幅下降。更糟的是，有时还会导致静态碰撞器处于未知状态，产生错误的物理运算。例如，可能无法检测向被改静态碰撞器发射的射线，或者随机返回空间中的一个位置。此外，被正在移动的静态碰撞器碰撞的刚体不一定会被『唤醒』，并且静态碰撞器也不会施加任何摩擦力。由于这些原因，只有刚体碰撞器才能被改变。如果想要一个不受其他刚体影响、并且可以用脚本移动的碰撞器对象，那么，应该绑定一个运动学刚体组件，而不是不绑定刚体。

<!-- ### Rigidbody Collider -->
### 刚体碰撞器


<!-- This is a GameObject with a Collider and a normal, non-kinematic Rigidbody attached. Rigidbody colliders are fully simulated by the physics engine and can react to collisions and forces applied from a script. They can collide with other objects (including static colliders) and are the most commonly used Collider configuration in games that use physics. -->

一个具有碰撞器和非运动学刚体的游戏对象。刚体碰撞器完全由物理引擎模拟，并且可以响应碰撞和脚本施加的作用力。刚体碰撞器可以和其他对象（包括静态碰撞器）发生碰撞，是游戏中最常用的碰撞器配置。

<!-- ### Kinematic Rigidbody Collider -->
###运动学刚体碰撞器

<!-- This is a GameObject with a Collider and a kinematic Rigidbody attached (ie, the IsKinematic property of the Rigidbody is enabled). You can move a kinematic rigidbody object from a script by modifying its Transform Component but it will not respond to collisions and forces like a non-kinematic rigidbody. Kinematic rigidbodies should be used for colliders that can be moved or disabled/enabled occasionally but that should otherwise behave like static colliders. An example of this is a sliding door that should normally act as an immovable physical obstacle but can be opened when necessary. Unlike a static collider, a moving kinematic rigidbody will apply friction to other objects and will “wake up” other rigidbodies when they make contact. -->

一个具有碰撞器和运动学刚体（（即启动了 IsKinematic 属性）的游戏对象。脚本可以修改变换主见，从而移动运动学刚体对象，但是不会响应碰撞和作用力，就像非运动学刚体一样。运动学刚体应该用于偶尔移动、禁用或启用的碰撞器，但是在其他情况下，它应该像静态碰撞器那样运行。例如一扇滑动门，通常情况下，它作为不可移动的物理障碍，但是需要时可以被打开。与静态碰撞器不同，一个移动的运动学刚体碰撞器将对其他对象施加摩擦力，并在碰撞时唤醒其他刚体对象。

<!-- Even when immobile, kinematic rigidbody colliders have different behavior to static colliders. For example, if the collider is set to as a trigger then you also need to add a rigidbody to it in order to receive trigger events in your script. If you don’t want the trigger to fall under gravity or otherwise be affected by physics then you can set the IsKinematic property on its rigidbody. -->

即使在不移动时，运动学刚体碰撞器的行为也与静态碰撞器不同。例如，如果静态碰撞器被设置为是一个触发器，那么为了在脚本中接收触发事件，你还需要为它添加一个刚体组件。如果希望触发器不受到重力或其他物理现象的影响，那么你可以在刚体组件上启用 IsKinematic 属性。

<!-- A Rigidbody component can be switched between normal and kinematic behavior at any time using the IsKinematic property. -->

通过 IsKinematic 属性，一个刚体组件可以随时在正常和运行学之间切换。

<!-- A common example of this is the “ragdoll” effect where a character normally moves under animation but is thrown physically by an explosion or a heavy collision. The character’s limbs can each be given their own Rigidbody component with IsKinematic enabled by default. The limbs will move normallly by animation until IsKinematic is switched off for all of them and they immediately behave as physics objects. At this point, a collision or explosion force will send the character flying with its limbs thrown in a convincing way. -->

一个常见的例子是『布偶』效果，正常情况下，一个角色在动画的控制下移动，但是可以被爆炸和重击抛出。这个角色的四肢各自被赋予刚体组件，并且默认启用 IsKinematic 属性。在 IsKinematic 关闭前，四肢将在动画的控制下移动，在关闭 IsKinematic 后，四肢立即表现出物理对象的行为。这个时候，碰撞或爆炸力将击飞这个角色，并且，它的四肢以逼真的方式被抛出。

<!-- ## Collision action matrix -->
## 碰撞行为矩阵

<!-- When two objects collide, a number of different script events can occur depending on the configurations of the colliding objects’ rigidbodies. The charts below give details of which event functions are called based on the components that are attached to the objects. Some of the combinations only cause one of the two objects to be affected by the collision, but the general rule is that physics will not be applied to an object that doesn’t have a Rigidbody component attached. -->

当两个对象碰撞时，根据刚体的配置，可能发生发生许多不同的脚本事件。下面的图表列出了基于对象组件调用事件函数的详细信息。某些组合只会导致两个对象中的一个被碰撞所影响，但一般规则是，没有附加刚体组件的对象不会应用物理现象。

> 译注：矩阵表格见 [原文](https://docs.unity3d.com/Manual/CollidersOverview.html)。