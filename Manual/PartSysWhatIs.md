<!-- # What is a Particle System? -->
# 什么是粒子系统？

<!-- **Particles** are small, simple images or meshes that are displayed and moved in great numbers by a particle system. Each particle represents a small portion of a fluid or amorphous entity and the effect of all the particles together creates the impression of the complete entity. Using a smoke cloud as an example, each particle would have a small smoke texture resembling a tiny cloud in its own right. When many of these mini-clouds are arranged together in an area of the scene, the overall effect is of a larger, volume-filling cloud. -->

**粒子** 是小而简单的图像或网格，由粒子系统负责显示和剧烈移动。每个粒子代表了流体或无形实体的一小部分，所有粒子一起创建实体的完整外观。以烟雾为例，每个粒子是一张微小的烟雾纹理，像小块浮云一样。当许多这种微小浮云被一起布置在场景的某个区域时，整体效果是巨大的、体积填充的云朵。

<!-- ## Dynamics of the System -->
## 系统动力学

<!-- Each particle has a predetermined lifetime, typically of a few seconds, during which it can undergo various changes. It begins its life when it is generated or _emitted_ by its particle system. The system emits particles at random positions within a region of space shaped like a sphere, hemisphere, cone, box or any arbitrary mesh. The particle is displayed until its time is up, at which point it is removed from the system. The system’s _emission rate_ indicates roughly how many particles are emitted per second, although the exact times of emission are randomized slightly. The choice of emission rate and average particle lifetime determine the number of particles in the “stable” state (ie, where emission and particle death are happening at the same rate) and how long the system takes to reach that state. -->

每个粒子的生命周期是预定好的，通常是几秒钟，在此期间它可以经历各种变化。当粒子系统生成或_射出_一个粒子时，该粒子的生命便开始了。系统在特定空间区域（形状像球形、半球形、椎体、盒形或任意网格等）内的随机位置发射例子。粒子被一直显示，直到它的时间用完，然后它被从系统中删除。系统的 _发射率_ 粗略地表示每秒钟发射的粒子数量，尽管发射的确切时间被略微随机化。发射率和粒子平均生命周期决定了『稳定』（即粒子的发射和死亡以相同速率发生）状态下粒子的粒子数量，以及系统达到这种状态所属额时间。

<!-- ## Dynamics of Particles -->
## 粒子动力学

<!-- The emission and lifetime settings affect the overall behaviour of the system but the individual particles can also change over time. Each one has a **velocity** vector that determines the direction and distance the particle moves with each frame update. The velocity can be changed by **forces** and **gravity** applied by the system itself or when the particles are blown around by a **wind zone** on a Terrain. The color, size and rotation of each particle can also change over its lifetime or in proportion to its current speed of movement. The color includes an alpha (transparency) component, so a particle can be made to fade gradually in and out of existence rather than simply appearing and disappearing abruptly. -->

发射率和粒子生命周期会影响系统的整体行为，不过单个粒子也可以随时间改变。每个粒子具有一个 **速度** 向量，决定了粒子每桢移动的方向和距离。速度可以被系统自身施加的 **力** 和 **重力** 所改变，或者，粒子被地形上的区域风吹的到处乱飞。每个粒子的颜色、大小、旋转也可以随时间改变，或者与它当前的移动速度成比例地改变。颜色包含一个透明度组件，所以，粒子可以逐渐淡入淡出，而不是简单地出现和突然消失。

<!-- Used in combination, particle dynamics can be used to simulate many kinds of fluid effects quite convincingly. For example, a waterfall can be simulated by using a thin emission shape and letting the water particles simply fall under gravity, accelerating as they go. Smoke from a fire tends to rise, expand and eventually dissipate, so the system should use an upward force on the smoke particles and increase their size and transparency over their lifetimes. -->

离子动力学可以用于相当逼真地模拟多重流体效果。例如，可以使用薄板发射形状来模拟瀑布，让水粒子在重力作用下下落，并逐渐加速。火产生的烟向上升起、膨胀并最终消散，所以系统应该在烟雾粒子上施加向上的力，并随着时间增加它们的尺寸和透明度。
