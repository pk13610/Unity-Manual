> [Audio Overview](https://docs.unity3d.com/es/current/Manual/AudioOverview.html)

Unity Manual > Audio > Audio Overview

# Audio Overview

A game would be incomplete without some kind of audio, be it background music or sound effects. Unity’s audio system is flexible and powerful. It can import most standard audio file formats and has sophisticated features for playing sounds in 3D space, optionally with effects like echo and filtering applied. Unity can also record audio from any available microphone on a user’s machine for use during gameplay or for storage and transmission.

## Basic Theory

In real life, sounds are emitted by objects and heard by listeners. The way a sound is perceived depends on a number of factors. A listener can tell roughly which direction a sound is coming from and may also get some sense of its distance from its loudness and quality. A fast-moving sound source (like a falling bomb or a passing police car) will change in pitch as it moves as a result of the Doppler Effect. Also, the surroundings will affect the way sound is reflected, so a voice inside a cave will have an echo but the same voice in the open air will not.

![Audio Sources and Listener](https://docs.unity3d.com/uploads/Main/AudioSourceListDiagram.png)
> Audio Sources and Listener

To simulate the effects of position, Unity requires sounds to originate from **Audio Sources** attached to objects. The sounds emitted are then picked up by an **Audio Listener** attached to another object, most often the main camera. Unity can then simulate the effects of a source’s distance and position from the listener object and play them to the user accordingly. The relative speed of the source and listener objects can also be used to simulate the Doppler Effect for added realism.

Unity can’t calculate echoes purely from scene geometry but you can simulate them by adding **Audio Filters** to objects. For example, you could apply the Echo filter to a sound that is supposed to be coming from inside a cave. In situations where objects can move in and out of a place with a strong echo, you can add a **Reverb Zone** to the scene. For example, your game might involve cars driving through a tunnel. If you place a reverb zone inside the tunnel then the cars’ engine sounds will start to echo as they enter and the echo will die down as they emerge from the other side.

The Unity **Audio Mixer** allows you to mix various audio sources, apply effects to them, and perform mastering.

The manual pages for [Audio Source](https://docs.unity3d.com/Manual/class-AudioSource.html), [Audio Listener](https://docs.unity3d.com/Manual/class-AudioListener.html), [Audio Mixer](https://docs.unity3d.com/Manual/class-AudioMixer.html), the [audio effects](https://docs.unity3d.com/Manual/class-AudioEffect.html) and [Reverb Zones](https://docs.unity3d.com/Manual/class-AudioReverbZone.html) give more information about the many options and parameters available for getting effects just right.

## Working with Audio Assets

Unity can import audio files in **AIFF**, **WAV**, **MP3** and **Ogg** formats in the same way as other assets, simply by dragging the files into the Project panel. Importing an audio file creates an Audio Clip which can then be dragged to an Audio Source or used from a script. The Audio Clip reference page has more details about the import options available for audio files.

For music, Unity also supports tracker modules, which use short audio samples as “instruments” that are then arranged to play tunes. Tracker modules can be imported from **.xm**, **.mod**, **.it**, and **.s3m** files but are otherwise used in much the same way as ordinary audio clips.

## Audio Recording

Unity can access the computer’s microphones from a script and create Audio Clips by direct recording. The **Microphone** class provides a straightforward API to find available microphones, query their capabilities and start and end a recording session. The script reference page for [Microphone](https://docs.unity3d.com/ScriptReference/Microphone.html) has further information and code samples for audio recording.