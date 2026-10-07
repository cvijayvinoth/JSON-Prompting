# Image Generation Using SCALE

This guide details how to implement the SCALE framework for static image generation platforms such as Midjourney, Flux.1, and Stable Diffusion XL.

---

## Production JSON Schema

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "title": "SCALE_Image_Prompt",
  "type": "object",
  "properties": {
    "subject": {
      "type": "object",
      "properties": {
        "entity": { "type": "string" },
        "features": { "type": "array", "items": { "type": "string" } },
        "clothing": { "type": "string" }
      },
      "required": ["entity"]
    },
    "composition": {
      "type": "object",
      "properties": {
        "framing": { "type": "string" },
        "focal_length": { "type": "string" },
        "depth_of_field": { "type": "string" },
        "aspect_ratio": { "type": "string" }
      },
      "required": ["framing", "aspect_ratio"]
    },
    "action": {
      "type": "object",
      "properties": {
        "stance": { "type": "string" },
        "expression": { "type": "string" }
      }
    },
    "location": {
      "type": "object",
      "properties": {
        "environment": { "type": "string" },
        "lighting_setup": { "type": "string" },
        "time_of_day": { "type": "string" }
      },
      "required": ["environment", "lighting_setup"]
    },
    "esthetic": {
      "type": "object",
      "properties": {
        "style": { "type": "string" },
        "color_profile": { "type": "string" },
        "rendering_engine": { "type": "string" }
      },
      "required": ["style"]
    }
  },
  "required": ["subject", "composition", "action", "location", "esthetic"]
}
```

---

## Real-World Case Studies

### 1. High-Fashion Editorial Photography

```json
{
  "subject": {
    "entity": "Scandinavian model",
    "features": ["sharp cheekbones", "slicked-back platinum blonde hair", "natural skin texture with subtle freckles"],
    "clothing": "structured sculptural metallic silver trench coat with oversized lapels"
  },
  "composition": {
    "framing": "waist-up medium portrait",
    "focal_length": "85mm prime lens",
    "depth_of_field": "shallow f/1.8, creamy background falloff",
    "aspect_ratio": "4:5"
  },
  "action": {
    "stance": "torso angled three-quarters, head turned toward the viewer",
    "expression": "haughty, calm, direct gaze into camera"
  },
  "location": {
    "environment": "minimalist brutalist concrete studio",
    "lighting_setup": "single high-contrast Profoto softbox from top-right, sharp shadow falloff",
    "time_of_day": "indoor studio"
  },
  "esthetic": {
    "style": "high-fashion editorial photography",
    "color_profile": "muted tones, cool silvers, stark blacks",
    "rendering_engine": "Hasselblad H6D-100c medium format"
  }
}
```

**Compiled Prompt (Flux / Midjourney):**
> High-fashion editorial waist-up portrait of a Scandinavian model with sharp cheekbones, slicked-back platinum hair, natural skin texture with freckles, wearing a structured sculptural metallic silver trench coat. Torso angled three-quarters, direct gaze. Minimalist brutalist concrete studio, high-contrast overhead softbox lighting with sharp shadows. Shot on Hasselblad H6D-100c, 85mm prime lens, f/1.8 shallow depth of field. Muted cool silver tones. --ar 4:5

---

### 2. Product Render (Industrial Design)

```json
{
  "subject": {
    "entity": "Mechanical chronograph watch",
    "features": ["exposed tourbillon movement", "titanium bezel", "matte black sapphire dial"],
    "clothing": "perforated black Italian leather strap with orange stitching"
  },
  "composition": {
    "framing": "macro close-up",
    "focal_length": "100mm macro",
    "depth_of_field": "deep focus f/11",
    "aspect_ratio": "1:1"
  },
  "action": {
    "stance": "resting angled at 45 degrees on raw slate rock",
    "expression": "second hand caught mid-sweep"
  },
  "location": {
    "environment": "dark mineral studio setting",
    "lighting_setup": "dual rim lights defining titanium edges, subtle soft rim bounce on dial",
    "time_of_day": "controlled studio"
  },
  "esthetic": {
    "style": "luxury commercial product photography",
    "color_profile": "deep slate grey, titanium highlights, punchy orange accents",
    "rendering_engine": "Octane Render, ray-traced reflections"
  }
}
```
