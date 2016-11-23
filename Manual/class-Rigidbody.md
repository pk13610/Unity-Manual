> [Rigidbody](http://docs.unity3d.com/Manual/class-Rigidbody.html)

Unity Manual > Physics > 3D Physics Reference > Rigidbody

# Rigidbody

[SWITCH TO SCRIPTING](http://docs.unity3d.com/ScriptReference/Rigidbody.html)

**Rigidbodies** enable your **GameObjects** to act under the control of physics. The Rigidbody can receive forces and torque to make your objects move in a realistic way. Any GameObject must contain a Rigidbody to be influenced by gravity, act under added forces via scripting, or interact with other objects through the NVIDIA PhysX physics engine.

**Rigidbody** 组件使游戏对象 **GameObject** 受物理系统的影响。Rigidbody 可以接受力和扭矩，从而以真实的方式移动。任何希望受重力影响的 GameObject 必须包含一个 Rigidbody 组件，可以通过脚本施加力，或者通过 NVIDIA PhysX 物理引擎与其他对象交互。

![](http://docs.unity3d.com/uploads/Main/Inspector-Rigidbody.png)

## Properties

> Property:   Function:

**Mass**    The mass of the object (in kilograms by default).

**质量** 游戏对象的质量（默认单位为公斤）。

**Drag**    How much air resistance affects the object when moving from forces. 0 means no air resistance, and infinity makes the object stop moving immediately.

**空气阻力** 当游戏对象受到作用力移动时受到的空气阻力。0 表示没有空气阻力，无限大会使立即停止移动。

**Angular Drag**    How much air resistance affects the object when rotating from torque. 0 means no air resistance. Note that you cannot make the object stop rotating just by setting its Angular Drag to infinity.

**旋转空气阻力** 当游戏对象受到扭矩旋转时受到的空气阻力。0 表示没有空气阻力。注意，设置为无限大并不能使游戏对象停止旋转。

**Use Gravity** If enabled, the object is affected by gravity.

**开始重力** 如果开启，游戏对象受重力影响。

**Is Kinematic**    If enabled, the object will not be driven by the physics engine, and can only be manipulated by its Transform. This is useful for moving platforms or if you want to animate a Rigidbody that has a HingeJoint attached.

**主动运行** 如果开始，游戏对象将不受物理引擎影响，只能被它的 Transform 影响。可以用于移动地面，或者为附加了 HingeJoint 的 Rigidbody 应用动画。

**Interpolate** Try one of the options only if you are seeing jerkiness in your Rigidbody’s movement.
    - **None**  No Interpolation is applied.
    - **Interpolate**   Transform is smoothed based on the Transform of the previous frame.
    - **Extrapolate**   Transform is smoothed based on the estimated Transform of the next frame.

**运动篡改** 如果 Rigidbody 的移动不连贯，那么试试下面的选项。

平滑的 Transform，基于前一桢 Transform。
平滑的 Transform，基于下一桢 Transform 的预测。

**Collision Detection** Used to prevent fast moving objects from passing through other objects without detecting collisions.
    - Discrete  Use Discreet collision detection against all other colliders in the scene. Other colliders will use Discreet collision detection when testing for collision against it. Used for normal collisions (This is the default value).
    - Continuous    Use Discrete collision detection against dynamic colliders (with a rigidbody) and continuous collision detection against static MeshColliders (without a rigidbody). Rigidbodies set to Continuous Dynamic will use continuous collision detection when testing for collision against this rigidbody. Other rigidbodies will use Discreet Collision detection. Used for objects which the Continuous Dynamic detection needs to collide with. (This has a big impact on physics performance, leave it set to Discrete, if you don’t have issues with collisions of fast objects)
    - Continuous Dynamic    Use continuous collision detection against objects set to Continuous and Continuous Dynamic Collision. It will also use continuous collision detection against static MeshColliders (without a rigidbody). For all other colliders it uses discreet collision detection. Used for fast moving objects.

**碰撞检测** 用于阻止快速运动的物体穿过其他物理，导致碰撞检测失效。

    - 离散检测 以预测的方式检测游戏对象与场景中其他碰撞器的碰撞。其他碰撞器也使用预测的方式检测与该游戏对象的碰撞。用于一般碰撞，这是默认值。
    - 连续检测 以预测方式检测与动态碰撞器（含有 Rigidbody）的碰撞，以连续的方式检测与静态碰撞器（不含有 Rigidbody）的碰撞。被设置为 连续动态检测 的 Rigidbody，将以连续碰撞检测的方式检测碰撞，其他 Rigidbody 将使用离散检测。（对物理引擎的性能有重大影响，如果快速移动的游戏对象没有问题，就设置为 离散检测。
    - 持续动态检测 以连续的方式检测碰撞。即使对于静态碰撞器（不含有 Rigidbody），也采用持续碰撞检测。对于其他碰撞器，使用离散检测。用于快速移动的游戏对象。

**Constraints** Restrictions on the Rigidbody’s motion:-
    - Freeze Position   Stops the Rigidbody moving in the world X, Y and Z axes selectively.
    - Freeze Rotation   Stops the Rigidbody rotating around the local X, Y and Z axes selectively.

**约束** 限制 Rigidbody 的动作。

    冻结位置 在选择的 X、Y、Z 坐标轴上停止 Rigidbody 的移动。
    冻结渲染 在选择的 X、Y、Z 坐标轴上停止 Rigidbody 的旋转。

## Details
## 详解

Rigidbodies allow your GameObjects to act under control of the physics engine. This opens the gateway to realistic collisions, varied types of joints, and other very cool behaviors. Manipulating your GameObjects by adding forces to a Rigidbody creates a very different feel and look than adjusting the Transform Component directly. Generally, you shouldn’t manipulate the Rigidbody and the Transform of the same GameObject - only one or the other.

Rigidbody 使你的游戏对象置于物理引擎之下。将开启真实碰撞、各种类型的链接，以及其他很酷的行为。为你的游戏对象添加 Rigidbody，然后添加作用力，将创建与直接修改 Transform 组件不同的感觉。通常情况下，你不应该在同一个游戏对象上同时修改 Rigidbody 和 Transform —— 一次只修改一个。

The biggest difference between manipulating the Transform versus the Rigidbody is the use of forces. Rigidbodies can receive forces and torque, but Transforms cannot. Transforms can be translated and rotated, but this is not the same as using physics. You’ll notice the distinct difference when you try it for yourself. Adding forces/torque to the Rigidbody will actually change the object’s position and rotation of the Transform component. This is why you should only be using one or the other. Changing the Transform while using physics could cause problems with collisions and other calculations.

修改 Transform 和 Rigidbody 的最大不同之处在于作用力的使用。Rigidbody 可以接受作用力和扭矩，但是 Transform 不行。虽然 Transform 也可以变形和旋转，但是与使用物理引擎完全不同。当你自己试的时候，就会发现这一明显不同。为 Rigidbody 添加作用力或扭矩，将会真实地改变 Transform 组件的位置和旋转。这就是为什么你应该只使用其中一个。在使用物理引擎的同时改变 Transform 可能会在碰撞时和其他计算时引发错误。

Rigidbodies must be explicitly added to your GameObject before they will be affected by the physics engine. You can add a Rigidbody to your selected object from Components->Physics->Rigidbody in the menu. Now your object is physics-ready; it will fall under gravity and can receive forces via scripting, but you may need to add a Collider or a Joint to get it to behave exactly how you want.

Rigidbody 必须明确地添加到游戏对象，才会受物理引擎的影响。通过菜单 Components -> Physics -> Rigidbody，你可以添加一个 Rigidbody 组件到选中的游戏对象；它将在重力的作用下下落，并且可以通过脚本施加作用力；为了达到你想要的行为，你可以还需要添加一个碰撞器 Collider 或连接器 Joint。

### Parenting
### 父子关系

When an object is under physics control, it moves semi-independently of the way its transform parents move. If you move any parents, they will pull the Rigidbody child along with them. However, the Rigidbodies will still fall down due to gravity and react to collision events.

当一个游戏对象受物理引擎的控制时，它的移动方式是半独立的，因为会受到父对象移动的影响。如果移动了父对象，它的 Rigidbody 子对象也会被移动。不过，Rigidbody 子对象依然会因为重力而下落，依然会响应碰撞事件。

### Scripting
### 脚本化

To control your Rigidbodies, you will primarily use scripts to add forces or torque. You do this by calling [AddForce()](http://docs.unity3d.com/ScriptReference/Rigidbody.AddForce.html) and [AddTorque()](http://docs.unity3d.com/ScriptReference/Rigidbody.AddTorque.html) on the object’s Rigidbody. Remember that you shouldn’t be directly altering the object’s Transform when you are using physics.

控制 Rigidbody 的主要方式是通过脚本添加作用力或扭矩，即调用游戏对象上 Rigidbody 组件的 `AddForce()` 和 `AddTorque()`。记住，在使用物理引擎的时候，你不应该直接修改游戏对象的 Transform 组件。

### Animation
### 动画

For some situations, mainly creating ragdoll effects, it is neccessary to switch control of the object between animations and physics. For this purpose Rigidbodies can be marked [isKinematic](http://docs.unity3d.com/ScriptReference/Rigidbody-isKinematic.html). While the Rigidbody is marked **isKinematic**, it will not be affected by collisions, forces, or any other part of the physics system. This means that you will have to control the object by manipulating the [Transform](http://docs.unity3d.com/Manual/class-Transform.html) component directly. Kinematic Rigidbodies will affect other objects, but they themselves will not be affected by physics. For example, Joints which are attached to Kinematic objects will constrain any other Rigidbodies attached to them and Kinematic Rigidbodies will affect other Rigidbodies through collisions.

在某些情况下，主要是创建 Ragdoll 效果时，对游戏对象的控制，需要在动画系统和物理引擎之间切换。为了达到这个目的，额可以选中 Rigidbody 的 `isKinematic` 选项。当一个 Rigidbody 被标记为 **isKinematic** 事，它将不再受到碰撞、作用力和任何物理引擎功能的影响。这意味着，你将需要通过直接修改 Transform 组件来控制对象。Kinematic Rigidbody 依然会影响其他游戏对象，但是它们自身不收物理引擎的影响。举个例子，Kinematic 游戏对象上的 连接 将驱动其他任意绑定的 Rigidbody，Kinematic Rigidbody 将通过碰撞影响其他 Rigidbody。

### Colliders
### 碰撞器

Colliders are another kind of component that must be added alongside the Rigidbody in order to allow collisions to occur. If two Rigidbodies bump into each other, the physics engine will not calculate a collision unless both objects also have a Collider attached. Collider-less Rigidbodies will simply pass through each other during physics simulation.

碰撞骑 Collider 是另一种组件，必须随 Rigidbody 一起添加，才能使碰撞检测生效。如果只是两个 Rigidbody 碰撞在一起，物理引擎不会计算碰撞，除非这两个游戏对象都附加了碰撞器 Collider。在模拟物理效果时，缺少碰撞器 Collider 的 Rigidbody 将会简单的彼此穿过。

![Colliders define the physical boundaries of a Rigidbody](http://docs.unity3d.com/uploads/Main/RigidbodyandCollider.png)
> Colliders define the physical boundaries of a Rigidbody

> 碰撞器定义了 Rigidbody 的物理边界。

Add a Collider with the **Component -> Physics menu**. View the Component Reference page of any individual Collider for more specific information:

通过菜单 **Component -> Physics** 添加一个碰撞器。查看每个碰撞器组件的文档获取更多细节信息：

* [Box Collider](http://docs.unity3d.com/Manual/class-BoxCollider.html) - primitive shape of a cube
* [Sphere Collider](http://docs.unity3d.com/Manual/class-SphereCollider.html) - primitive shape of a sphere
* [Capsule Collider](http://docs.unity3d.com/Manual/class-CapsuleCollider.html) - primitive shape of a capsule
* [Mesh Collider](http://docs.unity3d.com/Manual/class-MeshCollider.html) - creates a collider from the object’s mesh, cannot collide with another Mesh Collider
* [Wheel Collider](http://docs.unity3d.com/Manual/class-WheelCollider.html) - specifically for creating cars or other moving vehicles
* [Terrain Collider](http://docs.unity3d.com/Manual/class-TerrainCollider.html) - handles collision with Unity’s terrain system

盒子碰撞器，球形碰撞器，胶囊碰撞器，网格碰撞器，车轮碰撞器，地形碰撞器。

### Compound Colliders
### 混合碰撞器

Compound Colliders are combinations of primitive Colliders, collectively acting as a single Collider. They come in handy when you have a model that would be too complex or costly in terms of performance to simulate exactly, and want to simulate the collision of the shape in an optimal way using simple approximations. To create a Compound Collider, create child objects of your colliding object, then add a Collider component to each child object. This allows you to position, rotate, and scale each Collider easily and independently of one another. You can build your compound collider out of a number of primitive colliders and/or convex mesh colliders.

混合碰撞器是原生碰撞器的组合，共同组成一个碰撞器。如果你有一个非常复杂或非常消耗性能的模型，以至于无法精确地模拟它的物理效果，而你只是想要以一种优化的方式，简单地、近似地模拟模型的碰撞，那么，可以用混合碰撞器方便地实现。为了创建一个混合碰撞器，你需要为碰撞对象添加子对象，然后为每一个子对象添加一个碰撞器组件 Collider。你可以很容易地定位、旋转、缩放每个碰撞器，而它们之间相互独立、互不干扰。你可以用若干原生碰撞器和凸体网格碰撞器创建你自己的混合碰撞器。

![A real-world Compound Collider setup](http://docs.unity3d.com/uploads/Main/CompoundCollider.png)
> A real-world Compound Collider setup

> 一个真实的混合碰撞器装置。

In the above picture, the Gun Model GameObject has a Rigidbody attached, and multiple primitive Colliders as child GameObjects. When the Rigidbody parent is moved around by forces, the child Colliders move along with it. The primitive Colliders will collide with the environment’s Mesh Collider, and the parent Rigidbody will alter the way it moves based on forces being applied to it and how its child Colliders interact with other Colliders in the Scene.

在上面的图片中，枪支模型附加了一个 Rigidbody 组件，多个原生碰撞器作为子对象。当父级 Rigidbody 受力移动时，子级 Rigidbody 也随之移动。这些原生碰撞器将和环境中的网格碰撞器发生碰撞，子级碰撞器与场景中其他碰撞器的交互，将会修改父级 Rigidbody 的移动方式。

Mesh Colliders can’t normally collide with each other. If a Mesh Collider is marked as **Convex**, then it can collide with another Mesh Collider. The typical solution is to use primitive Colliders for any objects that move, and Mesh Colliders for static background objects.

默认情况下，网格碰撞器彼此之间不能发生碰撞，除非被标记为 **凸体 Convex**，才能彼此碰撞。典型的解决方案是，移动的游戏对象使用原生碰撞器，静态背景对象使用网格碰撞器。

### Continuous Collision Detection
### 连续碰撞检测

Continuous collision detection is a feature to prevent fast-moving colliders from passing each other. This may happen when using normal (**Discrete**) collision detection, when an object is one side of a collider in one frame, and already passed the collider in the next frame. To solve this, you can enable continuous collision detection on the rigidbody of the fast-moving object. Set the collision detection mode to Continuous to prevent the rigidbody from passing through any static (ie, non-rigidbody) MeshColliders. Set it to **Continuous Dynamic** to also prevent the rigidbody from passing through any other supported rigidbodies with collision detection mode set to **Continuous** or **Continuous Dynamic**. Continuous collision detection is supported for Box-, Sphere- and CapsuleColliders. Note that continuous collision detection is intended as a safety net to catch collisions in cases where objects would otherwise pass through each other, but will not deliver physically accurate collision results, so you might still consider decreasing the fixed Time step value in the TimeManager inspector to make the simulation more precise, if you run into problems with fast moving objects.

连续碰撞检测功能用于阻止快速移动的碰撞器彼此穿透。当使用默认的 **Discrete** 碰撞检测时，就可能发生这种情况，在上一桢，游戏对象还是碰撞器的一侧，到了下一桢，游戏对象已经穿过了碰撞器。为了解决这个问题，你可以为快速移动物体的 Rigidbody 组件开启连续碰撞检测。设置碰撞检测模式为 Continuous，可以阻止 Rigidbody 穿过任何静态（没有 Rigidbody 组件）网格碰撞器。设置为 Continuous Dynamic，可以阻止该 Rigidbody 穿够任何碰撞检测模式为 **Continuous** 或 **Continuous Dynamic** 的 Rigidbody。连续碰撞检测支持盒子碰撞器、球形碰撞器和胶囊碰撞器。注意，连续碰撞检测是为了在游戏对象可能互相穿透的情况下安全地捕获碰撞，并不能精确地返回物理碰撞信息，所以，如果快速移动的游戏对象仍然有问题，你可能需要在 TimeManager 视图中降低固定时间步长，从而让模拟过程更加精确。


## Use the right size
## 使用正确的尺寸

The size of the your GameObject’s mesh is much more important than the mass of the Rigidbody. If you find that your Rigidbody is not behaving exactly how you expect - it moves slowly, floats, or doesn’t collide correctly - consider adjusting the scale of your mesh asset. Unity’s default unit scale is 1 unit = 1 meter, so the scale of your imported mesh is maintained, and applied to physics calculations. For example, a crumbling skyscraper is going to fall apart very differently than a tower made of toy blocks, so objects of different sizes should be modeled to accurate scale.

游戏对象网格的尺寸比 Rigidbody 的质量更加重要。如果发现 Rigidbody 的行为不符合你的预期 —— 移动缓慢、漂浮或不能正确碰撞 —— 那么考虑修改网格的尺寸。Unity 的默认单位尺寸是 1 个单位等于 1 米，所以，你导入的网格需要被修改，才能应用到物理计算中。例如，一栋塌陷的摩天大楼将解体下落，而用砖块搭建的塔则完全不同，所以不同尺寸的对象应该修改为实际的尺寸。

If you are modeling a human make sure the model is around 2 meters tall in Unity. To check if your object has the right size compare it to the default cube. You can create a cube using **GameObject > 3D Object > Cube**. The cube’s height will be exactly 1 meter, so your human should be twice as tall.

如果你正在为一个人物建模，请确保模型在 Unity 中的高度约为 2 米。为了检测游戏对象的尺寸是否正确，可以和默认的立方体相比较。通过菜单 **GameObejct > 3D Object > Cube" 创建一个立方体，它的高度是标准 1 米，因此任务模型应该是它的两倍高度。

If you aren’t able to adjust the mesh itself, you can change the uniform scale of a particular mesh asset by selecting it in **Project View** and choosing **Assets->Import Settings…** from the menu. Here, you can change the scale and re-import your mesh.

你无法单独修改网格，你可以在 Project 视图中选中某个网格资源，然后通过菜单 **Aseets > Import Settings...** 修改缩放比例。然后，你可以修改尺寸，并重新导入网格。

If your game requires that your GameObject needs to be instantiated at different scales, it is okay to adjust the values of your Transform’s scale axes. The downside is that the physics simulation must do more work at the time the object is instantiated, and could cause a performance drop in your game. This isn’t a terrible loss, but it is not as efficient as finalizing your scale with the other two options. Also keep in mind that non-uniform scales can create undesirable behaviors when Parenting is used. For these reasons it is always optimal to create your object at the correct scale in your modeling application.

如果游戏中需要把一个游戏对象初始化为不同的尺寸，可以修改 Transform 组件的 Scale 坐标轴。缺点是，物理引擎在游戏对象初始化的时候，需要做更多的工作，可能导致游戏性能下降。这并不是一项严重的消耗，但是不如前面的步骤，前面的步骤可以更高效地修改尺寸。你要始终注意，当有父级对象的时候，不标准的尺寸可能导致不和预期的行为。因为这次原因，最理想的方案是，用建模程序中正确的尺寸创建游戏对象。

## Hints
## 提示

* The relative **Mass** of two Rigidbodies determines how they react when they collide with each other.
* Making one Rigidbody have greater Mass than another does not make it fall faster in free fall. Use **Drag** for that.
* A low **Drag** value makes an object seem heavy. A high one makes it seem light. Typical values for Drag are between .001 (solid block of metal) and 10 (feather).
* If you are directly manipulating the Transform component of your object but still want physics, attach a Rigidbody and make it Kinematic.
* If you are moving a GameObject through its Transform component but you want to receive Collision/Trigger messages, you must attach a Rigidbody to the object that is moving.
* You cannot make an object stop rotating just by setting its Angular Drag to infinity.

* 两个 Rigidbody 的相对质量 Mass 决定了它们碰撞后的行为。
* 给一个 Rigidbody 设置更大的质量 Mass，并不会让它下落的更快。应该为它设置阻力 Drap。
* 小阻力 Drap 会让一个游戏对象看起来更重。大阻力会让一个游戏对象看起来更轻。阻力 Drap 的典型值介于 .001（金属固体）和 10（羽毛）之间。
* 如果你直接修改了游戏对象的Transform 组件，但是还想要物理效果，那么附加一个 Rigidbody 组件，并把它设置为 Kinematic。
* 如果你正在通过游戏对象的 Transform 组件来移动物体，但是希望接收碰撞或触发消息，你必须为之再附加一个 Rigidbody 组件。
* 设置扭矩阻力 Angular Drap 为无限大，并不能使一个游戏对象停止旋转。
