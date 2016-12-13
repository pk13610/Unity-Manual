<!-- > 原文：[Generic Functions](http://docs.unity3d.com/Manual/GenericFunctions.html) -->

<!-- Unity Manual > Scripting > Scripting Overview > Generic Functions -->
<!-- Unity 手册 <i class="fa fa-angle-right"/> 脚本 <i class="fa fa-angle-right"/> 脚本概述 <i class="fa fa-angle-right"/> 泛型函数 -->

<!-- # Generic Functions -->
# 泛型函​​数

<!-- Some functions in the script reference (for example, the various GetComponent functions) are listed with a variant that has a letter T or a type name in angle brackets after the function name: -->
在脚本手册中，一些函数的名称后跟有一对尖括号，尖括号中是字符 T 或类型名称：

```cs
//C#
void FuncName<T>();
//JS
function FuncName.<T>(): T;
```

<!-- These are known as generic functions. The significance they have for scripting is that you get to specify the types of parameters and/or the return type when you call the function. In JavaScript, this can be used to get around the limitations of dynamic typing:- -->
这些被称为是泛型函数。他们的意义在于指定参数类型和（或）返回类型。在 JavaScript 中，泛型函数可以避开动态类型的局限性：

```js
// The type is correctly inferred since it is defined in the function call.
//In C#
var obj = GetComponent<Rigidbody>();
//In JS
var obj = GetComponent.<Rigidbody>();
```

<!-- In C#, it can save a lot of keystrokes and casts: -->
在 C# 中，泛型函数可以节省大量的按键：

```cs
Rigidbody rb = go.GetComponent<Rigidbody>();

// ...as compared with:

Rigidbody rb = (Rigidbody) go.GetComponent(typeof(Rigidbody));
```

<!-- Any function that has a generic variant listed on its script reference page will allow this special calling syntax. -->
如果在脚本参考页看到了带有泛型声明的函数，那么就可以使用这种特殊的调用语法。
