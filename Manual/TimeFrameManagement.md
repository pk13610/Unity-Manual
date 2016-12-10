<!-- # Time and Framerate Management -->
# 时间和帧率控制

<!-- The Update function allows you to monitor inputs and other events regularly from a script and take appropriate action. For example, you might move a character when the “forward” key is pressed. An important thing to remember when handling time-based actions like this is that the game’s framerate is not constant and neither is the length of time between Update function calls. -->

脚本中的 Update 函数允许你定期地监听输入和其他事件，并执行适当的响应。例如，当按下『向前』键时，你可以会移动一个角色。处理类似这样的基于时间的行为时，一件重要的事情是，游戏的帧率不是恒定的，两次 Update 函数调用之间的时间长度也不是恒定的。

<!-- As an example of this, consider the task of moving an object forward gradually, one frame at a time. It might seem at first that you could just shift the object by a fixed distance each frame: -->

举个例子，假设有一个逐渐向前移动对象的任务，每桢移动一次。开始时，你可能只是使对象每桢移动一个固定距离：

```c#
//C# script example
using UnityEngine;
using System.Collections;

public class ExampleScript : MonoBehaviour {
    public float distancePerFrame;
    
    void Update() {
        transform.Translate(0, 0, distancePerFrame);
    }
}
```

```js
//JS script example
var distancePerFrame: float;

function Update() {
    transform.Translate(0, 0, distancePerFrame);
}
```

<!-- However, given that the frame time is not constant, the object will appear to move at an irregular speed. If the frame time is 10 milliseconds then the object will step forward by distancePerFrame one hundred times per second. But if the frame time increases to 25 milliseconds (due to CPU load, say) then it will only step forward forty times a second and therefore cover less distance. The solution is to scale the size of the movement by the frame time which you can read from the Time.deltaTime property: -->

但是，因为桢时间不是恒定的，所以对象看起来将以不规则的速度移动。如果桢时间是 10 毫秒，那么该对象每秒向前移动 100 步 distancePerFrame。但是，如果桢时间增加到 25 毫秒（例如由于 CPU 负载），那么只会每秒向前移动 40 步，因此移动距离更短。解决方案是按照桢时间适配移动距离，可以从 Time.deltaTime 属性读取桢时间：


```c#
//C# script example
using UnityEngine;
using System.Collections;

public class ExampleScript : MonoBehaviour {
    public float distancePerSecond;
    
    void Update() {
        transform.Translate(0, 0, distancePerSecond * Time.deltaTime);
    }
}
```

```js
//JS script example
var distancePerSecond: float;

function Update() {
    transform.Translate(0, 0, distancePerSecond * Time.deltaTime);
}
```

<!-- Note that the movement is now given as distancePerSecond rather than distancePerFrame. As the framerate changes, the size of the movement step will change accordingly and so the object’s speed will be constant. -->

注意，现在用 distancePerSecond 表示移动距离而不是 distancePerFrame。当帧率改变时，移动步长将相应地改变，对象的速度将是恒定的。

<!-- ## Fixed Timestep -->
## 固定时间步长

<!-- Unlike the main frame update, Unity’s physics system does work to a fixed timestep, which is important for the accuracy and consistency of the simulation. At the start of the physics update, Unity sets an “alarm” by adding the fixed timestep value onto the time when the last physics update ended. The physics system will then perform calculations until the alarm goes off. -->

与主桢更新不同，Unity 的物理系统以固定的时间步长运行，这对模拟的精确性和一致性非常重要。当物理更新开始时，Unity 在时间轴上设置一个固定时间步长（后将消失）的『警告器』，用来表示物理更新的结束时间。然后，物理更新开始执行计算，直到『警告器』消失。

<!-- You can change the size of the fixed timestep from the Time Manager and you can read it from a script using the Time.fixedDeltaTime property. Note that a lower value for the timestep will result in more frequent physics updates and more precise simulation but at the cost of greater CPU load. You probably won’t need to change the default fixed timestep unless you are placing high demands on the physics engine. -->

通过时间管理器可以更改固定时间步长的大小，在脚本中，可以使用 Time.fixedDeltaTime 属性读取它的值。注意，较小的时间步长将导致更频繁的物理更新和更精确的模拟，代价是更大的 CPU 负载。除非对物理引擎有很高的要求，否则可能不需要更改默认的固定时间步长。

> 译注：时间管理器 Time Manager 的菜单位置 **Edit > Project Settings > Time**。

<!-- ## Maximum Allowed Timestep -->
## 最大时间步长

<!-- The fixed timestep keeps the physical simulation accurate in real time but it can cause problems in cases where the game makes heavy use of physics and the gameplay framerate has also become low (due to a large number of objects in play, say). The main frame update processing has to be “squeezed” in between the regular physics updates and if there is a lot of processing to do then several physics updates can take place during a single frame. Since the frame time, positions of objects and other properties are frozen at the start of the frame, the graphics can get out of sync with the more frequently updated physics. -->

固定时间步长保证了物理模拟的实时精确，但是，当游戏使用了大量物理模拟时，可能会导致游戏帧率降低（由于有大量对象在运行）。频繁的物理更新会『挤压』主桢更新的时间，并且，如果有大量处理需要执行，那么一帧时间内可能发生多次物理更新。这时，当桢更新开始时，对象的位置和其他属性被冻结，图像可能与频繁的物理更新不同步。

<!-- Naturally, there is only so much CPU power available but Unity has an option to let you effectively slow down physics time to let the frame processing catch up. The Maximum Allowed Timestep setting (in the Time Manager) puts a limit on the amount of time Unity will spend processing physics and FixedUpdate calls during a given frame update. If a frame update takes longer than Maximum Allowed Timestep to process, the physics engine will “stop time” and let the frame processing catch up. Once the frame update has finished, the physics will resume as though no time has passed since it was stopped. The result of this is that rigidbodies will not move perfectly in real time as they usually do but will be slowed slightly. However, the physics “clock” will still track them as though they were moving normally. The slowing of physics time is usually not noticeable and is an acceptable trade-off against gameplay performance. -->

尽管事实上只有有限的 CPU 功率可用，但是 Unity 提供了一个选项，可以让你有效地降低物理时间，从而让桢处理保持（恢复）同步。最大时间步长（在时间管理器中）限制了一帧中消耗在物理更新和 FixedUpdate 调用上的时间。如果桢更新消耗的时间超过了最大时间步长，物理引擎将暂停执行，从而让桢更新保持（赶上）同步。一旦桢更新完成，物理更新将恢复执行，就像自它停止后时间没有流逝一样。这样做的结果是，刚体将不会像通常那样完美地实时移动，而是稍微减慢。但是，物理时钟将会像正常移动一样跟踪它们。这种物理更新放慢通常不明显，是一种可接受的游戏性能平衡。

<!-- ## Time Scale -->
## 时间尺度

<!-- For special effects, such as “bullet-time”, it is sometimes useful to slow the passage of game time so that animations and script responses happen at a reduced rate. Furthermore, you may sometimes want to freeze game time completely, as when the game is paused. Unity has a Time Scale property that controls how fast game time proceeds relative to real time. If the scale is set to 1.0 then game time matches real time. A value of 2.0 makes time pass twice as quickly in Unity (ie, the action will be speeded-up) while a value of 0.5 will slow gameplay down to half speed. A value of zero will make time “stop” completely. Note that the time scale doesn’t actually slow execution but simply changes the time step reported to the Update and FixedUpdate functions via Time.deltaTime and Time.fixedDeltaTime. The Update function is likely to be called more often than usual when game time is slowed down but the deltaTime step reported each frame will simply be reduced. Other script functions are not affected by the time scale so you can, for example, display a GUI with normal interaction when the game is paused. -->

减慢游戏时间对于某些特效会很有用，例如『子弹时间』，可以使动画和脚本响应以降低后的速率运行。另外，有时可能想要完全冻结游戏时间，此时游戏被暂停。Unity 提供了一个时间尺寸 Time Scale 来控制游戏时间相对于真实时间的速度。如果时间尺寸设置为 1.0，那么游戏时间和真实时间一致。设置为 2.0，将使 Unity 中的游戏时间两倍于真实时间（例如，动作将加速）；而设置为 0.5，将使游戏速度降低一半。设置为 0 将使事件完全『停止』。注意，时间尺寸不会真正减慢执行过程，而是简单地改变了 Time.deltaTime 和 Time.fixedDeltaTIme 返回给 Update 和 FixedUpdate 函数的时间步长。当游戏时间降低时，Update 函数的调用比正常情况更频繁，只是每桢返回的 deltaTime 被简单地降低了。其他脚本函数不会受到时间尺度的影响，例如，在游戏暂停时，显示可正常交互的 GUI。

> 译注：子弹时间（Bullet time）是一种使用在电影、电视广告或电脑游戏中，用计算机辅助的摄影技术模拟变速特效，例如强化的慢镜头、时间静止等效果。“子弹时间”效果因在好莱坞华纳兄弟电影公司出品的电影《骇客帝国》中大量使用名声大噪。其中男主角 Neo 仰身躲子弹的慢动作镜头堪称经典，“子弹时间”也因此得名。—— [百度百科](http://baike.baidu.com/view/164264.htm)

<!-- The Time Manager has a property to let you set the time scale globally but it is generally more useful to set the value from a script using the Time.timeScale property: -->

时间管理器提供了一个可全局设置时间尺度的属性，不过，通常是在脚本中使用 Time.timeScale 属性设置时间尺度：

```c#
//C# script example
using UnityEngine;
using System.Collections;

public class ExampleScript : MonoBehaviour {
    void Pause() {
        Time.timeScale = 0;
    }
    
    void Resume() {
        Time.timeScale = 1;
    }
}
```

```js
//JS script example
function Pause() {
    Time.timeScale = 0;
}

function Resume() {
    Time.timeScale = 1;
}
```

<!-- ## Capture Framerate -->
## 捕获帧率

<!-- A very special case of time management is where you want to record gameplay as a video. Since the task of saving screen images takes considerable time, the usual framerate of the game will be drastically reduced if you attempt to do this during normal gameplay. This will result in a video that doesn’t reflect the true performance of the game. -->

时间管理的一个特例是把游戏记录为视频。如果你尝试在正常的游戏过程中录制视，因为保存屏幕图像需要相当长的时间，游戏帧率通常会大大降低。这将导致视频不能真实反应游戏的性能。

<!-- Fortunately, Unity provides a Capture Framerate property that lets you get around this problem. When the property’s value is set to anything other than zero, game time will be slowed and the frame updates will be issued at precise regular intervals. The interval between frames is equal to 1 / Time.captureFramerate, so if the value is set to 5.0 then updates occur every fifth of a second. With the demands on framerate effectively reduced, you have time in the Update function to save screenshots or take other actions: -->

幸运的是，Unity 提供了一个捕获帧率 Capture Framerate 属性来解决这个问题。当该属性的值被设置为非 0 时，游戏速度将降低，桢更新将以精确的时间间隔定期执行。两桢之间的间隔等于 `1 / Time.captureFramerate`，因此，如果该值被设置为 5.0，那么桢更新每 1/5 秒发生一次。随着帧率的有效降低，Update 函数有充足的时间来保存屏幕截图或执行其他行为。

```c#
//C# script example
using UnityEngine;
using System.Collections;

public class ExampleScript : MonoBehaviour {
    // Capture frames as a screenshot sequence. Images are
    // stored as PNG files in a folder - these can be combined into
    // a movie using image utility software (eg, QuickTime Pro).
    // The folder to contain our screenshots.
    // If the folder exists we will append numbers to create an empty folder.
    string folder = "ScreenshotFolder";
    int frameRate = 25;
        
    void Start () {
        // Set the playback framerate (real time will not relate to game time after this).
        Time.captureFramerate = frameRate;
        
        // Create the folder
        System.IO.Directory.CreateDirectory(folder);
    }
    
    void Update () {
        // Append filename to folder name (format is '0005 shot.png"')
        string name = string.Format("{0}/{1:D04} shot.png", folder, Time.frameCount );
        
        // Capture the screenshot to the specified file.
        Application.CaptureScreenshot(name);
    }
}
```

```js
//JS script example

// Capture frames as a screenshot sequence. Images are
// stored as PNG files in a folder - these can be combined into
// a movie using image utility software (eg, QuickTime Pro).
// The folder to contain our screenshots.
// If the folder exists we will append numbers to create an empty folder.
var folder = "ScreenshotFolder";
var frameRate = 25;


function Start () {
    // Set the playback framerate (real time will not relate to game time after this).
    Time.captureFramerate = frameRate;

    // Create the folder
    System.IO.Directory.CreateDirectory(folder);
}

function Update () {
    // Append filename to folder name (format is '0005 shot.png"')
    var name = String.Format("{0}/{1:D04} shot.png", folder, Time.frameCount );

    // Capture the screenshot to the specified file.
    Application.CaptureScreenshot(name);
}
```

<!-- Although the video recorded using this technique typically looks very good, the game can be hard to play when slowed-down drastically. You may need to experiment with the value of Time.captureFramerate to allow ample recording time without unduly complicating the task of the test player. -->

使用这种技术录制的视频虽然通常看起来很不错，但是当游戏速度大幅降低时，游戏可能没法完了。为了保证充足的记录时间，并避免使播放器任务过度复杂化，你可能需要反复实验 Time.captureFramerate 的值。
