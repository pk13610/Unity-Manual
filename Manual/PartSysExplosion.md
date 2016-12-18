<!-- # A Simple Explosion -->
# 简单的爆炸

<!-- You can use a particle system to create a convincing explosion but the dynamics are perhaps a little more complicated than they seem at first. At its core, an explosion is just an outward burst of particles but there are a few simple modifications you can apply to make it look much more realistic. -->

你可以使用粒子系统创建一个逼真的爆炸效果，但是其中的动力学可能有些复杂。本质上，爆炸不过是向外的粒子脉冲（爆发），不过你可以做一些简单的修改，让爆炸看起来更逼真。

![A particle system explosion during development](http://docs.unity3d.com/uploads/Main/PartSysExpScreenshot.png)
<!-- > A particle system explosion during development -->
> 开发阶段的粒子系统爆炸

<!-- ## Timeline of a Particle -->
## 粒子的时间轴

<!-- A simple explosion produces a ball of flame that expands outward rapidly in all directions. The initial burst has a lot of energy and is therefore very hot (ie, bright) and moves very fast. This energy quickly dissipates which results in the expansion of flame slowing down and also cooling down (ie, getting less bright). Finally, as all the fuel is burned up, the flames will die away and soon disappear completely. -->

一个简单的爆炸会产生一个在所有方向上迅速向外膨胀的火焰球。爆炸的初始阶段具有巨大的能量，因此非常帜热（即明亮），并且火焰非常快速地移动。然后，能量快速消散，导致火焰的膨胀减慢和冷却（即变得不明亮）。最终，随着所有燃料被烧尽，火焰将减弱，并且很快完全消失。

<!-- An explosion particle will typically have a short lifetime and you can vary several different properties over that lifetime to simulate the effect. The particle will start off moving very fast but then its speed should reduce greatly as it moves away from the centre of the explosion. Also, the color should start off bright but then darken and eventually fade to transparency. Finally, reducing the particle’s size over its lifetime will give the effect of the flames dispersing as the fuel is used up. -->

爆炸粒子的生命周期通常很短，你可以在其生命周期中改变多个不同属性，以模拟这种效果。粒子的初始移动速度非常快，然后随着远离爆炸中心，它的速度将急剧降低。另外，颜色应该从明亮开始，然后变暗，最终逐渐变淡直至透明。最后，随着生命周期减小粒子的尺寸，将产生火焰因燃料耗尽而消散的效果。

<!-- ## Implementation -->
## 实现

<!-- Starting with the default particle system object (menu: **GameObject > Create General > Particle System**), go to the _Shape_ module and set the emitter shape to a small _Sphere_, say about 0.5 units in radius. The particles in the standard assets include a material called _Fire Add_ which is very suitable for explosions (menu: **Assets > Import Package > Particles**). You can set this material for the system using the _Renderer_ module. With the _Renderer_ open, you should also disable _Cast Shadows_ and _Receive Shadows_ since the explosion flames are supposed to give out light rather than receive it. -->

从默认的粒子系统对象开始（菜单：**GameObject > Create General > Particle System**），找到 _形状 Shape_ 模块，设置发射形状为一个小 _球 Sphere_，并设置半径为 0.5 单位。粒子标准资源包中包含了一个名为 _Fire Add_ 的材质，非常适合用于爆炸（菜单：**Assets > Import Package > Particles**）。你可以使用 _Renderer_ 模块为粒子系统设置材质。展开 _Renderer_ 后，还应该禁用 _投射阴影 Cast Shadows_ 和 _接收阴影 Receive Shadows_，因为爆炸的火焰应该发射光而不是接收光。

<!-- At this stage, the system looks like lots of little fireballs being thrown out from a central point. The explosion should, of course, create a burst with lots of particles all at once. In the _Emission_ module, you can set the _Rate_ value to zero and add a single _Burst_ of particles at time zero. The number of particles in the burst will depend on the size and intensity you want your explosion to have but a good starting point is about fifty particles. With the burst set up, the system is now starting to look much more like and explosion but it is rather slow and the flames seem to hang around for a long time. In the Particle System module (which will have the same name as the GameObject, eg, “Explosion”), set both the _Duration_ of the system and the _Start Lifetime_ of the particles to two seconds. -->

在这个阶段，粒子系统看起来像从中心点抛出了许多小火球。爆炸当然应该立即产生大量的粒子脉冲。在 _发射 Emission_ 模块，你可以设置 _速率 Rate_ 为 0，并在时间 0 点添加一个单独的粒子 _脉冲 Burst_。该脉冲中的粒子数量取决于暴躁的大小和强度，不过，开始时最好设置为 50 个粒子。设置好这个脉冲后，现在粒子系统开始看起来更像是爆炸了，但是它相当缓慢，并且火焰看起来长时间炫富。在粒子系统模块中（与游戏对象同名，例如 Explosion），设置 _系统持续时间 Duration_ 和 _粒子生命周期 Start Lifetime_ 为 2 秒。

<!-- You can also use the _Size Over Lifetime_ module to create the effect of the flames using up their fuel. Set the size curve using the “ramp down” preset (ie, the size starts off at 100% and reduces to zero. To make the flames darken and fade, enable the _Color Over Lifetime_ module and set the gradient to start with white at the left and finish with black at the right. Since the _Fire Add_ material uses and additive shader for rendering, the darkness of the color property also controls the transparency of the particle; the flame’s will become fully transparent as the color fades to black. Also, the additive material allows the brightness of particles to “add” together as they are drawn on top of each other. This helps to further enhance the impression of a bright flash at the start of the explosion when the particles are all close together. -->

你也可以使用 _随生命周期改变大小 Size Over Lifetime_ 模块创建火焰耗尽燃料的效果。设置大小曲线为预设的『斜降 ramp down』（即，大小从 100% 开始，然后减小为 0）。为了使火焰变暗和变淡，开启 _随生命周期改变颜色 Color Over Lifetime_ 模块，设置颜色渐变，从左侧的白色开始，到右侧的黑色结束。因为材质 _Fire Add_ 材质使用了 Additive 着色器，所以颜色属性的明暗度也控制了粒子的透明度；当颜色渐变为黑色时，火焰将变得完全透明。并且，当绘制的粒子彼此重叠时，Additive 材质支持粒子亮度的叠加。这有助于增强爆炸开始时的明亮闪光，此时全部粒子紧靠在一起。

<!-- As it stands, the explosion is taking shape but it looks as though it is happening out in space. The particles get thrown out and travel a long distance at constant speed before fading. If your game is set in space then this might be the exact effect you want. However, an explosion that happens in the atmosphere will be slowed and dampened by the surrounding air. Enable the _Limit Velocity Over Lifetime_ module and set the _Speed_ to about 3.0 and the _Dampen_ fraction to about 0.4 and you should see the explosion lose a little strength as it progresses. -->

现在，爆炸正在形成，但是它看起来好像发生在太空中。粒子从被抛出到消失，以恒定的速度传播。如果游戏发生在天空中，那么这确实可能是你想要的效果。但是，发生在大气中的爆炸将被周围的空气阻碍并衰减。开启 _随生命周期抑制速度 Limit Velocity Over Lifetime_，设置 _速度 Speed_ 为约 3.0，_抑制 Dampen_ 分数为约 0.4，你应该看到爆炸随着进度损失一些强度。

<!-- A final thing to note is that as the particles move away from the centre of the explosion, their individual shapes become more recognisable. In particular, seeing the particles all at the same size and with the same rotation makes it obvious that the same graphic is being reused for each particle. A simple way to avoid this is to add a bit of random variation to the size and rotation of the particles as they are generated. In the Particle System module at the top of the inspector, click the small arrow to the right of the _Start Size_ and _Start Rotation_ properties and set them both to Random Between Two Constants. For the rotation, set the two values to 0 and 360 (ie, completely random rotation). For the size, set the values to 0.5 and 1.5 to give some variation without the risk of having too many huge or tiny particles. You should now see that the repetition of particle graphics is now much less noticeable. -->

最后要注意的是，随着粒子远离爆炸中心，它们各自的形状变得更加可辨认。特别是，可以看到所有粒子具有相同的大小和相同的旋转，显而易见，同样的图形被重复用于每个粒子。避免这种情况的一个简单方法是，在生成粒子时，为粒子的大小和大小增加一点随机变化。在检视视图顶部的 粒子系统 模块中，点击 _初始大小 Start Size_ 和 _初始旋转 Start Rotation_ 右侧的小箭头，把它们都设置为 _在两个常量之间随机 Random Between Two Constants_。对于旋转，将两个值设置为 0 和 360（即完全随机地旋转）。对于大小，设置为 0.5 和 1.5，以提供一些变化，并且不用担心会有大多巨大或微小的粒子。现在，你应该看到粒子图形的重复不太明显了。

<!-- ## Usage -->
## 用法

<!-- During testing, it is useful to have the _Looping_ property switched on so you can see the explosion repeatedly but in the finished game, you should switch this off so the explosion happens only once. When the explosion is designed for an object that has the potential to explode (a fuel tank, say) you might want to add the Particle System component to the object with the _Play On Awake_ property disabled. You can then set off the explosion from a script as necessary. -->

在测试期间，打开 _Looping_ 属性是有用的，以便你可以反复看到爆炸，但是在完成的游戏中，你应该关闭它，以使爆炸只发生一次。当为一个可能爆炸的对象（例如燃油箱）设置爆炸效果时，你需要为它添加粒子系统组件，并禁用 _唤醒时播放 Play On Awake_ 属性。然后，你可以根据需要触发爆炸效果。

```cs
    void Explode() {
        var exp = GetComponent<ParticleSystem>();
        exp.Play();
        Destroy(gameObject, exp.duration);
    }
```

<!-- In other cases, explosions happen at points of impact. If the explosion originates from an object (eg, a grenade) then you could call the `Explode` function detailed above after a time delay or when it makes contact with the target. -->

在某些情况下，爆炸发生在撞击点。如果爆炸来自某个对象（例如手榴弹），那么你可以在延迟一段时间后或当它与目标接触时，调用上面编写的 `Explode` 函数。

```cs
    // Grenade explodes after a time delay.
    public float fuseTime;

    void Start() {
        Invoke("Explode", fuseTime);
    }

    // Grenade explodes on impact.
    void OnCollisionEnter(Collision coll) {
        Explode();
    }
```

> 译注：fuse time 引信时间。

<!-- Where the explosion comes from an object that is not actually represented in the game (eg, a projectile that travels too fast to be seen), you can just instantiate an explosion in the appropriate place. You might determine the contact point from a [raycast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html), for example. -->

当爆炸来自一个不可见的游戏对象时（例如，速度太快以至于无法看到的子弹），你可以诶在适当的位置实例化爆炸。例如，你可以用 [射线 raycast] 确定接触点。

[raycast]: http://docs.unity3d.com/ScriptReference/Physics.Raycast.html
[射线 raycast]: http://docs.unity3d.com/ScriptReference/Physics.Raycast.html


```cs
    // On the explosion object.
    void Start() {
        var exp = GetComponent<ParticleSystem>();
        exp.Play();
        Destroy(gameObject, exp.duration);
    }
    
    // Possible projectile script.
    public GameObject explosionPrefab;

    void Update() {
        RaycastHit hit;

        if (Physics.Raycast (Camera.main.ScreenPointToRay (Input.mousePosition), out hit)) {
            Instantiate (explosionPrefab, hit.point, Quaternion.identity);
        }
    }
```

<!-- ## Further Ideas -->
## 更进一步

<!-- The explosion developed here is very basic but you can modify various aspects of it to get the exact feel you are looking for in your game. -->

这里开发的爆炸非常基础，不过你可以修改它的各个模块，以获得想要的精确效果。

<!-- The particle graphic you use will have a big effect on how the player “reads” the explosion. Having lots of small, separately recognisable flames suggests burning pieces being thrown out. Larger particles that don’t move completely apart appear more like a fireball fed by a destroyed fuel tank. Typically, you will need to change several properties together to complete the effect. For example, the fireball will persist longer and expand less before it disappears while a sharp burst may scatter burning pieces quite some distance. -->

你使用的粒子图形将极大地影响玩家如何『理解』爆炸。许多微小的、单独可识别的火焰，暗示燃烧的碎片正在被抛出。更大的、完全不可移动的部分，看起来更像是由被破坏的燃料箱产生的火球。通常，你需要同时更改多个属性才能实现这种效果。例如，火球在消失前将持续更长的时间和较小的膨胀，而剧烈的爆炸可能在相当一段距离内散布燃烧的碎片。

<!-- A few properties are set with random values here but other many properties have a _Random Between Two Constants/Curves_ option and you can use these to add variation in all sorts of ways. Varying the size and rotation helps to avoid the most obvious effects of particle repetition but you might also consider adding some randomness to the _Start Delay_, _Start Lifetime_ and _Start Speed_ properties. A small amount of variation helps to reinforce the impression of the explosion being a “natural” and unpredictable effect rather than a controlled mechanical process. Larger variations suggest a “dirty” explosion. For example, varying the _Start Delay_ will produce an explosion that is no longer sharp but bursts more slowly, perhaps because fuel tanks in a vehicle are being separately ignited. -->

爆炸示例中的几个属性被设置为随机值，但是其他许多其他属性都有一个 _在两个常量/曲线之间随机 Random Between Two Constants/Curves_ 选项，你可以使用这些属性添加各种变化。改变大小和旋转可以避免最明显的粒子重复问题，你也可以考虑为 _初始延迟 Start Delay_、_初始生命周期 Start Lifetime_ 和 _初始速度 Start Speed_ 添加一些随机性。轻微的变化有助于增强爆炸效果的自然性和不可预测性，而不是受控的机械式过程。较大的变化暗示一场『放射性』爆炸。例如，改变 _初始延迟Start Delay_ 将产生不再突然、爆发更慢的爆炸，可能是因为车辆的燃油箱被单独点燃。
