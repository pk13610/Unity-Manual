<!-- > 原文：[Creating and Using Scripts](http://docs.unity3d.com/Manual/CreatingAndUsingScripts.html) -->

<!-- Unity Manual > Scripting > Scripting Overview > Creating and Using Scripts -->
<!-- Unity 手册 <i class="fa fa-angle-right"/> 脚本 <i class="fa fa-angle-right"/> 脚本概述 <i class="fa fa-angle-right"/> 创建和使用脚本 -->

<!-- # Creating and Using Scripts -->
# 创建和使用脚本

<!-- The behavior of GameObjects is controlled by the **Components** that are attached to them. Although Unity’s built-in Components can be very versatile, you will soon find you need to go beyond what they can provide to implement your own gameplay features. Unity allows you to create your own Components using **scripts**. These allow you to trigger game events, modify Component properties over time and respond to user input in any way you like. -->

游戏对象的行为由绑定的 **组件** 所控制。尽管 Unity 内置的组件非常灵活多样，但是你很快就会发现它们提供的功能远远不够，为了实现你所要的游戏功能，你需要超越它们才行。Unity 支持通过 **脚本** 创建属于你自己的组件。在组件中，随着时间的推移，你可以触发游戏事件、修改组件属性，还可以以任何你喜欢的方式来响应用户输入。

<!-- Unity supports two programming languages natively: -->
Unity 内置支持两种编程语言：

<!-- * **C#** (pronounced C-sharp), an industry-standard language similar to Java or C++;
** **UnityScript**, a language designed specifically for use with Unity and modelled after JavaScript; -->
* **C#** 一种工业标准语言，类似于 Java 或 C++；
* **UnityScript** 一种专为 Unity 设计的语言，模仿自 JavaScript；

<!-- In addition to these, many other .NET languages can be used with Unity if they can compile a compatible DLL - see [here](http://docs.unity3d.com/540/Documentation/Manual/UsingDLL.html) for further details. -->
除此之外，许多其他可以编译为兼容 DLL 的语言也可以用于 Unity —— 更多细节请查阅 [这里](http://docs.unity3d.com/540/Documentation/Manual/UsingDLL.html)。

<!-- Learning the art of programming and the use of these particular languages is beyond the scope of this introduction. However, there are many books, tutorials and other resources for learning how to program with Unity. See the [Learning section](http://unity3d.com/learn) of our website for further details. -->
学习编程艺术和使用这些特定语言超出了本文的范围。不过，有许多书籍、指南和其他资源可以让你学习如何在 Unity 中编程。请参阅我们网站的 [学习部分](http://unity3d.com/learn) 了解更多细节。

<!-- ## Creating Scripts -->
## 创建脚本

<!-- Unlike most other assets, scripts are usually created within Unity directly. You can create a new script from the Create menu at the top left of the Project panel or by selecting **Assets > Create > C# Script** (or JavaScript) from the main menu. -->

与其他大多数资源文件不同的是，脚本通常是直接在 Unity 中创建。你可以通过 Project 面板左上角的 Create 菜单创建一个新脚本，或者从主菜单选择 **Assets > Create > C# Script** (或 JavaScript) 。

<!-- The new script will be created in whichever folder you have selected in the Project panel. The new script file’s name will be selected, prompting you to enter a new name. -->

新脚本将被创建在 Project 面板中选中的文件夹下。新脚本的文件名将被选中，提示你输入一个新的名称。

![](http://docs.unity3d.com/540/Documentation/uploads/Main/NewScriptIcon.png)

<!-- It is a good idea to enter the name of the new script at this point rather than editing it later. The name that you enter will be used to create the initial text inside the file, as described below. -->
最好是在这个时候为新脚本输入名称，而不是在以后再修改。你输入的脚本名称将被用于初始化文件的内容，如下所述。

<!-- ## Anatomy of a Script file -->
## 脚本文件剖析

<!-- When you double-click a script asset in Unity, it will be opened in a text editor. By default, Unity will use MonoDevelop, but you can select any editor you like from the External Tools panel in Unity’s preferences. -->
当你在 Unity 中双击一个脚本文件时，它将被一个文件编辑器打开。默认情况下，Unity 会使用 MonoDevelop，你也可以在 Unity 偏好设置的 External Tools 面板中选择任何你喜欢的编辑器。

<!-- The initial contents of the file will look something like this: -->
脚本文件的初始内容会是这个样子：

```cs
using UnityEngine;
using System.Collections;

public class MainPlayer : MonoBehaviour {

    // Use this for initialization
    void Start () {
    
    }
    
    // Update is called once per frame
    void Update () {
    
    }
}
```

<!-- A script makes its connection with the internal workings of Unity by implementing a class which derives from the built-in class called **MonoBehaviour**. You can think of a class as a kind of blueprint for creating a new Component type that can be attached to GameObjects. Each time you attach a script component to a GameObject, it creates a new instance of the object defined by the blueprint. The name of the class is taken from the name you supplied when the file was created. The class name and file name must be the same to enable the script component to be attached to a GameObject. -->

脚本通过继承内置类 **MonoBehaviour** 与 Unity 相连接。你可以把类当作是一种设计图，它可以创建一个新的组件，并绑定到游戏对象上。每当你把脚本组件绑定到游戏对象上时，会创建一个由设计图定义的对象实例。类的名称来自于文件创建时你提供的文件名。类名和文件名必须一致，这个脚本组件才能被绑定到游戏对象。

<!-- The main things to note, however, are the two functions defined inside the class. The **Update** function is the place to put code that will handle the frame update for the GameObject. This might include movement, triggering actions and responding to user input, basically anything that needs to be handled over time during gameplay. To enable the Update function to do its work, it is often useful to be able to set up variables, read preferences and make connections with other GameObjects before any game action takes place. The **Start** function will be called by Unity before gameplay begins (ie, before the Update function is called for the first time) and is an ideal place to do any initialization. -->

特别需要注意在类中定义的两个函数。函数 **Update** 用于放置处理游戏对象桢更新的代码。可能包括移动、触发动作和响应用户输入等，基本上包含了任何游戏运行时随着时间推移需要处理的事情。为了让 Update 函数能够工作起来，通常需要在任何游戏行为发生前，设置变量、读取配置和连接其他游戏对象。函数 **Start** 在游戏开始前被 Unity 调用（例如，第一次调用 Update 函数之前），是执行初始化的理想场所。

<!-- Note to experienced programmers: you may be surprised that initialization of an object is not done using a constructor function. This is because the construction of objects is handled by the editor and does not take place at the start of gameplay as you might expect. If you attempt to define a constructor for a script component, it will interfere with the normal operation of Unity and can cause major problems with the project. -->
老司机请注意：你可能会惊讶于一个对象的初始化居然没有用到构造函数，这是因为，对象的构造过程是由编辑器处理的，而且不是发生在你所期望的游戏开始时。如果你试图为脚本组件定义一个构造函数，将妨碍 Unity 的正常运行，可能会引发严重问题。

<!-- A UnityScript script works a bit differently to C# script: -->
UnityScript 脚本与 C# 脚本稍有不同：

```
#pragma strict

function Start () {

}

function Update () {

}
```

<!-- Here, the Start and Update functions have the same meaning but the class is not explicitly declared. The script itself is assumed to define the class; it will implicitly derive from MonoBehaviour and take its name from the filename of the script asset. -->
在这里，Start 和 Update 函数具有相同的含义，但是没有显示地声明类。脚本本身就被认为是对类的定义；它将隐式地继承 MonoBehaviour，并且把脚本文件名作为类名。

<!-- ## Controlling a GameObject -->
## 控制游戏对象

<!-- As noted above, a script only defines a blueprint for a Component and so none of its code will be activated until an instance of the script is attached to a GameObject. You can attach a script by dragging the script asset to a GameObject in the hierarchy panel or to the inspector of the GameObject that is currently selected. There is also a Scripts submenu on the Component menu which will contain all the scripts available in the project, including those you have created yourself. The script instance looks much like any other Component in the Inspector: -->
如上所述，脚本只是组件的设计图，在脚本实例被附加到游戏对象之前，它的代码不会被激活。你可以拖动脚本文件到层级视图的某个游戏对象上，或者拖到到当前选中的游戏对象的检视视图中。在 Component 菜单下有一个 Scripts 子菜单，其中包含了当前项目中的所有有效脚步，包括你创建的脚本。脚本实例看起来就像检视视图中的其他组件一样。

![](http://docs.unity3d.com/540/Documentation/uploads/Main/ScriptInInspector.png)

<!-- Once attached, the script will start working when you press Play and run the game. You can check this by adding the following code in the Start function:- -->
绑定之后，当你按下 Play 按钮运行游戏时，脚本就开始工作。你可以在 Start 函数中添加下面的代码来验证这一点：

```
// Use this for initialization
void Start () {
    Debug.Log("I am alive!");
}
```

<!-- **Debug.Log** is a simple command that just prints a message to Unity’s console output. If you press Play now, you should see the message at the bottom of the main Unity editor window and in the Console window (menu: **Window > Console**). -->

**Debug.Log** 是一个简单的命令，只是向 Unity 的控制台输出打印一条消息。现在，如果你按下 Play 按钮，你会在 Unity 编辑器窗口底部和 Console 窗口（菜单：**Window > Console**）看到这条消息。
