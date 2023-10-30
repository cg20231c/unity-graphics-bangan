# Lighting and Rendering

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



