# Unity-Nanite-Seamless-Virtual-Geometry

Nanite in Unity Now!  
📘 Online Document: https://zenginestudios.github.io/

## 🎥 YouTube Demos

[![Video 1](https://img.youtube.com/vi/BfrKjMJbpjc/0.jpg)](https://www.youtube.com/watch?v=BfrKjMJbpjc)  
[![Video 2](https://img.youtube.com/vi/Mvty08Og7Lo/0.jpg)](https://www.youtube.com/watch?v=Mvty08Og7Lo)  
[![Video 3](https://img.youtube.com/vi/BMM8glnEb9o/0.jpg)](https://www.youtube.com/watch?v=BMM8glnEb9o)  
[![Video 4](https://img.youtube.com/vi/wklo_K_ixQI/0.jpg)](https://www.youtube.com/watch?v=wklo_K_ixQI)  
[![Video 5](https://img.youtube.com/vi/yaKzL0-Msgo/0.jpg)](https://www.youtube.com/watch?v=yaKzL0-Msgo)

## 🧾 Summary

A Unity package inspired by Virtual Geometry, enabling massive, detailed asset rendering with seamless LOD management and virtualized geometry. It is a fully GPU-driven solution.

Seamless Virtual Geometry is a package similar to Unreal's Virtual Geometry. This package allows developers to render massive amounts of detailed assets with unparalleled efficiency, leveraging advanced level-of-detail (LOD) management. Some source code is provided, while the core code and shaders are provided in the form of DLLs and Asset Bundles.

## ⚙️ Description

### ✅ Supported Features:

- Meshlet LOD and BVH node generation  
- Meshlet LOD hierarchy  
- BVH tree  
- Instance GPU frustum and occlusion culling  
- BVH node GPU frustum and occlusion culling with LOD traversal  
- Meshlet GPU frustum and occlusion culling  
- Hardware rasterizer  
- Visibility buffer  
- Shadow support, including point light shadows and directional light shadows (CSM)  
- Deferred material  
- Per-chunk material culling  
- Single-phase Occlusion Culling  
- Programmable rasterizer (Alpha Test)  
- Skinned mesh  
- Rendering layer supported  
- Deferred shading only  
- Per-object GI is supported (per-object light probe, reflection probe and Lightmap)  
- Meshlet generation speed up  

### ❌ Not Supported Yet:

- No software rasterizer  
- No two phase Occlusion Culling  
- No Streaming  
- No Compression currently  
- Not Support Unity Terrain (no plan to support)  

## 📖 User Guide

- Try the package with an empty URP Core project and enter the demo scene.  
- The demo folder can be safely deleted.  
- If you encounter any issues, please send me an email with your Unity version, URP version, and a detailed description of the problem. If possible, provide the simplest reproducible version of the issue. Or commit a GitHub issue.  
- 📧 Email: [zenginestudios@hotmail.com](mailto:zenginestudios@hotmail.com)

## 📄 License

This software is licensed under the MIT License, with the following additional condition:

> If you use this software in a released game or product, you must:  
> - Allow your product to be listed publicly as a user of this software;  
> - Include a visible reference to this repository in your product’s “About” or “Credits” page.  

❗Failure to comply with these terms terminates your right to use this software.

## ☕ Support This Project

If you like this project, please consider buying me a coffee:

<a href="https://ko-fi.com/zenginestudios" target="_blank">
  <img src="https://cdn.ko-fi.com/cdn/kofi_button.png" alt="Buy Me a Coffee" style="height: 36px;" />
</a>

## 📦 Dependencies

This project makes use of the following open-source or external libraries:

- **Meshoptimizer** (used for meshlet generation) — [https://github.com/zeux/meshoptimizer](https://github.com/zeux/meshoptimizer)
- **METIS** (BVH build) — [https://github.com/KarypisLab/METIS](https://github.com/KarypisLab/METIS)
- **nanite-webgpu** (Inspired strongly by) — [https://github.com/Scthe/nanite-webgpu](https://github.com/Scthe/nanite-webgpu)
