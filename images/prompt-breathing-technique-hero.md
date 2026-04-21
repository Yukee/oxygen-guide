# Prompt: Breathing Technique Hero

## Final prompt (used to generate the image)

```
Clean flat infographic illustration on a light cream background. Blue and teal color palette. Medical educational style, not photorealistic. Simple clean lines and shapes. 16:9 aspect ratio.

Two-panel infographic showing the cluster headache hyperventilation breathing technique using a ClusterO2 kit (no mask, mouthpiece only).

FRAMING: each panel is a MEDIUM SHOT of the UPPER BODY only (head, shoulders, chest, down to about mid-torso). Feet and legs OUT OF FRAME. Equipment at realistic scale — T-junction roughly fist-sized, green bag about grapefruit-sized (clearly smaller than the head).

VIEW ANGLE (critical): BOTH persons are shown in THREE-QUARTER VIEW — body turned partly toward the viewer but angled slightly, face visible at a 3/4 angle (not full-front, not full-profile). Both panels use the SAME three-quarter angle so the two figures clearly match as the same person.

EQUIPMENT (identical in both panels):
- The ClusterO2 kit has a T-shaped connector with THREE openings: one side horizontal (to mouthpiece going to the mouth), the other side horizontal (to oxygen tube going away behind person), and the bottom (to green bag hanging straight down)
- A short cylindrical bite-style mouthpiece — HORIZONTAL orientation, sticking out sideways from the side of the T-junction toward the person's mouth at mouth-level
- The mouthpiece is horizontal, like a cigarette or whistle — NOT vertical, NOT pointing upward
- Green reservoir bag is OPAQUE solid green rubber, hanging straight down below the T

HAND POSITION (same in both panels): hand grips the T-junction body itself from below, fingers wrapping around it just above where the green bag attaches. Hand does NOT grip the mouthpiece.

TUBE ROUTING (same in both panels): the oxygen tube exits the opposite side of the T from the mouthpiece, routes back and disappears BEHIND the person's shoulder/body (drawn partly occluded by the torso to convey depth), and exits the frame.

PANEL 1 (left), labeled "INHALE FULLY" below:
- Three-quarter view of person, upright standing posture (upper body only)
- Plain teal/blue t-shirt
- Mouth sealed around the horizontal mouthpiece
- CLEARLY FORCEFUL INHALE: chest dramatically puffed up and expanded, shoulders raised, head tilted slightly back, eyebrows furrowed with effort, subtle motion lines at the shoulders/chest. The strain of a big forceful inhale must be visible — mirror the effort shown in panel 2's exhale.
- Green bag FULL, plump, inflated
- EXACTLY ONE single continuous blue arrow inside the flow path — starts inside the green bag, runs up through the T-junction, ends pointing into the mouthpiece

PANEL 2 (right), labeled "EXHALE FULLY" below:
- Same three-quarter view angle as panel 1, same person, same teal shirt
- Bent slightly forward at the waist, abdominal area engaged to forcefully expel air
- Hand grips T-junction lower stem, equipment held slightly AWAY from mouth (mouthpiece still horizontal)
- Mouth open, breath puffs coming OUT
- Green bag visibly DEFLATED — flatter, limper than panel 1
- ZERO arrows inside tubing/equipment (breath puffs at mouth are fine)

BETWEEN THE PANELS:
- EXACTLY ONE curved loop arrow and ONE instance of "repeat as fast as possible" — never duplicated

ABSOLUTE RULES:
- Both figures in THREE-QUARTER view at matching angle
- Mouthpiece is HORIZONTAL, not vertical
- Panel 1: clearly forceful inhale (big chest puff, raised shoulders, effort lines, furrowed brow)
- Panel 2: forward lean, deflated bag
- Upper body framing only, no legs
- Hand grips lower stem of T, not the mouthpiece
- Tube routes BEHIND the body (partially occluded by torso)
- Green opaque bag. No mask.
```

## Notes

- The model tends to draw multiple arrows inside the flow path unless explicitly constrained to ONE continuous arrow
- Must explicitly forbid duplicate "repeat as fast as possible" labels — the model sometimes stamps the text twice
- The model defaults to a vertical/upward-pointing mouthpiece unless "HORIZONTAL, like a cigarette or whistle" is specified
- "Tube routes BEHIND the body (partially occluded by torso)" is the phrasing that finally produced proper depth — "behind the person" alone was ambiguous
- Forceful inhale posture needs concrete cues (puffed chest + raised shoulders + furrowed brow + motion lines) — asking for "effort" alone produces a neutral face
- Upper-body-only framing prevents the equipment from being drawn oversized
- Hand must be explicitly told to grip the LOWER stem of the T, not the mouthpiece, or the model puts fingers on the mouthpiece itself
