> 原文：[Networking Overview](http://docs.unity3d.com/Manual/UNetOverview.html)

<!-- Unity Manual > Multiplayer and Networking > Networking Overview -->
用户手册 > 多玩家和联机 > 联机简介

<!-- # Networking Overview -->
# 联机简介

<!-- Related tutorials: [Multiplayer Networking](https://unity3d.com/learn/tutorials/topics/multiplayer-networking) -->
相关教程：[Multiplayer Networking](https://unity3d.com/learn/tutorials/topics/multiplayer-networking)

<!-- There are two kinds of users for the Networking feature: -->
从联机的角度看，有两种类型的的用户：

<!-- 
* Users making a Multiplayer game with Unity. These users should start with the [NetworkManager](http://docs.unity3d.com/Manual/UNetManager.html) or the [High Level API](http://docs.unity3d.com/Manual/UNetUsingHLAPI.html).
* Users building network infrastructure or advanced multiplayer games. These users should start with the [NetworkTransport API](http://docs.unity3d.com/Manual/UNetUsingTransport.html).
 -->
* 使用 Unity 创建多玩家游戏的用户。这部分用户从[网络管理](http://docs.unity3d.com/Manual/UNetManager.html)或[高级 API](http://docs.unity3d.com/Manual/UNetUsingHLAPI.html) 开始学习。
* 创建网络基础设施活高级多玩家游戏的用户。这部分用户应该从[网络传输 API](http://docs.unity3d.com/Manual/UNetUsingTransport.html) 开始学习。

<!-- ## High level scripting API -->
## 脚本高级 API

<!-- Unity’s networking has a “high-level” scripting API (which we’ll refer to as the HLAPI). Using this means you get access to commands which cover most of the common requirements for multiuser games without needing to worry about the “lower level” implementation details. The HLAPI allows you to: -->
Unity 的联机功能提供了『高级』脚本 API（称为 HLAPI）。高级 API 涵盖了多人游戏所需的大部分常用命令，你不需要关系那些『低级』API 的实现细节。高级 API 允许你：

<!-- 
* Control the networked state of the game using a “Network Manager”.
* Operate “client hosted” games, where the host is also a player client.
* Serialize data using a general-purpose serializer.
* Send and receive network messages.
* Send networked commands from clients to servers.
* Make remote procedure calls (RPCs) from servers to clients.
* Send networked events from servers to clients.
 -->
* 使用『网络管理器』控制游戏的联机状态。
* 操作『客户端』游戏，主机也是一个玩家终端。
* 使用多功能序列化器序列化数据。
* 发送和接收网络信息。
* 从客户端向服务端发送网络命令。
* 从服务端向客户端执行远程过程调用（RPC）。
* 从服务端向客户端发送网络事件。

<!-- ## Engine and Editor integration -->
## 整合引擎和编辑器

Unity’s networking is integrated into the engine and the editor, allowing you to work with components and visual aids to build your multiplayer game. It provides:

A NetworkIdentity component for networked objects.
A NetworkBehaviour for networked scripts.
Configurable automatic synchronization of object transforms.
Automatic synchronization of script variables.
Support for placing networked objects in Unity scenes.
Network components
Internet Services

Unity offers Internet Services to support your game throughout production and release, which includes:

Matchmaking service
Create matches and advertise matches.
List available matches and join matches.
Relay server
Game-play over internet with no dedicated server.
Routing of messages for participants of matches.
NetworkTransport real-time transport layer

We include a Real-Time Transport Layer that offers:

Optimized UDP based protocol.
Multi-channel design to avoid head-of-line blocking issues
Support for a variety of levels of Quality of Service (QoS) per channel.
Flexible network topology that supports peer-to-peer or client-server architectures.
Sample Projects

You can also dig into our multiplayer sample projects to see how these features are used together. The following sample projects can be found within this Unity Forum post:

Multiplayer 2D Tanks example game
Multiplayer Invaders game with Matchmaking
Multiplayer 2D space shooter with Matchmaking
Minimal Multiplayer project