> [A Simple Explosion](http://docs.unity3d.com/Manual/PartSysExplosion.html)

Unity Manual > Graphics > Graphics Overview > Particle Systems > Particle System > How-Tos > A Simple Explosion

# A Simple Explosion
You can use a particle system to create a convincing explosion but the dynamics are perhaps a little more complicated than they seem at first. At its core, an explosion is just an outward burst of particles but there are a few simple modifications you can apply to make it look much more realistic.

![A particle system explosion during development](http://docs.unity3d.com/uploads/Main/PartSysExpScreenshot.png)
> A particle system explosion during development

## Timeline of a Particle

A simple explosion produces a ball of flame that expands outward rapidly in all directions. The initial burst has a lot of energy and is therefore very hot (ie, bright) and moves very fast. This energy quickly dissipates which results in the expansion of flame slowing down and also cooling down (ie, getting less bright). Finally, as all the fuel is burned up, the flames will die away and soon disappear completely.

An explosion particle will typically have a short lifetime and you can vary several different properties over that lifetime to simulate the effect. The particle will start off moving very fast but then its speed should reduce greatly as it moves away from the centre of the explosion. Also, the color should start off bright but then darken and eventually fade to transparency. Finally, reducing the particle’s size over its lifetime will give the effect of the flames dispersing as the fuel is used up.

## Implementation

Starting with the default particle system object (menu: **GameObject > Create General > Particle System**), go to the _Shape_ module and set the emitter shape to a small _Sphere_, say about 0.5 units in radius. The particles in the standard assets include a material called _Fire Add_ which is very suitable for explosions (menu: **Assets > Import Package > Particles**). You can set this material for the system using the _Renderer_ module. With the _Renderer_ open, you should also disable _Cast Shadows_ and _Receive Shadows_ since the explosion flames are supposed to give out light rather than receive it.

At this stage, the system looks like lots of little fireballs being thrown out from a central point. The explosion should, of course, create a burst with lots of particles all at once. In the _Emission_ module, you can set the _Rate_ value to zero and add a single _Burst_ of particles at time zero. The number of particles in the burst will depend on the size and intensity you want your explosion to have but a good starting point is about fifty particles. With the burst set up, the system is now starting to look much more like and explosion but it is rather slow and the flames seem to hang around for a long time. In the Particle System module (which will have the same name as the GameObject, eg, “Explosion”), set both the _Duration_ of the system and the _Start Lifetime_ of the particles to two seconds.

You can also use the _Size Over Lifetime_ module to create the effect of the flames using up their fuel. Set the size curve using the “ramp down” preset (ie, the size starts off at 100% and reduces to zero. To make the flames darken and fade, enable the _Color Over Lifetime_ module and set the gradient to start with white at the left and finish with black at the right. Since the _Fire Add_ material uses and additive shader for rendering, the darkness of the color property also controls the transparency of the particle; the flame’s will become fully transparent as the color fades to black. Also, the additive material allows the brightness of particles to “add” together as they are drawn on top of each other. This helps to further enhance the impression of a bright flash at the start of the explosion when the particles are all close together.

As it stands, the explosion is taking shape but it looks as though it is happening out in space. The particles get thrown out and travel a long distance at constant speed before fading. If your game is set in space then this might be the exact effect you want. However, an explosion that happens in the atmosphere will be slowed and dampened by the surrounding air. Enable the _Limit Velocity Over Lifetime_ module and set the _Speed_ to about 3.0 and the _Dampen_ fraction to about 0.4 and you should see the explosion lose a little strength as it progresses.

A final thing to note is that as the particles move away from the centre of the explosion, their individual shapes become more recognisable. In particular, seeing the particles all at the same size and with the same rotation makes it obvious that the same graphic is being reused for each particle. A simple way to avoid this is to add a bit of random variation to the size and rotation of the particles as they are generated. In the Particle System module at the top of the inspector, click the small arrow to the right of the _Start Size_ and _Start Rotation_ properties and set them both to _Random Between Two Constants_. For the rotation, set the two values to 0 and 360 (ie, completely random rotation). For the size, set the values to 0.5 and 1.5 to give some variation without the risk of having too many huge or tiny particles. You should now see that the repetition of particle graphics is now much less noticeable.

## Usage

During testing, it is useful to have the _Looping_ property switched on so you can see the explosion repeatedly but in the finished game, you should switch this off so the explosion happens only once. When the explosion is designed for an object that has the potential to explode (a fuel tank, say) you might want to add the Particle System component to the object with the _Play On Awake_ property disabled. You can then set off the explosion from a script as necessary.

```c#
    void Explode() {
        var exp = GetComponent<ParticleSystem>();
        exp.Play();
        Destroy(gameObject, exp.duration);
    }
```

In other cases, explosions happen at points of impact. If the explosion originates from an object (eg, a grenade) then you could call the Explode function detailed above after a time delay or when it makes contact with the target.

```c#
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

Where the explosion comes from an object that is not actually represented in the game (eg, a projectile that travels too fast to be seen), you can just instantiate an explosion in the appropriate place. You might determine the contact point from a [raycast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html), for example.

```c#
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

## Further Ideas

The explosion developed here is very basic but you can modify various aspects of it to get the exact feel you are looking for in your game.

The particle graphic you use will have a big effect on how the player “reads” the explosion. Having lots of small, separately recognisable flames suggests burning pieces being thrown out. Larger particles that don’t move completely apart appear more like a fireball fed by a destroyed fuel tank. Typically, you will need to change several properties together to complete the effect. For example, the fireball will persist longer and expand less before it disappears while a sharp burst may scatter burning pieces quite some distance.

A few properties are set with random values here but other many properties have a _Random Between Two Constants/Curves_ option and you can use these to add variation in all sorts of ways. Varying the size and rotation helps to avoid the most obvious effects of particle repetition but you might also consider adding some randomness to the _Start Delay_, _Start Lifetime_ and _Start Speed_ properties. A small amount of variation helps to reinforce the impression of the explosion being a “natural” and unpredictable effect rather than a controlled mechanical process. Larger variations suggest a “dirty” explosion. For example, varying the _Start Delay_ will produce an explosion that is no longer sharp but bursts more slowly, perhaps because fuel tanks in a vehicle are being separately ignited.

Particle System How-Tos
