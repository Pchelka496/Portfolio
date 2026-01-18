<h2>🌱 Grass Rendering & GPU Culling</h2>

<p>
A fully custom grass rendering system designed for large-scale environments, combining CPU and GPU culling with procedural generation and GPU-driven rendering.
</p>

<hr>

<h3>🧩 GPU Culling</h3>
<p align="center">
  <img src="Grass/culling.png" width="720">
</p>

<p>
The grass system uses a <b>hybrid culling approach</b> to efficiently handle large amounts of vegetation.
</p>

<ul>
  <li>CPU culling operates on spatial grass chunks</li>
  <li>Chunks support different sizes and variable grass height</li>
  <li>Invisible or distant chunks are fully discarded on the CPU</li>
  <li>Visible chunks are processed further on the GPU</li>
</ul>

<p>
This significantly reduces CPU overhead while keeping GPU workloads tightly bounded.
</p>

<hr>

<h3>🌿 Grass Rendering</h3>
<p align="center">
  <img src="Grass/grass.gif" width="48%" style="margin-right:2%">
  <img src="Grass/grass_1.gif" width="48%">
</p>

<p>
Grass instances are generated <b>automatically from terrain data</b>.
The system supports multiple terrain layers, allowing different grass types, densities, and visual parameters per layer.
</p>

<ul>
  <li>Layer-based procedural generation</li>
  <li>Consistent distribution across large terrains</li>
  <li>Per-layer control over density and height</li>
</ul>

<p>
Rendering is fully GPU-driven using <b>Graphics.DrawMeshInstancedIndirect</b>, enabling large instance counts with minimal CPU cost.
</p>

<hr>

<h3>🍃 Grass Bending</h3>
<p align="center">
  <img src="Grass/grassBend.gif" width="720">
</p>

<p>
Wind animation is implemented as a <b>three-band system</b>, providing natural and scalable motion.
</p>

<ul>
  <li>Low-frequency global wind</li>
  <li>Mid-frequency directional movement</li>
  <li>High-frequency local noise for detail</li>
</ul>

<p>
Color variation is driven by a <b>color map</b> combined with three additional tint colors:
</p>

<ul>
  <li>Root tint</li>
  <li>Mid-section tint</li>
  <li>Tip tint</li>
</ul>

<p>
This approach adds depth and variation while avoiding visible repetition.
</p>

<hr>

<h2>☁️ Volumetric Clouds</h2>

<p align="center">
  <img src="VolumetricClouds/Cloud.gif" width="720">
</p>

<p>
A real-time volumetric cloud system implemented as a <b>ScriptableRendererFeature</b>, focused on artistic flexibility and performance.
</p>

<ul>
  <li>Raymarch-based volumetric rendering</li>
  <li>Custom 3D textures for cloud shape and fine detail</li>
  <li>Additional noise textures and jitter for variation</li>
</ul>

<p align="center">
  <img src="VolumetricClouds/Cloud_0.png" width="48%" style="margin-right:2%">
  <img src="VolumetricClouds/Cloud_1.png" width="48%">
</p>

<p>
The system includes tools for generating and tuning the 3D textures used for cloud form and detail layers.
Lighting supports adjustable sun influence and cloud coloration.
</p>

<p>
Cloud movement is controlled via a configurable wind system with parameters for direction and strength.
</p>

<hr>

<h2>💡 Volumetric Light</h2>

<p align="center">
  <img src="VolumetricLight/VLight.gif" width="720">
</p>

<p>
A custom volumetric lighting solution built using a <b>ScriptableRendererFeature</b>, designed for cinematic light shafts and atmospheric depth.
</p>

<p align="center">
  <img src="VolumetricLight/VLight_2.png" width="720">
</p>

<p>
The effect is composed of four main rendering passes:
</p>

<ol>
  <li><b>Raymarch Pass</b> – computes volumetric light scattering</li>
  <li><b>Horizontal Blur</b> – reduces noise</li>
  <li><b>Vertical Blur</b> – reduces noise</li>
  <li><b>Composite Pass</b> – blends the result with the scene</li>
</ol>

<ul>
  <li>Optional render target downscaling for performance</li>
  <li>Jitter-based sampling to reduce raymarch steps</li>
  <li>Blur passes used to hide sampling artifacts</li>
</ul>

<hr>

<p>
<b>Technologies:</b> Unity · URP · HLSL · Compute Shaders · GPU Instancing · ScriptableRendererFeature
</p>
