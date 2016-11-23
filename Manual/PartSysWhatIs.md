> [What is a Particle System?](http://docs.unity3d.com/Manual/PartSysWhatIs.html)

Unity ManualGraphicsGraphics OverviewParticle SystemsWhat is a Particle System?
Using Particle Systems in Unity

# What is a Particle System?

**Particles** are small, simple images or meshes that are displayed and moved in great numbers by a particle system. Each particle represents a small portion of a fluid or amorphous entity and the effect of all the particles together creates the impression of the complete entity. Using a smoke cloud as an example, each particle would have a small smoke texture resembling a tiny cloud in its own right. When many of these mini-clouds are arranged together in an area of the scene, the overall effect is of a larger, volume-filling cloud.

## Dynamics of the System

Each particle has a predetermined lifetime, typically of a few seconds, during which it can undergo various changes. It begins its life when it is generated or emitted by its particle system. The system emits particles at random positions within a region of space shaped like a sphere, hemisphere, cone, box or any arbitrary mesh. The particle is displayed until its time is up, at which point it is removed from the system. The system’s emission rate indicates roughly how many particles are emitted per second, although the exact times of emission are randomized slightly. The choice of emission rate and average particle lifetime determine the number of particles in the “stable” state (ie, where emission and particle death are happening at the same rate) and how long the system takes to reach that state.

## Dynamics of Particles

The emission and lifetime settings affect the overall behaviour of the system but the individual particles can also change over time. Each one has a **velocity** vector that determines the direction and distance the particle moves with each frame update. The velocity can be changed by **forces** and **gravity** applied by the system itself or when the particles are blown around by a **wind zone** on a Terrain. The color, size and rotation of each particle can also change over its lifetime or in proportion to its current speed of movement. The color includes an alpha (transparency) component, so a particle can be made to fade gradually in and out of existence rather than simply appearing and disappearing abruptly.

Used in combination, particle dynamics can be used to simulate many kinds of fluid effects quite convincingly. For example, a waterfall can be simulated by using a thin emission shape and letting the water particles simply fall under gravity, accelerating as they go. Smoke from a fire tends to rise, expand and eventually dissipate, so the system should use an upward force on the smoke particles and increase their size and transparency over their lifetimes.