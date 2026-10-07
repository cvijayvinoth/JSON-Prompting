# JSON Prompting: Video Generation Using SCALE

Video generation models (Runway Gen-3 Alpha, Luma Dream Machine, Kling AI, OpenAI Sora) require strict control over camera trajectories and kinetic consistency across time. 

The SCALE framework adapts to video by extending **Composition** into camera motions and **Action** into temporal step progressions.

---

## Video-Extended SCALE Parameters

| Parameter | Extension Key | Description |
| :--- | :--- | :--- |
| **C** (Composition) | `camera_motion` | Dolly, pan, tilt, orbit, tracking, crane, zoom velocity |
| **A** (Action) | `temporal_progression` | Movement sequence broken down by seconds |
| **A** (Action) | `speed` | Slow-motion (120 fps), real-time (24 fps), hyperlapse |
| **E** (Esthetic) | `motion_blur` | Shutter angle (180 deg), optical stability |

---

## Video JSON Schema Example

```json
{
  "task": "video_generation",
  "duration_seconds": 5,
  "fps": 24,
  "scale": {
    "subject": {
      "entity": "Futuristic VTOL aircraft",
      "details": "twin tilt-rotors spinning, heat distortion from jet nozzles, carbon-composite fuselage"
    },
    "composition": {
      "framing": "wide dynamic chase shot",
      "lens": "24mm ultra-wide",
      "camera_motion": {
        "type": "forward_tracking_dolly",
        "movement": "tracking closely behind the craft, slowly orbiting 30 degrees to the right",
        "speed": "accelerating"
      },
      "aspect_ratio": "16:9"
    },
    "action": {
      "temporal_progression": [
        {
          "seconds": "0.0 - 2.0",
          "event": "VTOL transitions from hover mode to forward propulsion, tilting rotors horizontal"
        },
        {
          "seconds": "2.1 - 5.0",
          "event": "Vessel blasts forward, cutting through low-hanging clouds and leaving dual condensation trails"
        }
      ],
      "physics": "realistic aerodynamic drag, volumetric cloud displacement"
    },
    "location": {
      "environment": "over a cloud-blanketed mountain ridge at dusk",
      "lighting": "intense golden hour sun backlighting the aircraft, fiery orange reflections on cockpit glass",
      "atmosphere": "wisps of turbulent fog tearing across the lens"
    },
    "esthetic": {
      "style": "photorealistic cinematic action film",
      "color_grade": "warm amber and deep navy contrast",
      "optics_behavior": "anamorphic horizontal lens flare, subtle motion blur"
    }
  }
}
```

---

## Compiling for Video Platforms

### Runway Gen-3 Alpha Format
Runway works best with clear camera trajectory notation at the start:
```text
[Camera Motion]: Forward tracking chase shot, orbiting right. 
[Subject]: Futuristic VTOL aircraft with spinning tilt-rotors. 
[Action]: Rotors transition from hover to horizontal forward flight, then accelerating forward through cloud banks. 
[Environment]: Golden hour clouds over mountain ridge with lens flare. Cinestill 800T, cinematic 24fps.
```

### Luma Dream Machine / Kling AI Format
```text
Dynamic tracking shot behind a futuristic VTOL aircraft as it tilts its twin rotors forward from hover into high-speed flight. Jet nozzle heat distortion visible. Golden hour lighting hitting misty mountain clouds below. 24mm wide angle, cinematic motion blur.
```

---

## Best Practices for Video JSON

1. **Avoid Contradictory Movements**: Do not combine conflicting vectors in `composition.camera_motion` (e.g., avoid `dolly_in` simultaneously paired with `fast_zoom_out` unless a Hitchcock vertigo effect is explicitly desired).
2. **Cap Action Density**: Maintain a realistic pacing boundary. An action sequence should describe 1 to 2 distinct transitions per 5-second interval to avoid temporal morphing.
3. **Explicit Continuity**: When chaining prompts into multi-scene sequences, keep the `subject` and `esthetic` blocks identical while altering only `composition`, `action`, and `location`.
