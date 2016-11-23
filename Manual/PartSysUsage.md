> [Using Particle Systems in Unity](http://docs.unity3d.com/Manual/PartSysUsage.html)

Unity Manual > Graphics > Graphics Overview > Particle Systems > Using Particle Systems in Unity

## Using Particle Systems in Unity

Unity implements particle systems with a Component, so placing a system in a scene is a simple matter of adding a pre-made object (menu: **GameObject > Create General > Particle System**) or adding the component to an existing object (menu: **Component > Effects > Particle System**). Since the component is quite complicated, the inspector is divided into a number of collapsible sub-sections or _modules_ that each contain a group of related properties. Additionally, you can edit one or more systems at the same time using a separate editor window accessed via the Open Window button on the inspector. The many options available for the Particle System component are described in detail on its [component reference](http://docs.unity3d.com/Manual/class-ParticleSystem.html) page and the pages for the individual [modules](http://docs.unity3d.com/Manual/ParticleSystemModules.html).

When an object with a particle system is selected, the scene view will contain a small _Particle Effect_ panel with some simple controls that are useful for visualising changes you make to the system’s settings.

![](http://docs.unity3d.com/uploads/Main/PartSysEffectPanel.png)

The _Playback Speed_ allows you to speed up or slow down the particle simulation so you can quickly see how it will look at an advanced state. The _Playback Time_ indicates the time elapsed since the system was started; this may be faster or slower than real time depending on the playback speed. The _Particle Count_ indicates how many particles are currently in the system. The playback time can be “scrubbed” backwards and forwards by clicking on the _Playback Time_ label and dragging the mouse left and right. The buttons at the top of the panel can be used to pause and resume the simulation or to stop it and reset to the initial state.

## Varying Properties Over Time

Many of the numeric properties of particles or even the whole system can be varied over time. Unity provides several different methods of specifying how the variation will happen:-

* _Constant_: The property’s value is fixed throughout its lifetime.
* _Curve_: The value is specified by a curve/graph.
* _Random between two constants_: Two constant values define the upper and lower bounds for the value; the actual value varies randomly over time between those bounds.
* _Random between two curves_: Two curves define the upper and lower bounds of the the value at a given point in its lifetime; the current value varies randomly between those bounds.

For color properties, such as _Color over lifetime_, there are two separate options:

* _Gradient:_ The color value is taken from a gradient.
* _Random between two gradients:_ Two gradients define upper and lower “bounds” on the color value at a given time; the value used is a randomly weighted average of the two bound colors.
What is a Particle System?
