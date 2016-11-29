<!-- # Special Folders and Script Compilation Order -->
# 特殊文件夹和脚本的编译顺序

<!-- For the most part, you can choose any names you like for the folders in your project but Unity reserves some names to indicate that the contents have a special purpose. Some of these folders have an effect on the order of script compilation. Essentially, there are four separate phases of script compilation and the phase where a script will be compiled is determined by its parent folder. -->
大多数情况下，你可以为项目中的文件夹选择任意你喜欢的名称，但是 Unity 因为一些特殊原因而保留了一些名称。其中，有部分命名会影响到脚本的编译顺序。从本质上看，脚本编辑过程分为 4 个独立的阶段，而一个脚本何时被变异，则取决于它所在的父文件夹。

<!-- This is significant in cases where a script must refer to classes defined in other scripts. The basic rule is that anything that will be compiled in a phase after the current one cannot be referenced. Anything that is compiled in the current phase or an earlier phase is fully available. -->
当一个脚本必须引用其他脚本中的类时，这个问题变得尤为明显。基本规则是，先编译的脚本不能引用后编译的脚本。也就是说，处于同一编译阶段的所有脚本都是可引用的，所有更早编译的脚本也是可引用的。

<!-- Another situation occurs when a script written in one language must refer to a class defined in another language (say, a UnityScript file that declares variables of a class defined in a C# script). The rule here is that the class being referenced must have been compiled in a earlier phase. -->
还有一种特殊情况，一个脚本是用某种语言编写的，它必须引用另外一个脚本，而第二个脚本是用别的语言编写的（例如，一个 UnityScript 文件声明了定义在 C# 文件中的类的变量）。这种情况的规则是，被引用的类必须在早期阶段被编译。

<!-- The phases of compilation are as follows: -->
4 个编译阶段如下：

<!-- **Phase 1:** Runtime scripts in folders called **Standard Assets**, **Pro Standard Assets** and **Plugins**. -->
**第 1 阶段：**文件夹 **Standard Assets**、**Pro Standard Assets** 和 **Plugins** 中的运行时脚本。

<!-- **Phase 2:** Editor scripts in folders called **Editor** that are anywhere inside top-level folders called **Standard Assets**, **Pro Standard Assets** and **Plugins**. -->
**第 2 阶段：**文件夹 **Standard Assets**、**Pro Standard Assets** 和 **Plugins** 下 **Editor** 中的编辑器扩展脚本。

<!-- **Phase 3:** All other scripts that are not inside a folder called **Editor**. -->
**第 3 阶段：**不在文件夹 **Editor** 中的所有脚本文件。

<!-- **Phase 4:** All remaining scripts (ie, the ones that are inside a folder called **Editor**). -->
**第 4 阶段：**所有剩余的文件（例如，文件 Editor 中的脚本文件。

<!-- A common example is where a UnityScript file needs to reference a class defined in a C# file. You can achieve this by placing the C# file inside a Plugins folder and the UnityScript file in a non-special folder. If you don’t do this, you will get an error saying the C# class cannot be found. -->
一个常见的例子是，一个 UnityScript 文件需要引用 C# 文件中的类。你可以把 C# 文件放入 Plugins 文件夹，把 UnityScript 放入普通文件夹。如果不这么处理，就会报错，提示找不到 C# 类。

<!-- **Note.** Standard Assets work only in the Assets root folder. -->
**注意：**文件夹  Standard Assets 只在根目录 Assets 下起作用。
