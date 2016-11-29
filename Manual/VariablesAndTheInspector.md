<!-- > 原文：[Variables and the Inspector](http://docs.unity3d.com/Manual/VariablesAndTheInspector.html) -->

<!-- Unity Manual > Scripting > Scripting Overview > Creating and Using Scripts -->
<!-- Unity 手册 <i class="fa fa-angle-right"/> 脚本 <i class="fa fa-angle-right"/> 脚本概述 <i class="fa fa-angle-right"/> 变量和检视面板 -->

<!-- # Variables and the Inspector -->
# 变量和检视面板

When creating a script, you are essentially creating your own new type of component that can be attached to Game Objects just like any other component.

创建脚本时，你基本上是创建您自己的新类型，它可以连接到游戏对象，就像任何其他部件的组件。

Just like other Components often have properties that are editable in the inspector, you can allow values in your script to be edited from the Inspector too.

就像其他组件经常有，在检查是可编辑的属性，你可以让你的脚本值从Inspector进行编辑了。

```
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

This code creates an editable field in the Inspector labelled “My Name”.

此代码在检查标记为“我的名字”创建一个可编辑的字段。


![](http://docs.unity3d.com/540/Documentation/uploads/Main/EditingVarInspector.png)

Unity creates the Inspector label by introducing a space wherever a capital letter occurs in the variable name. However, this is purely for display purposes and you should always use the variable name within your code. If you edit the name and then press Play, you will see that the message includes the text you entered.

统一由地方大写字母的变量名发生引入空间创建督察标签。然而，这纯粹是为了显示目的，你应该总是你的代码中使用的变量名。如果编辑名称，然后按播放，你会看到，该信息包含您输入的文本。

![](http://docs.unity3d.com/540/Documentation/uploads/Main/DebugLogMessage.png)

In C#, you must declare a variable as public to see it in the Inspector. In UnityScript, variables are public by default unless you specify that they should be private:

在C＃中，您必须声明一个变量作为公众看到它的督察。在UnityScript，变量默认为公用，除非您指定它们应该是私有的：

```
#pragma strict

private var invisibleVar: int;

function Start () {

}
```

Unity will actually let you change the value of a script’s variables while the game is running. This is very useful for seeing the effects of changes directly without having to stop and restart. When gameplay ends, the values of the variables will be reset to whatever they were before you pressed Play. This ensures that you are free to tweak your object’s settings without fear of doing any permanent damage.

团结实际上将让游戏运行时更改了脚本变量的值。这是看到变化的影响直接而无需停止和重新启动非常有用的。当游戏结束时，变量的值将被重置为不管他们是你按下播放之前。这可确保您可以自由无惧做任何永久性损坏调整你的对象的设置。
