Unity Manual > Animation > A Glossary of Animation and Mecanim terms

# A Glossary of Animation and Mecanim terms

## Animation Clip terms
## 动画片段术语


Term:   | Definition:
------- | -----------
Animation Clip | Animation data that can be used for animated characters or simple animations. It is a simple “unit” piece of motion, such as (one specific instance of) “Idle”, “Walk” or “Run”.
Animation Curves | Curves can be attached to animation clips and controlled by various parameters from the game.
Avatar | Mask A specification for which body parts to include or exclude for a skeleton. Used in Animation Layers and in the importer.

术语 | 定义
---- | ----
动画片段 | 动画数据，可以用于角色动画或简单动画。它是动作的最小单位，例如闲置、行走或奔跑。
动画曲线 | 附加到动画片段的曲线，可以在游戏中被各种参数控制。
阿凡达 | 骨骼蒙皮，规范身体哪些部位被包含（或不包含）。用于动画层和动画导入。

## Avatar terms
## 阿凡达术语

Term: | Definition:
----- | -----------
Avatar | An interface for retargeting one skeleton to another.
Retargeting |  Applying animations created for one model to another.
Rigging | The process of building a skeleton hierarchy of bone joints for your mesh. Performed with an external tool, such as Max or Maya.
Skinning | The process of binding bone joints to the character’s mesh or ‘skin’. Performed with an external tool, such as Max or Maya.
Muscle Definition | A Mecanim concept, which allows you to have a more intuitive control over the character’s skeleton. When an Avatar is in place, Mecanim works in muscle space, which is more intuitive than bone space.
T-pose | The pose in which the character has their arms straight out to the sides, forming a “T”. The required pose for the character to be in, in order to make an Avatar.
Bind-pose | The pose at which the character was modelled.
Human template | A pre-defined bone-mapping. Used for matching bones from FBX files to the Avatar.
Translate DoF | The three degrees-of-freedom associated with translation (movement in X,Y & Z) as opposed to rotation.

术语 | 定义
---- | ----
Avatar 阿凡达 | 重定向一副骨骼到另一幅的接口。
Retargeting 重定向 | 把为一个模型创建的动画应用到另一个。
Rigging 骨骼动画 | 为网格创建骨骼层级和连接的过程。使用外部工具制作，例如 Max 或 Maya。
Skinning 蒙皮 | 把骨骼连接到角色网格或皮肤的过程。使用外部工具制作，例如 Max 或 Maya。
Muscle Definition 肌肉定义 | 一个动画概念，允许你对角色骨骼进行更符合直觉的控制。当使用 Avatar 时，动画系统运行在肌肉模式洗，比骨骼模式更加直观。
T-pose 标准姿势 | 角色的手臂向向两边伸直成 T 字形。这个姿势是为了制作一个 Avatar。
Bind-pose 模型姿势 | 角色建模时的姿势。
Human template 人形模板 | 一副预定义的骨骼映射。用于把 FBX 文件的骨骼匹配到 Avatar。
Translate DoF 自由度转换 | 把表示位置的 3 自由度转换为旋转。

## Animator and Animator Controller terms
## 动画控制器术语

Term: | Definition:
----- | -----------
Animator Component | Component on a model that animates that model using the Mecanim animation system. The component has a reference to an Animator Controller asset that controls the animation.
Root Motion | Motion of character’s root, whether it’s controlled by the animation itself or externally.
Animator Controller | The Animator Controller controls animation through Animation Layers with Animation State Machines and Animation Blend Trees, controlled by Animation Parameters. The same Animator Controller can be referenced by multiple models with Animator components.
Animator Window | The window where the Animator Controller is visualized and edited.
Animation Layer | An Animation Layer contains an Animation State Machine that controls animations of a model or part of it. An example of this is if you have a full-body layer for walking or jumping and a higher layer for upper-body motions such as throwing an object or shooting. The higher layers take precedence for the body parts they control.
Animation State Machine | A graph controlling the interaction of Animation States. Each state references an Animation Blend Tree or a single Animation Clip.
Animation Blend Tree | Used for continuous blending between similar Animation Clips based on float Animation Parameters.
Animation Parameters | Used to communicate between scripting and the Animator Controller. Some parameters can be set in scripting and used by the controller, while other parameters are based on Custom Curves in Animation Clips and can be sampled using the scripting API.
Inverse Kinematics (IK) | The ability to control the character’s body parts based on various objects in the world.

术语 | 定义
---- | ----
Animator Component 动画组件 | 附加到模型上的组件，通过 Mecanim 动画系统使模型动起来。该组件引用了一个动画控制器资源，用于控制动画剪辑。
Root Motion 躯干动作 | 角色躯干的动作，无论是被动画系统控制还是外部工具。
Animator Controller 动画控制器| 动画控制通过动画状态机的动画层和动画混合树的动画参数控制动画。同一个动画控制器可以被多个附加了动画组件的模型引用。
Animator Window 动画视图 | 可视化和编辑动画控制器的视图。
Animation Layer 动画层 | 一个动画层包含一个动画状态机，用于控制一个模型的全部或部分动画。一个例子是，用一个全身层控制行走或跳跃，用一个更高的层控制上半身动作，例如抛掷物体或设计。这个更高的层的优先级高于全身层。
Animation State Machine 动画状态机 | 一副控制动画状态交互的图形。每个状态引用一个动画混合树或单个动画剪辑。
Animation Blend Tree 动画混合树 | 用于连续混合相似的动画剪辑，基于动画参数。
Animation Parameters 动画参数 | 用于脚本和动画控制器的通信。一些参数可以在脚本中设置，并应用到动画控制器，而另一些参数则基于动画剪辑的自定义曲线，并且可以在脚本中使用。
Inverse Kinematics (IK) 反向动力学 | 基于各种对象控制角色身体部位的能力。

> 译著：

> 反响动力学 http://baike.baidu.com/view/1600095.htm
> Inverse Kinematics，IK，一种通过先确定子骨骼的位置，然后反求推导出其所在骨骼链上 n 级父骨骼位置，从而确定整条骨骼链的方法。

> 前向动力学，正向动力学 http://baike.baidu.com/view/2255474.htm
> Forward Kinematics，FK，完全遵循父子关系的层级，由父层级带动子层级的运动。

> 在前向运动学中，每一个子关节的位置、方向，都是由父关节所支配的。在电脑动画软件的发展初期，关节动画都是正向链接系统，它的特点是软件开发容易，最致命的弱点便是工作效率太低。

> 与前向运动学正好相反，反向运动学是依据某些子关节的最终位置和角度，来反求出整个骨架的形态。它的特点是工作效率高，大大减少了需要手动控制的关节数目，缺点是求解方程组需要耗费较多的计算机资源，在关节数增多的时候尤其明显。
