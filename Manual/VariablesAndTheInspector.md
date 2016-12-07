<!-- > 原文：[Variables and the Inspector](http://docs.unity3d.com/Manual/VariablesAndTheInspector.html) -->

<!-- Unity Manual > Scripting > Scripting Overview > Creating and Using Scripts -->
<!-- Unity 手册 <i class="fa fa-angle-right"/> 脚本 <i class="fa fa-angle-right"/> 脚本概述 <i class="fa fa-angle-right"/> 变量和检视面板 -->

<!-- # Variables and the Inspector -->
# 变量和检视视图

<!-- When creating a script, you are essentially creating your own new type of component that can be attached to Game Objects just like any other component. -->

创建脚本的本质是创建新的组件类型，它可以像其他组件一样附加到游戏对象。

<!-- Just like other Components often have properties that are editable in the inspector, you can allow values in your script to be edited from the Inspector too. -->

就像其他组件在检视视图中具有可编辑的属性一样，你也可以在检视视图中编辑脚本的属性值。

```c#
using UnityEngine;
using System.Collections;

public class MainPlayer : MonoBehaviour {
    public string myName;
    
    // Use this for initialization
    void Start () {
        Debug.Log("I am alive and my name is " + myName);
    }
    
    // Update is called once per frame
    void Update () {
    
    }
}
```

<!-- This code creates an editable field in the Inspector labelled “My Name”. -->

这段代码在检视视图中创建了一个标签为『My Name』的可编辑字段，。

![](http://docs.unity3d.com/540/Documentation/uploads/Main/EditingVarInspector.png)

<!-- Unity creates the Inspector label by introducing a space wherever a capital letter occurs in the variable name. However, this is purely for display purposes and you should always use the variable name within your code. If you edit the name and then press Play, you will see that the message includes the text you entered. -->

Unity 在检视视图中创建标签时，发现变量名中包含了一个大写字母，然后会在大写字母的位置插入一个空格。不过这纯粹是为了显示，你应该一直使用代码中的变量名。如果编辑这个名称，然后按下播放按钮，你看到日志信息中包含了你输入的文本。

![](http://docs.unity3d.com/540/Documentation/uploads/Main/DebugLogMessage.png)

<!-- In C#, you must declare a variable as public to see it in the Inspector. In UnityScript, variables are public by default unless you specify that they should be private: -->

在 C# 中，你必须把一个变量声明为公共变量，才能在检视视图中看到它。在 UnityScript 中，变量默认是公共的，除非被指定为私有变量。

```js
#pragma strict

private var invisibleVar: int;

function Start () {

}
```

<!-- Unity will actually let you change the value of a script’s variables while the game is running. This is very useful for seeing the effects of changes directly without having to stop and restart. When gameplay ends, the values of the variables will be reset to whatever they were before you pressed Play. This ensures that you are free to tweak your object’s settings without fear of doing any permanent damage. -->

实际上，你可以在游戏运行时改变脚本变量的值。这点非常有用，无需停止和重新启动，就可以直接看到改变后的效果。当游戏结束时，变量的值将被重置会按下播放按钮之前的状态。你可以自由调整对象的设置，而无需担心造成任何永久性破坏。
