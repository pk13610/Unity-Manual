> [Audio files](https://docs.unity3d.com/Manual/AudioFiles.html)

Unity Manual > Audio > Audio files

# Audio files

As with Meshes or Textures, the workflow for **Audio File** assets is designed to be smooth and trouble free. Unity can import almost every common file format but there are a few details that are useful to be aware of when working with Audio Files.

Since Unity 5.0 audio data is separated from the actual AudioClips. The AudioClips merely refer to the files containing the audio data and there are various combinations of options in the AudioClip importer that determine how the clips are loaded at runtime. This means that you have great flexibility for deciding which audio assets should be kept in memory at all times (because you may not be able to predict how often or how fast they will be playing, i.e. footsteps, weapons and impacts), while other assets may be loaded on demand or gradually as the player progresses through the level (speech, background music, ambience loops etc).

When audio is encoded in Unity the main options for how it is stored on disk is either PCM, ADPCM or Compressed. Additionally there are a few platform-specific formats, but they work in similar ways. Unity supports most common formats for importing audio (see the list below) and will import an audio file when it is added to the project. The default mode is Compressed, where the audio data is compressed with either Vorbis/MP3 for standalone and mobile platforms, or HEVAG/XMA for PS Vita and Xbox One.

See the [AudioClip](https://docs.unity3d.com/Manual/class-AudioClip.html) documentation for an extensive description of the compression formats and other options available for encoding audio data.

Any Audio File imported into Unity is available from scripts as an Audio Clip instance, which provides a way for the game runtime of the audio system to access the encoded audio data. The game may access meta-information about the audio data via the AudioClip even before the actual audio data has been loaded. This is possible because the import process has extracted various bits of information such as length, channel count and sample rate from the encoded audio data and stored it in the AudioClip. This can for instance be useful when creating automatic dialogue or music sequencing systems, because the music engine can use the information about the length to schedule music playback before actually loading the data. It also helps reducing memory usage by only keeping the audio clips in memory that are needed at a time.

## Supported formats

| Format                        | Extensions
| ----------------------------- | ----------
| MPEG layer 3                  | .mp3
| Ogg Vorbis                    | .ogg
| Microsoft Wave                | .wav
| Audio Interchange File Format | .aiff / .aif
| Ultimate Soundtracker module  | .mod
| Impulse Tracker module        | .it
| Scream Tracker module         | .s3m
| FastTracker 2 module          | .xm

See the [Audio Overview](https://docs.unity3d.com/Manual/AudioOverview.html) for more information on using sound in Unity.
