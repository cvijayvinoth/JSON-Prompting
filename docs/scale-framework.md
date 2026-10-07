# The SCALE Framework: Foundational Specification

The **SCALE Framework** provides a syntax-safe schema for multi-agent visual generation pipelines. It decomposes generative tasks into five atomic domains to prevent model prompt drift.

---

## Schema Architecture

```text
SCALE
├── [S] Subject       -> Identity, features, apparel, materials
├── [C] Composition   -> Camera placement, lens specs, focal depth, framing
├── [A] Action        -> Poses, kinetics, micro-gestures, temporal states
├── [L] Location      -> Environment, background depth, atmospheric conditions, light sources
└── [E] Esthetic      -> Artistic direction, rendering pipeline, color grade, film stock
```

---

## Layer Definitions

### 1. Subject (`subject`)
Defines *what* or *who* commands focal priority.
- `count`: Number of primary subjects.
- `identity`: Core taxonomy (e.g., "elderly artisan", "robotic mechanical hound").
- `attributes`: Physical details, skin textures, scars, eye colors, age indicators.
- `wardrobe`: Detailed apparel, textile physics, fabric types.

### 2. Composition (`composition`)
Instructs the virtual camera and optical geometry.
- `shot_type`: Extreme close-up, close-up, medium shot, wide shot, extreme long shot.
- `angle`: Eye-level, low-angle hero, bird's-eye view, Dutch angle.
- `optics`: Focal length (e.g., 24mm, 50mm, 85mm), aperture (f/1.4, f/8), anamorphic bokeh.
- `aspect_ratio`: Format ratio (e.g., `16:9`, `1:1`, `9:16`, `2.39:1`).

### 3. Action (`action`)
Specifies motion, kinematics, and kinetic energy.
- `pose`: Static posture, skeletal orientation.
- `gesture`: Active movements (e.g., "reaching toward lens", "sprinting through water").
- `gaze`: Line of sight (e.g., "direct eye contact with lens", "looking over shoulder").

### 4. Location (`location`)
Establishes spatial context, atmospheric volume, and illumination.
- `setting`: Interior/exterior architectural context.
- `lighting`: Key light, fill light, back light, volumetric god-rays, rim lighting.
- `atmosphere`: Rain, volumetric fog, haze, dust particles, reflections.

### 5. Esthetic (`esthetic`)
Defines the technical and visual pipeline signature.
- `medium`: Photography, oil painting, 3D Octane render, anime illustration.
- `color_science`: Color grade, LUT profiles (e.g., "teal and orange", "monochromatic sepia").
- `fidelity_markers`: 35mm grain, subsurface scattering, chromatic aberration, ray tracing.

---

## Compiling SCALE JSON to Linear Prompts

When sending to models that do not accept JSON directly (e.g., Midjourney), compile using a template string:

```text
[Subject], [Action], [Location], [Composition], [Esthetic] --ar [aspect_ratio]
```
