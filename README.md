# JSON Prompting for Generative AI

A structured, schema-driven approach to generative AI prompting. By utilizing JSON rather than unstructured natural language, prompt engineers and developers can eliminate ambiguity, enforce modular prompt structures, ensure repeatability, and programmatically generate complex multimodal assets.

---

## 📑 Repository Structure

```text
├── README.md
├── docs/
│   ├── scale-framework.md          # Core architecture of the SCALE framework
│   ├── image-generation-scale.md   # Image prompting schema & Midjourney/Flux workflows
│   └── video-generation-scale.md   # Video synthesis schema, camera motion, and timeline logic
├── schemas/
│   ├── image-scale.json            # JSON Schema for static image generation
│   └── video-scale.json            # JSON Schema for video generation
└── Examples/
    ├── english_prompt-video.json            # JSON Schema for static video generation
    ├── tamil_prompt-video.json              # JSON Schema for video generation
    └── english_prompt-image.json            # JSON Schema for static image generation
```

---

## 🎯 Why JSON Prompting?

- **Deterministic Weights & Structure**: Clear separation of subjects, environment, camera angles, and rendering engines.
- **Programmatic Control**: Easily inject parameters via backend pipelines (Node.js, Python, Next.js).
- **Reduced Hallucinations**: Constrains generative models (GPT-4o, Claude 3.5 Sonnet, Gemini Pro) when converting prompt requests into diffusion or video model prompts.
- **Model Agnostic**: Converts cleanly into Midjourney parameters, Flux raw text, Stable Diffusion prompt fragments, Runway Gen-3/Luma/Kling camera prompts.

---

## 📐 The SCALE Framework Overview

The **SCALE** framework structures visual generation requests into five distinct semantic layers:

| Layer | Key | Purpose |
| :--- | :--- | :--- |
| **S** | `subject` | Primary entities, attributes, garments, micro-details |
| **C** | `composition` | Shot type, framing, camera angle, focal length, aspect ratio |
| **A** | `action` | Poses, physical movements, gaze direction, interactions |
| **L** | `location` | Foreground, background, environment, lighting, weather |
| **E** | `esthetic` | Visual style, art direction, color grading, film stock / render engine |

---

## 🚀 Quick Start Example

A standardized SCALE JSON prompt:

```json
{
  "version": "1.0",
  "task": "image_generation",
  "scale": {
    "subject": {
      "type": "human",
      "identity": "Cyberpunk courier",
      "features": ["late 20s", "augmented carbon-fiber prosthetic arm", "sweat on brow"],
      "attire": "weathered neon-yellow technical rain poncho, high-collar tactical vest"
    },
    "composition": {
      "framing": "medium_shot",
      "angle": "low_angle",
      "lens": "35mm anamorphic",
      "aspect_ratio": "16:9"
    },
    "action": {
      "primary": "leaning against a sleek neon-lit hoverbike",
      "expression": "alert, scanning the alleyway",
      "interaction": "holding a glowing data drive in left hand"
    },
    "location": {
      "environment": "dense neon-lit Shinjuku back-alley at midnight",
      "weather": "heavy downpour, damp wet asphalt with puddles",
      "lighting": "harsh neon magenta rim light combined with cool blue ambient reflections"
    },
    "esthetic": {
      "style": "cinematic realism",
      "render": "Kodak Vision3 500T 5219 film stock, authentic 35mm grain",
      "color_palette": ["neon magenta", "cyan", "deep slate grey"]
    }
  }
}
```

---

## 📚 Guides

1. [The SCALE Framework Core Guide](docs/scale-framework.md)
2. [Image Generation Using SCALE](docs/image-generation-scale.md)
3. [Video Generation Using SCALE](docs/video-generation-scale.md)

---
