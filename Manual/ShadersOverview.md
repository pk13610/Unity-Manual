> [Writing Shaders](http://docs.unity3d.com/Manual/ShadersOverview.html)

Unity Manual > Graphics > Graphics Overview > Materials, Shaders & Textures > Writing Shaders

# Writing Shaders

Shaders in Unity can be written in one of three different ways:

### Surface Shaders

[Surface Shaders](http://docs.unity3d.com/Manual/SL-SurfaceShaders.html) are your best option if your Shader needs to be affected by lights and shadows. Surface Shaders make it easy to write complex Shaders in a compact way - it’s a higher level of abstraction for interaction with Unity’s lighting pipeline. Most Surface Shaders automatically support both forward and deferred lighting. You write Surface Shaders in a couple of lines of **Cg/HLSL**, and a lot more code gets auto-generated from that.

Do not use Surface Shaders if your Shader is not doing anything with lights. For [Image Effects](http://docs.unity3d.com/Manual/comp-ImageEffects.html) or many special-effect Shaders, Surface Shaders are a suboptimal option, since they do a bunch of lighting calculations for no good reason.

### Vertex and Fragment Shaders

[Vertex and Fragment Shaders](http://docs.unity3d.com/Manual/SL-ShaderPrograms.html) are required if your Shader doesn’t need to interact with lighting, or if you need some very exotic effects that the Surface Shaders can’t handle. Shader programs written this way are the most flexible way to create the effect you need (even Surface Shaders are automatically converted to a bunch of Vertex and Fragment Shaders), but that comes at a price: you have to write more code and it’s harder to make it interact with lighting. These Shaders are written in **Cg/HLSL** as well.

### Fixed Function Shaders

Fixed Function Shaders are legacy Shader syntax for very simple effects. It is advisable to write programmable Shaders, since that allows much more flexibility. Fixed function shaders are entirely written in a language called **ShaderLab**, which is similar to Microsoft’s .FX files or NVIDIA’s CgFX. Internally, all Fixed Function Shaders are converted into [Vertex and Fragment Shaders](http://docs.unity3d.com/Manual/SL-ShaderPrograms.html) at shader import time.

## ShaderLab

Regardless of which type you choose, the actual Shader code is always wrapped in ShaderLab, which is used to organize the Shader structure. It looks like this:

```shaderlab
Shader "MyShader" {
    Properties {
        _MyTexture ("My Texture", 2D) = "white" { }
        // Place other properties like colors or vectors here as well
    }
    SubShader {
        // here goes your
        // - Surface Shader or
        // - Vertex and Fragment Shader or
        // - Fixed Function Shader
    }
    SubShader {
        // Place a simpler "fallback" version of the SubShader above
        // that can run on older graphics cards here
    }
}
```

We recommend that you start by reading about some basic concepts of the ShaderLab syntax in the [ShaderLab reference](http://docs.unity3d.com/Manual/SL-Shader.html) and then move on to the tutorials listed below.

The tutorials include plenty of examples for the different types of Shaders. Unity’s [Image Effects](http://docs.unity3d.com/Manual/comp-ImageEffects.html) package contains a lot of interesting vertex and fragment Shaders.

Read on for an introduction to shaders, and check out the [Shader reference](http://docs.unity3d.com/Manual/SL-Reference.html)!

* [Tutorial: ShaderLab & Fixed Function Shaders](http://docs.unity3d.com/Manual/ShaderTut1.html)
* [Tutorial: Vertex and Fragment Shaders](http://docs.unity3d.com/Manual/ShaderTut2.html)
* [Surface Shaders](http://docs.unity3d.com/Manual/SL-SurfaceShaders.html)
* [Writing Vertex and Fragment Shaders](http://docs.unity3d.com/Manual/SL-ShaderPrograms.html)