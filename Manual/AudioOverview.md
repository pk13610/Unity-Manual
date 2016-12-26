<!-- # Audio Overview -->
# 音频概述

<!-- A game would be incomplete without some kind of audio, be it background music or sound effects. Unity’s audio system is flexible and powerful. It can import most standard audio file formats and has sophisticated features for playing sounds in 3D space, optionally with effects like echo and filtering applied. Unity can also record audio from any available microphone on a user’s machine for use during gameplay or for storage and transmission. -->

没有音频的游戏是不完整的，例如背景音乐或音响效果。Unity 的音频系统灵活而强大。它可以导入大多数标准音频文件格式，并且为播放 3D 空间中的声音提供了复杂的功能，以及可选的音响效果，例如回音和过滤。Unity 还可以记录来自用户机器上任意可用麦克风的音频，以便在游戏过程中使用，或者用于存储和传输。

<!-- ## Basic Theory -->
## 基础理论

<!-- In real life, sounds are emitted by objects and heard by listeners. The way a sound is perceived depends on a number of factors. A listener can tell roughly which direction a sound is coming from and may also get some sense of its distance from its loudness and quality. A fast-moving sound source (like a falling bomb or a passing police car) will change in pitch as it moves as a result of the Doppler Effect. Also, the surroundings will affect the way sound is reflected, so a voice inside a cave will have an echo but the same voice in the open air will not. -->

在现实生活中，声音由对象发出，并被听众听到。声音被感知的方式取决于许多因素。听众可以大致地判断声音来自的方向，并且可以通过音量和音质判断声音的距离。因为多普勒效应，快速移动的音源（例如下落的炸弹或路过的警车）将随着移动改变音高。此外，周围环境将影响声音反射的方式，所以，同样的声音，在洞穴内会有回音，在露天中则没有回音。

![Audio Sources and Listener](https://docs.unity3d.com/uploads/Main/AudioSourceListDiagram.png)
> Audio Sources and Listener
> 音频源和侦听器

<!-- To simulate the effects of position, Unity requires sounds to originate from **Audio Sources** attached to objects. The sounds emitted are then picked up by an **Audio Listener** attached to another object, most often the main camera. Unity can then simulate the effects of a source’s distance and position from the listener object and play them to the user accordingly. The relative speed of the source and listener objects can also be used to simulate the Doppler Effect for added realism. -->

为了模拟位置效果，Unity 要求为对象附加 **音频源 Audio Source** 组件，并指定声音文件；并为另一个对象附加 **音频侦听器 Audio Listener** 组件，通常是主摄像机。这样，音频源发出的声音被音频侦听器检测到。然后，Unity 可以模拟侦听器到音源的距离和位置效果，并相应地向用户播放声音。也可以用音频源和侦听器的相对速度来更加逼真地模拟多普勒效应。

<!-- Unity can’t calculate echoes purely from scene geometry but you can simulate them by adding **Audio Filters** to objects. For example, you could apply the Echo filter to a sound that is supposed to be coming from inside a cave. In situations where objects can move in and out of a place with a strong echo, you can add a **Reverb Zone** to the scene. For example, your game might involve cars driving through a tunnel. If you place a reverb zone inside the tunnel then the cars’ engine sounds will start to echo as they enter and the echo will die down as they emerge from the other side. -->

Unity 不支持纯粹地通过场景几何计算回音，但是可以通过添加 **音频过滤器 Audio Filters** 来模拟它们。例如，你可以为来自洞穴内部的声音应用回音过滤器 Echo。对于对象可以移入和移出的强回音场景，可以添加 **混响区域 Reverb Zone**。例如，游戏可能会汽车穿过隧道。如果在隧道内放置一个混响区域，当汽车进入隧道时，引擎声音将开始产生回音，当汽车从隧道另一边出现时，回音将消失。

<!-- The Unity **Audio Mixer** allows you to mix various audio sources, apply effects to them, and perform mastering. -->

Unity 的 **音频混音器 Audio Mixer** 支持混合各种音频源、添加效果和执行母带处理。

<!-- The manual pages for [Audio Source], [Audio Listener], [Audio Mixer], the [audio effects] and [Reverb Zones] give more information about the many options and parameters available for getting effects just right. -->

有关音响效果的选项和参数的更多信息，请参阅 [音频源]、[音频侦听器]，[音频混音器]，[音频效果] 和 [混响区域] 的手册页。

[Audio Source]: https://docs.unity3d.com/Manual/class-AudioSource.html
[Audio Listener]: https://docs.unity3d.com/Manual/class-AudioListener.html
[Audio Mixer]: https://docs.unity3d.com/Manual/class-AudioMixer.html
[audio effects]: https://docs.unity3d.com/Manual/class-AudioEffect.html
[Reverb Zones]: https://docs.unity3d.com/Manual/class-AudioReverbZone.html

[音频源]: https://docs.unity3d.com/Manual/class-AudioSource.html
[音频侦听器]: https://docs.unity3d.com/Manual/class-AudioListener.html
[音频混音器]: https://docs.unity3d.com/Manual/class-AudioMixer.html
[音频效果]: https://docs.unity3d.com/Manual/class-AudioEffect.html
[混响区域]: https://docs.unity3d.com/Manual/class-AudioReverbZone.html

<!-- ## Working with Audio Assets -->
## 使用音频资源

<!-- Unity can import audio files in **AIFF**, **WAV**, **MP3** and **Ogg** formats in the same way as other assets, simply by dragging the files into the Project panel. Importing an audio file creates an Audio Clip which can then be dragged to an Audio Source or used from a script. The Audio Clip reference page has more details about the import options available for audio files. -->

Unity 可以导入 **AIFF**、**WAV**、**MP3** 和 **Ogg** 格式的音频文件，导入方式与其他资源一样，只需简单地将文件拖入项目面板。导入一个音频文件会创建一个音频剪辑 Audio Clip，可以将其拖动到一个音频源 Audio Source 组件，或是从脚本中使用它。音频剪辑的参考页提供了导入音频文件时可用选项的更多详细信息。

<!-- For music, Unity also supports tracker modules, which use short audio samples as “instruments” that are then arranged to play tunes. Tracker modules can be imported from **.xm**, **.mod**, **.it**, and **.s3m** files but are otherwise used in much the same way as ordinary audio clips. -->

对于音乐，Unity 还支持音轨模块，它采用短音频样本作为乐器，然后排列乐器播放音乐。音轨模块可以从 **.xm**、**.mod**、**.it** 和 **.s3m** 文件导入，使用方式与普通的音频剪辑大致相同。

<!-- ## Audio Recording -->
## 音频录制

<!-- Unity can access the computer’s microphones from a script and create Audio Clips by direct recording. The **Microphone** class provides a straightforward API to find available microphones, query their capabilities and start and end a recording session. The script reference page for [Microphone] has further information and code samples for audio recording. -->

Unity 可以通过脚本访问计算机的麦克风，通过直接录制创建音频剪辑。**麦克风 Microphone** 类提供了直观的 API 来查找可用的麦克风，包括查询性能、开始和结束录制会话。[麦克风 Microphone] 的脚本引用页提供了音频录制的更多信息和代码示例。

[Microphone]: https://docs.unity3d.com/ScriptReference/Microphone.html
[麦克风 Microphone]: https://docs.unity3d.com/ScriptReference/Microphone.html
