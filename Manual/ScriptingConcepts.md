<!-- Unity Manual > Scripting > Scripting Overview -->
Unity 手册 > 脚本 > 脚本概述

<!-- # Scripting Overview -->
# 脚本概述

<!-- Although Unity uses an implementation of the standard Mono runtime for scripting, it still has its own practices and techniques for accessing the engine from scripts. This section explains how objects created in the Unity editor are controlled from scripts, and details the relationship between Unity’s gameplay features and the Mono runtime. -->
Unity 采用了标准的 Mono 运行时来提供脚本功能，并扩展了自主的实践和技术，来支持脚本访问引擎。本节介绍如何通过脚本控制在 Unity 编辑器中创建的对象，并详细介绍 Unity 游戏功能和 Mono 运行时之间的关系。

> 译注：[Mono](http://www.mono-project.com/docs/advanced/runtime/) 是 [ECMA 通用语言基础架构（ECMA Common Language Infrastructure，CLI）](http://www.ecma-international.org/publications/standards/Ecma-335.htm) 的实现。关于 Mono 是如何提供脚本功能的，请参阅这篇[从游戏脚本语言说起，剖析 Mono 所搭建的脚本基础](https://segmentfault.com/a/1190000004071127)。