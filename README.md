
## Team Name

| No.  | Nama Anggota       | NRP          |
|------|--------------------|--------------|
| 1    | Arkana Bilal Imani        | 5025211034  |
| 2    | Christian Kevin Emor      | 5025211153  |
| 3    | Katarina Inezita Prambudi | 5025211148 |


## Introduction to Lighting and Rendering
Lighting and rendering are crucial aspects of creating realistic and visually appealing 3D environments in Unity. They play a significant role in shaping the game or application looks and feels. Let's breakdown the concepts of lighting and rendering :

### Lighting
#### Light Sources
Lighting in Unity is driven by various light sources. These sources can be directional (ex: sunlight), point lights (ex: lightbulb), spotlights, or area lights. Each type of light source affects the scene differently

#### Light Properties
Light have properties such as color, intensity, range, and shadow settings. Adjusting these properties helps to achieve the desired visual atmosphere and mood in the scene

#### Shadows 
Proper shadow casting and receiving are essential for realism. Unity supports various shadow techniques, including shadow mapping and ray tracing

### Rendering
#### Rendering Pipeline
Unity uses a rendering pipeline to process and display 3D graphics. Unity offers several rendering pipelinse, including the Built-in Render Pipeline and the High Definition Render Pipeline

#### Materials and Shaders
Materials define how an object responds to light. Shaders are used to create complex materials by defining how the interact with light and shadows


## Choosing a Lighting Technique
### 1. Realtime Lighting 
Realtime lighting is a technique in which lighting is computed on the fly ad the game runs. This includes all light sources that interact in real-time with objects and characters in the game. It involves direct lighting, dynamic shadows, and lighting effects that change over time

Realtime lighting is well suited for games with a lot of changes in lighting, such as games with dynamic day night cycles or environment that change continuously. It is also suitable for VR or AR games that require real time interaction between lights and objects

### 2. Baked Global Illumination (GI) Lighting
Baked GI Lighting is a technique in which lighting is calculated before the game starts and stored in lightmaps. These lightmaps are used during gameplay and store information about how light interacts with objects in the environment

Baked GI Lighting is very useful for games with relatively static lighting or infrequent changes. It can help reduce the computation load during gameplay, thus improving game performance








## GI (Global Illumination) Cache
In Baked Global Illumination (GI) within Unity, data related to your Scene's lighting is stored in the GI cache. Unity attempts to utilize this stored data whenever possible to save time during the precomputing process. The extent and type of modifications you've made to your Scene will determine how much of this data can be reused, if at all. The GI cache is stored separately from your Unity project and can be cleared by accessing **Edit > Preferences > GI Cache > Clean Cache**. Clearing the cache will necessitate recalculating all precompute stages from the beginning, which can be time-consuming. However, in certain situations where disk space reduction is necessary, this can be a useful option.

![image](https://github.com/cg20231c/unity-graphics-bangan/assets/97864068/fc413e9e-8a7e-4299-b1ce-278ab7b67955)

## Rendering Path
Unity offers various rendering techniques or paths, and deciding which path to utilize is a crucial early choice when commencing a project.
- **Forward Rendering**

  It involves rendering each object in the scene individually during a single pass, making it suitable for scenarios with a relatively small number of objects and lights. The primary advantage of forward rendering is its simplicity and efficiency on older hardware or mobile devices. It's best employed in projects where the scene's complexity is limited, and there are only a few lights and post-processing effects, making it a good choice for simpler scenes and mobile games. However, in more graphically complex and demanding environments with numerous lights, materials, and advanced visual effects, deferred rendering or other modern techniques may be preferred to achieve better performance and visual fidelity.

  ![image](https://github.com/cg20231c/unity-graphics-bangan/assets/97864068/d9a8142f-a202-41ea-ab61-f9a7c036112f)

- **Deferred Rendering**

  Deferred rendering is a sophisticated rendering technique employed in computer graphics and game development. It diverges from forward rendering by first collecting and storing various pieces of information (like object properties, positions, normals, and materials) in multiple buffers during an initial pass, and then using this stored information to calculate lighting and shading in subsequent passes. This approach is particularly advantageous when dealing with complex scenes containing numerous lights and materials, as it reduces the processing load per pass, resulting in improved performance. Deferred rendering allows for the implementation of advanced lighting and post-processing effects, making it a preferred choice for high-end PC and console games seeking to achieve superior graphics quality and realism in visually intricate environments.

  ![image](https://github.com/cg20231c/unity-graphics-bangan/assets/97864068/c6bafd46-7d1c-497a-95e0-87fd1aafbc62)


It is recommended to use forward rendering when:
- Speed is a priority and real-time rendering is needed
- The scene has a small number of non-overlapping opaque objects
- The lighting model is simple with fewer lights

It is recommended to use deferred rendering when:
- Image quality is a priority and a large number of lights and complex lighting models are used
- The scene is large and complex
- More efficient rendering is needed for scenes with many lights and objects
![image](https://github.com/cg20231c/unity-graphics-bangan/assets/97864068/f94d5197-8e9e-45db-aa11-f38ceaa8f083)

## Color Space
Besides picking a rendering path, you will also have to decide on a Color Space prior to illuminating your project. The Color Space choice dictates the mathematical approach Unity employs for blending colors in lighting calculations and interpreting data from textures. Frequently, your selection of Color Space will probably depend on the hardware constraints of your intended platform. This can be selected via **Edit > Project Settings > Player**

![image](https://github.com/cg20231c/unity-graphics-bangan/assets/97864068/8b0b45bd-07df-4334-9220-316c44d9cac8)


- **Linear Color Space**

  Color representation where the relationship between colors is maintained in a linear fashion, as opposed to the gamma-corrected color space, which has a non-linear relationship. Unity uses linear color space to accurately simulate how light interacts with materials in the real world. It's particularly useful for achieving realistic lighting and shading effects, as it ensures that the mathematical operations on color values behave as expected. Linear color space is typically used in high-quality, visually demanding projects where accurate color reproduction and physically-based rendering are essential, such as in AAA games or professional applications.

- **Gamma Color Space**

  gamma color space refers to a color rendering and lighting model that approximates the way the human eye perceives brightness. It uses gamma correction to apply a nonlinear adjustment to colors, making it suitable for displaying images and colors on standard monitors and televisions. Gamma correction helps to maintain more accurate and visually pleasing color and lighting results in a variety of lighting conditions. Gamma color space is typically used when working with legacy content or older rendering pipelines that rely on gamma-corrected textures and shaders, but it has largely been replaced by the more physically accurate linear color space in modern Unity workflows, especially for high-quality graphics and rendering.


![image](https://github.com/cg20231c/unity-graphics-bangan/assets/97864068/94e13d9a-3ad5-443b-883b-c2385d71f5e7)

![image](https://github.com/cg20231c/unity-graphics-bangan/assets/97864068/1282ebeb-ae1b-4e88-8941-0646c287da69)

## High Dynamic Range (HDR)
In addition to adjusting the Color Space, it is important to configure the dynamic range of your camera. Essentially, this setting determines how the camera captures extremely bright or dark colors in the scene. You can enable HDR (High Dynamic Range) from the Camera component in the Inspector by checking the HDR option. It's important to note that not all mobile hardware supports HDR, and it's also not compatible with Forward Rendering when using techniques like multi-sample anti-aliasing (MSAA). For optimal results, HDR is best used in conjunction with Linear Color Space to maintain color accuracy, as Unity's default setting is Low Dynamic Range (LDR). In LDR, colors are stored with 8 bits per channel for red, green, and blue, providing 256 possible unique combinations for each color channel, resulting in more than 16 million color variations. However, in reality, colors extend beyond this 16 million range, and Unity is capable of handling extremely bright colors that LDR cannot represent. Enabling HDR on your Scene camera allows colors to be stored with much greater precision using a floating-point representation, enabling handling of a broader range of luminance and preserving differences in brightness between various lighting conditions. This opens up the possibility of applying effects like blooms or glows to bright colors, adding realism to particles and other visible light sources, while ensuring that extreme color values are properly represented without being clamped to white.

![image](https://github.com/cg20231c/unity-graphics-bangan/assets/97864068/da9679f4-f34d-461f-8ef0-0f6789d5da2b)

**with hdr**


![image](https://github.com/cg20231c/unity-graphics-bangan/assets/97864068/a5111fd9-f8f2-464f-ab60-8c511fd59625)


The car window sun reflections in this scene have intensity values

**no hdr**


![image](https://github.com/cg20231c/unity-graphics-bangan/assets/97864068/d7276091-fa49-4dbc-9670-4f33003f95b1)


The car window will remain without glow if the camera is not HDR enabled. Only way to add glow is to lower the intensity threshhold but then unwanted parts of the image will start glowing as well.


## Tonemapping
Using the comparison of photography, when we capture a scene with varying exposure settings, we start revealing intricate color details that might have otherwise been obscured. The light tones in the brightest parts of an image, which had turned completely white, can be restored, and the dark tones, previously lost in deep black, can also be retrieved. This process is similar to tonemapping in computer graphics, where we take colors that fall outside the range that our target device, such as a computer screen, can reproduce, and then mathematically adjust them into a range that is displayable. The resulting output still maintains its perceptual integrity because the colors remain relative to each other and make sense in the given context. To utilize tonemapping, you will need to acquire the Post Processing package from the Package Manager by navigating to **Window > Package Manager** Tonemapping offers the ability to control how the extreme colors captured by your camera are transformed into colors that can be showcased.

![image](https://github.com/cg20231c/unity-graphics-bangan/assets/97864068/33a6a5c4-f66d-493e-93f1-b96cdb8efc9f)

![image](https://github.com/cg20231c/unity-graphics-bangan/assets/97864068/051dca90-8d4a-4033-82b8-da29c0ca61e1)


to import post processing you can go to main camera > add component > post-process layer and post-process volume

![image](https://github.com/cg20231c/unity-graphics-bangan/assets/97864068/c3d23988-ab0d-4999-a895-49d11fddc02f)


in post process volume you can add effect what you wanto to make


![image](https://github.com/cg20231c/unity-graphics-bangan/assets/97864068/449ec274-b273-412a-9e54-9faf384eab37)


![image](https://github.com/cg20231c/unity-graphics-bangan/assets/97864068/88c1b5e2-1804-447c-8ea8-f4a9ee46fcd8)

## Reflection
### 1. Reflection Source
Reflection Source is a component used to specify an object or a specific area within the game that will emit reflections. It can be objects such as water, mirrors, or highly reflective materials like glass. The reflection source emits the necessary light information to create more accurate and realistic reflections.

### 2. Reflection Probes
Reflection Probes are objects used to gathed environmental data from their surroundings and create a "cubemap" texture used to render reflections on objects that require them

## Ambient Lighting
Ambient lighting refers to the even and indirect light that illuminates a scene without a specific light source
