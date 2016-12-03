<!-- Unity Manual > Animation > Animation Clips > Animation Window Guide > Creating a New Animation Clip -->

<!-- # Creating a New Animation Clip -->
# 创建动画剪辑

<!-- To animate Game Objects in Unity, the object or objects need an **Animator Component** attached. This Animator Component must reference an **Animator Controller**, which in turn contains references to one or more **Animation Clips**. -->
在 Unity 中，为了让游戏对象动起来，需要附加一个 **动画组件**。这个动画组件必须引用一个 **动画控制器**，动画控制器再引用一个或多个 **动画剪辑**。

<!-- When using the Animation View to begin animating a GameObject in Unity, all these items will be automatically created, attached and set-up for you. -->
在 Unity 中，当开始使用动画视图让游戏对象动起来时，这些元素将被自动创建和绑定。

<!-- To create a new **Animation Clip** for the selected GameObject, and make sure the **Animation Window** is visible. -->
在为选中的游戏对象创建一个新动画剪辑前，需要先确保 **动画视图** 是打开的。

<!-- If the GameObject does not yet have any Animation Clips assigned, you will see the “Create” button in the centre of the Animation Window timeline area. Click the Create button. You will then be prompted to save your new empty Animation Clip somewhere in your **Assets** folder. -->
如果游戏对象尚未绑定任何动画剪辑，那么可以在动画视图的时间轴区域中看到『Create』按钮。点击该按钮，将会提示你把新创建的空动画剪辑保存到 **Assets** 文件的某个位置。

![Create a new Animation Clip](https://docs.unity3d.com/uploads/Main/AnimationEditorNewClip.png)
<!-- > Create a new Animation Clip -->
> 创建一个新动画剪辑

<!-- Once you have saved this new empty Animation Clip, a number of things happen automatically: -->
一旦保存了新创建的空动画剪辑，那么将自动执行下面的操作：

<!-- 
* A new Animator Controller asset will be will be created
* The new clip being created will be added into the Animator Controller as the default state
* An Animator Component will be added to the GameObject being animated
* The Animator Component will have the new Animator Controller assigned to it
 -->
* 一个新的动画控制器资源文件将被创建
* 新创建的动画剪辑将作为默认状态，被添加到该动画控制器中
* 一个动画组件将被添加到该游戏对象
* 该动画组件将引用该动画控制器

<!-- The result of this automatic sequence is that all the required elements of the animation system are set up for you, and you can now begin animating the objects. -->
上述操作（自动化序列）完成后，动画系统所需的所有元素已经就绪，可以开始让游戏对象动起来了。

<!-- ## Adding another Animation Clip -->
## 再创建一个动画剪辑

<!-- If the Game Object already has one or more Animation Clips assigned, the “Create” button will not be visible. Instead, one of the clips will be visible in the animation window. You can switch between which Animation Clip is visible in the window by using the menu in the top-left of the Animation window, just under the playback controls. -->
如果这个游戏对象已经分配了一个或多个动画剪辑，则『Create』按钮将不可见。相反，其中一个剪辑将出现在动画视图中。 你可以使用动画视图左上角的下拉菜单，就在播放控件下面，切换视图中显示的动画剪辑。

<!-- If you want to create a new Animation Clip on an object that already has animations, you must select “Create New Clip” from this menu. Again, you will be prompted to save your new empty Animation Clip before being able to work with it. -->
如果想要在一个已经含有动画的游戏对象上创建一个新的动画剪辑，则必须在下拉菜单中选择『Create New Clip』。你将被再次提示保存新建的空动画剪辑，然后才能使用它。

![Adding an additional new Animation Clip to an object which already has some clips assigned](https://docs.unity3d.com/uploads/Main/AnimationEditorNewClipMenu.png)
<!-- > Adding an additional new Animation Clip to an object which already has some clips assigned -->
> 为已经含有动画剪辑的游戏对象添加一个新的动画剪辑。

<!-- ## How it fits together -->
## 如何整合在一起

<!-- While the above steps automatically set up the relevant components and references, it can useful to understand which pieces must be connected together. -->
虽然上述步骤自动设置相关的组建和引用，但是理解它们是如何整合在一起的也非常有用。

<!-- 
* A GameObject must have an **Animator** component
* The Animator component must have an **Animator Controller** asset assigned
* The Animator Controller asset must have one or more Animation Clips assigned
 -->
* 一个游戏对象必须有一个 **动画组件**
* 该游戏组件必须被分配一个 **动画控制器** 资源
* 该动画控制器资源必须被分配一个或多个动画剪辑

<!-- The diagram below shows how these pieces are assigned, starting from the new animation clip created in the Animation Window: -->
下图演示了，在动画视图中新建一个动画剪辑时，这些元素是如何分配的：

![A new clip is created, and saved as an asset. The clip is automatically added as the default state to a new Animator Controller which is also saved as an asset. The Animator Controller is assigned to an Animator Component which is added to the GameObject.](https://docs.unity3d.com/uploads/Main/AnimationNewClipAutoSetup.png)
<!-- > A new clip is created, and saved as an asset. The clip is automatically added as the default state to a new Animator Controller which is also saved as an asset. The Animator Controller is assigned to an Animator Component which is added to the GameObject. -->
> 新建一个动画剪辑，并保存为一个资源。该动画剪辑作为默认状体，被自动添加到一个新的动画控制器中，该动画控制器也被保存一个资源。该动画控制器被分配给游戏对象上的动画组建。

<!-- In the image below, you can see a GameObject selected (“Cube”) that is not yet animated. We have just a simple cube, with no Animator component. The Animation, Hierarchy, Project and Inspector windows are arranged side-by-side for clarity. -->
在下面的图中，你可以看到一个没有动画的游戏对象。它只是一个简单的立方体，没有附加动画组件。动画视图、检视视图、层级视图和项目视图挨个排列如下。

![Before: An un-animated gameobject (Cube) is selected. It does not yet have an Animator Component, and no Animator Controller exists.](https://docs.unity3d.com/uploads/Main/AnimationEditorNewAnimationBefore.png)
<!-- > Before: An un-animated gameobject (“Cube”) is selected. It does not yet have an Animator Component, and no Animator Controller exists. -->
> 之前：一个无动画的游戏对象（立方体）被选中。它没有动画组件，动画控制器也不存在。

<!-- By pressing the create button in the Animation view, a new animation clip is created. Unity will ask to pick the name & location to save this new Animation Clip. Unity also creates an Animator Controller asset with the same name as the selected GameObject, adds an Animator component to the GameObject, and connects the assets up appropriately. -->
通过按下动画视图中的创建按钮，就创建了一个新的动画剪辑。Unity 将会询问你该动画剪辑的名字和存储位置。Unity 还会创建一个与选中的游戏对象同名的动画控制器资源文件，并且添加一个动画组件到游戏对象上，并且恰当地连接这些资源。

![After: After creating a new clip, you can see the new assets created in the project window, and the Animator Component assigned in the Inspector window (far right). You can also see the new clip assigned as the default state in the Animator Window](https://docs.unity3d.com/uploads/Main/AnimationEditorNewAnimationAdded.png)
<!-- > After: After creating a new clip, you can see the new assets created in the project window, and the Animator Component assigned in the Inspector window (far right). You can also see the new clip assigned as the default state in the Animator Window -->
> 之后：创建一个新的动画剪辑后，你可以在项目视图中看到新的资源文件，在检视视图（右侧）中看到附加的动画组件。你还可以在动画控制器视图中看到该动画剪辑被当作了默认状态。

<!-- In the new view above, you can see: -->
在上面的视图中，你可以看到：

<!-- 
* The Animation Window (top left) now shows a timeline with a red playback head line, ready to record new keyframes. The clip’s name is visible in the clip menu, just below the playback controls.
* The Inspector (center) shows that the Cube GameObject now has an **Animator Component** added, and the “Controller” field of the component shows that an Animator Controller asset called “Cube” is assigned
* The Project Window (bottom right) shows that two new assets have been created - An Animator Controller asset called “Cube” and an Animation Clip asset called “Cube Animation Clip”
* The Animator Window (bottom left) shows the contents of the Animator Controller - you can see that the Cube Animation Clip has been added to the controller, and that it is the “default state” as indicated by the orange color. Subsequent clips added to the controller would have a grey color, indicating they are not the default state.
 -->
* 动画视图（左上）现在显示一条带有红色播放磁头的时间轴，准备开始记录新关键帧。该剪辑的名字出现在剪辑菜单中，就在播放空间下方
* 检视视图（中间）显示立方体游戏对象现在添加了一个 **动画组件**，并且该组件的『Controller』域被分配了一个名为『Cube』的动画控制器资源。
* 项目视图（右下）现实两个新资源已经被创建——一个名为『Cube』的动画控制器资源和一个名称『Cube Animation Clip』的动画剪辑资源。
* 动画控制器视图（左下）显示了动画控制器的内容——你可以看到立方体动画剪辑已经被添加到了控制器中，并且是『默认状态』，用橙色颜色标出。后续添加到该控制器中的剪辑将是灰色，表示它们不是默认状态。
