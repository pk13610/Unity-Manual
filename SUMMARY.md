# Summary

* [简介](README.md)
* [Unity 手册](Manual/UnityManual.md)
<!-- * [使用 Unity](Manual/UnityOverview.md) -->
    <!-- * [Basics](Manual/UnityBasics.md) -->
    <!-- * [Asset Workflow](Manual/AssetWorkflow.md) -->
        <!-- * [Primitive and Placeholder Objects](Manual/PrimitiveObjects.md) -->
        <!-- * [Importing Assets](Manual/ImportingAssets.md) -->
* [图形](Manual/Graphics.md)
    * [图形概述](Manual/GraphicsOverview.md)
        <!-- * [光照概述](Manual/LightingOverview.md) -->
            <!-- * [光照概述](Manual/Lighting.md) -->
            <!-- * [光源](Manual/LightSources.md) -->
                <!-- * [光源类型](Manual/Lighting.md) -->
                <!-- * [光源检视](Manual/class-Light.md) -->
                <!-- * [使用光源](Manual/UsingLights.md) -->
            <!-- * [光照投影](Manual/Cookies.md) -->
            <!-- * [阴影](Manual/ShadowOverview.md) -->
            <!-- * [平行光阴影](Manual/DirLightShadows.md) -->
            <!-- * [光照排查和性能优化](Manual/LightPerformance.md) -->
            <!-- * [全局光照](Manual/GIIntro.md) -->
            <!-- * [线性渲染](Manual/LinearLighting.md) -->
        <!-- * [摄像机](Manual/CamerasOverview.md) -->
        * [材质、着色器、纹理](Manual/Shaders.md)
            * [创建和使用材质](Manual/Materials.md)
            * [标准着色器](Manual/shader-StandardShader.md)
                * [内容和上下文](Manual/StandardShaderContextAndContent.md)
                * [工作流程：金属 vs 镜面](Manual/StandardShaderMetallicVsSpecular.md)
                * [材质参数](Manual/StandardShaderMaterialParameters.md)
                    * [渲染模式](Manual/StandardShaderMaterialParameterRenderingMode.md)
                    * [漫反射颜色和透明度](Manual/StandardShaderMaterialParameterAlbedoColor.md)
                    <!-- * [镜面模式：镜面参数](Manual/StandardShaderMaterialParameterSpecular.md) -->
                    * [金属模式：金属参数](Manual/StandardShaderMaterialParameterMetallic.md)
                    * [平滑度](Manual/StandardShaderMaterialParameterSmoothness.md)
                    * [法线贴图（凹凸贴图）](Manual/StandardShaderMaterialParameterNormalMap.md)
                    * [高度图](Manual/StandardShaderMaterialParameterHeightMap.md)
                    * [散射贴图](Manual/StandardShaderMaterialParameterOcclusionMap.md)
                    * [自发光](Manual/StandardShaderMaterialParameterEmission.md)
                    * [辅助贴图（细节贴图）和细节蒙板](Manual/StandardShaderMaterialParameterDetail.md)
                    <!-- * [菲涅耳效应](Manual/StandardShaderFresnel.md) -->
                <!-- * [材质图表](Manual/StandardShaderMaterialCharts.md) -->
                <!-- * [自定义着色器](Manual/StandardShaderMakeYourOwn.md) -->
            <!-- * [脚本访问和修改材质参数](Manual/MaterialsAccessingViaScript.md) -->
            <!-- * [编写着色器](Manual/ShadersOverview.md) -->
* [脚本](Manual/ScriptingSection.md)
    * [脚本概述](Manual/ScriptingConcepts.md)
        * [创建和使用脚本](Manual/CreatingAndUsingScripts.md)
        * [变量和检视面板](Manual/VariablesAndTheInspector.md)
        <!-- * [Controlling GameObjects Using Components](Manual/ControllingGameObjectsComponents.md) -->
        <!-- * [Event Functions](Manual/EventFunctions.md) -->
        <!-- * [Time and Framerate Management](Manual/TimeFrameManagement.md) -->
        * [创建和销毁游戏对象](Manual/CreateDestroyObjects.md)
        <!-- * [Coroutines](Manual/Coroutines.md) -->
        * [特殊文件夹和脚本的编译顺序](Manual/ScriptCompileOrderFolders.md)
        <!-- * [Namespaces](Manual/Namespaces.md) -->
        * [属性](Manual/Attributes.md)
        * [事件函数执行顺序](Manual/ExecutionOrder.md)
        * [理解自动内存管理](Manual/UnderstandingAutomaticMemoryManagement.md)
        <!-- * [Platform Dependent Compilation](Manual/PlatformDependentCompilation.md) -->
        * [泛型函​​数](Manual/GenericFunctions.md)
        <!-- * [Scripting Restrictions](Manual/ScriptingRestrictions.md) -->
        <!-- * [Script Serialization](Manual/script-Serialization.md) -->
        <!-- * [UnityEvents](Manual/UnityEvents.md) -->
        <!-- * [What is a Null Reference Exception](Manual/NullReferenceException.md) -->
        <!-- * [Important Classes](Manual/ScriptingImportantClasses.md) -->
        <!-- * [Vector Cookbook](Manual/VectorCookbook.md) -->
            <!-- * [Understanding Vector Arithmetic](Manual/UnderstandingVectorArithmetic.md) -->
            <!-- * [Direction and Distance from One Object to Another](Manual/DirectionDistanceFromOneObjectToAnother.md) -->
            <!-- * [Computing a Normal\/Perpendicular vector](Manual/ComputingNormalPerpendicularVector.md) -->
            <!-- * [The Amount of One Vector's Magnitude that Lies in Another Vector's Direction](Manual/AmountVectorMagnitudeInAnotherDirection.md) -->
<!-- * [Multiplayer and Networking](Manual/UNet.md) -->
    <!-- * [Networking Overview](Manual/UNetOverview.md) -->
        <!-- * [The High Level API](Manual/UNetUsingHLAPI.md) -->
        <!-- * [Using the Transport Layer API](Manual/UNetUsingTransport.md) -->
        <!-- * [Internet Services](Manual/UNetInternetServicesOverview.md) -->
        <!-- * [Networking Tips for Mobile devices.](Manual/MobileNetworking.md) -->
        <!-- * [UnityWebRequest](Manual/UnityWebRequest.md) -->
    <!-- * [Networking Reference](Manual/UNetReference.md) -->
* [动画](Manual/AnimationSection.md)
    * [动画系统概览](Manual/AnimationOverview.md)
    * [动画剪辑](Manual/AnimationClips.md)
        <!-- * [从外部资源导入动画](Manual/AnimationsImport.md) -->
        * [动画视图指南](Manual/AnimationEditorGuide.md)
            * [使用动画视图](Manual/animeditor-UsingAnimationEditor.md)
            * [使用动画曲线](Manual/animeditor-AnimationCurves.md)
            <!-- * [编辑动画曲线](Manual/EditingCurves.md) -->
            <!-- * [多个动画](Manual/animeditor-MultipleParts.md) -->
            <!-- * [使用动画事件](Manual/animeditor-AnimationEvents.md) -->
    <!-- * [动画控制器](Manual/AnimatorControllers.md) -->
        <!-- * [动画控制器资源](Manual/Animator.md) -->
        <!-- * [动画控制器视图](Manual/AnimatorWindow.md) -->
        <!-- * [动画状态机](Manual/AnimationStateMachines.md) -->
            <!-- * [状态机基础](Manual/StateMachineBasics.md) -->
            <!-- * [动画参数](Manual/AnimationParameters.md) -->
            <!-- * [状态机转换](Manual/StateMachineTransitions.md) -->
            <!-- * [状态机行为](Manual/StateMachineBehaviours.md) -->
            <!-- * [子状态机](Manual/NestedStateMachines.md) -->
            <!-- * [动画层](Manual/AnimationLayers.md) -->
            <!-- * [独奏和静音功能](Manual/AnimationSoloMute.md) -->
            <!-- * [目标匹配](Manual/TargetMatching.md) -->
            <!-- * [反向运动学](Manual/InverseKinematics.md) -->
            <!-- * [主体运动](Manual/RootMotion.md) -->
        <!-- * [动画混合树](Manual/class-BlendTree.md) -->
        <!-- * [动画混合着色器](Manual/BlendShapes.md) -->
        <!-- * [动画控制器覆盖](Manual/AnimatorOverrideController.md) -->
<!-- * [Virtual Reality](Manual/VirtualReality.md) -->
    <!-- * [VR overview](Manual/VROverview.md) -->
    <!-- * [VR reference](Manual/VRReference.md) -->
    <!-- * [VR devices](Manual/VRDevices.md) -->
        <!-- * [Oculus](Manual/VRDevices-Oculus.md) -->
        <!-- * [ OpenVR](Manual/VRDevices-OpenVR.md) -->
    <!-- * [VR Audio Spatializers](Manual/VRAudioSpatializer.md) -->

