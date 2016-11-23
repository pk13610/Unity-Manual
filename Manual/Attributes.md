> 原文：[Attributes](http://docs.unity3d.com/Manual/Attributes.html)

<!-- Unity Manual > Scripting > Scripting Overview > Attributes -->
Unity 手册 <i class="fa fa-angle-right"/> 脚本 <i class="fa fa-angle-right"/> 脚本概述 <i class="fa fa-angle-right"/> 属性

<!-- # Attributes -->
# 属性

<!-- **Attributes** are markers that can be placed above a class, property or function in a script to indicate special behaviour. For example, the **HideInInspector** attribute can be added above a property declaration to prevent the property being shown in the inspector, even if it is public. In JavaScript, an attribute name begins with an “@” sign, whilst in C#, it is contained within square brackets:- -->
**属性**是一些标记，可以附加到脚本中的类、属性或函数之前，用来指示特定的行为。例如，属性 **HideInInspector** 可以添加到一个属性声明之前，来阻止该属性出现在检视面板中，即使它是一个公共属性。在 JavaScript 中，属性名以 @ 符号开头，而在 C# 中，则包裹在方括号中：

```js
// JS

@HideInInspector
var strength: float;
```

```c#
// C#

[HideInInspector]
public float strength;
```

Unity provides a number of attributes which are listed in the script reference (select the Editor or Runtime Attributes section from popup menu in the sidebar). There are also attributes defined in the .NET libraries which may sometimes be useful in Unity code.

团结提供了许多这是在脚本引用列出的属性（选择编辑器或运行时属性从弹出菜单中部分中的边栏）。也有属性，其中有时是统一的代码很有用.NET库定义。



Note: the [ThreadStatic](http://msdn.microsoft.com/en-us/library/system.threadstaticattribute.aspx) attribute defined in the .NET library should not be used as it will cause a crash if added to a Unity script.

注意：在.NET库中定义的[ThreadStatic]（http://msdn.microsoft.com/en-us/library/system.threadstaticattribute.aspx）属性不应使用，因为它会导致崩溃如果加入到统一的脚本。
