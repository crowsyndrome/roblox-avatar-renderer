# Roblox Avatar Renderer

Renders Roblox avatars in 3D using Three.js by fetching avatar data via Roblox User ID. Provides controls for lighting, shadows, SSAO, and allows exporting to GLTF, OBJ, or as a screenshot.

## Live Demo

[https://crowsyndrome.github.io/roblox-avatar-renderer/]

## Core Features

* **Roblox Avatar Fetching:** Loads avatar assets (OBJ/MTL) by User ID using Roblox's public APIs via a CORS proxy.
* **3D Rendering:** Utilizes Three.js for scene creation, rendering, and camera controls (OrbitControls).
* **Lighting Control:**
    * Ambient Light: Color and intensity.
    * Directional Light: Color, intensity, position, and shadow softness (radius).
* **Shadows:** Dynamic VSMShadowMap for softer shadows.
* **SSAO (Screen Space Ambient Occlusion):** Post-processing effect for enhanced realism with configurable kernel radius, min/max distance.
* **Scene Customization:**
    * Adjustable background color.
    * Toggleable ground plane.
* **Export Options:**
    * **Screenshot (PNG):** Captures the current view.
    * **GLTF (.gltf):** Exports the avatar model with embedded textures.
    * **OBJ (.obj):** Exports the avatar model. Textures might require manual linking in external software.
* **Responsive UI:** Controls for all features are available in a side panel.

## Technologies Used

* **HTML5, CSS3, JavaScript (ES6+)**
* **Three.js (r128):** Core 3D rendering library.
    * `OBJLoader`: For loading Roblox avatar models.
    * `OrbitControls`: For camera manipulation.
    * `EffectComposer`, `RenderPass`, `SSAOPass`, `ShaderPass`: For post-processing effects.
    * `GLTFExporter`, `OBJExporter`: For model exporting.
    * `VSMShadowMap`: For shadow rendering.
* **CORS Proxy:** Uses `corsproxy.io` to bypass CORS restrictions when fetching Roblox assets.

## Setup & Usage

1.  Open `index.html` in a modern web browser.
    * All dependencies (Three.js modules) are loaded via CDN. No local server or build step is strictly required for basic operation if a CORS proxy is available and browser security settings permit.
    * For development or to avoid potential public proxy issues, running a local server that can proxy requests might be beneficial.
2.  Enter a valid Roblox User ID into the input field.
3.  Click "Render Avatar".
4.  Use the UI controls to adjust scene parameters, lighting, SSAO, and export the result.

## Key Constants & Configuration

* `PROXY`: `https://corsproxy.io/?url=`

## Notes & Limitations

* **CORS Proxy:** The application relies on an external CORS proxy (`corsproxy.io`) to fetch Roblox assets due to browser security restrictions. The reliability of this proxy can affect the application.
* **Roblox API Changes:** Functionality may break if Roblox changes its avatar asset API endpoints or data structures.
* **OBJ Texture Linking:** When exporting to OBJ, textures are not embedded. They may need to be manually downloaded and linked in 3D editing software. GLTF export is recommended for easier texture handling.
* **Performance:** Rendering complex avatars or enabling intensive SSAO settings might impact performance on lower-end devices.

## Future Considerations

* Implement a self-hosted CORS proxy solution.
* More advanced material properties.
* Allow direct texture URL input for OBJ exports.