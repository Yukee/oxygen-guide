# Prompt: Breathing Equipment Comparison

## Final prompt (used to generate the base image)

```
Clean flat infographic illustration on a light cream background. Blue and teal color palette. Medical educational style, not photorealistic. Simple clean lines and shapes. 16:9 aspect ratio. NO title at the top.

A comparison chart of three oxygen breathing equipment options for cluster headache patients, arranged left to right from best to worst.

People shown should have friendly, approachable faces in three-quarter view. In EVERY panel, the person uses ONE HAND to hold the device firmly pressed against their face. The hand should be clearly visible gripping the mouthpiece or mask to their mouth.

ABSOLUTE RULES:
- No straps on any masks
- ZERO arrows anywhere in the entire image. Not a single arrow. No directional indicators of any kind.
- All breathing bags are OPAQUE solid colored rubber — not transparent, not see-through

LEFT THIRD (header: "BEST — Demand Valve", 3 blue stars below header):
Two sub-panels.
Left: person in three-quarter view, hand holding a round disc-shaped demand valve RIGHT AT THEIR MOUTH, biting on the mouthpiece that plugs into it. The demand valve is a palm-sized puck shape. A single hose runs down from the back. Label below: "Mouthpiece"
Right: same person in three-quarter view, hand pressing a simple sealed face mask (NO holes, NO vents) against their nose and mouth. The mask connects to the identical round demand valve right at the face. Same hose down. Label below: "Mask"
Circular inset below labeled "DISS fitting": a threaded metal DISS connector.

CENTER THIRD (header: "GOOD — ClusterO2 Kit", 2 blue stars below header):
Two sub-panels. The device is a T-shaped connector with exactly 3 openings: top to patient, bottom to ONE large OPAQUE solid green elongated oval bag, left arm to oxygen tube.
Left: person in three-quarter view, hand holding mouthpiece to mouth. Mouthpiece into top of T. Large opaque green bag hangs down. Tube exits left. Label below: "Mouthpiece"
Right: same person in three-quarter view, hand pressing sealed mask (NO holes, NO vents) to face. Mask into top of T. Same green bag, same tube. Label below: "Mask"
Circular inset below labeled "Barb fitting": oxygen tube from left sliding onto a tapered barbed fitting on right.

RIGHT THIRD (header: "BASIC — Non-Rebreather Mask", 1 blue star below header):
Single panel: person in three-quarter view, hand pressing a non-rebreather mask to face. The mask has visible round holes on its sides. NO arrows, NO indicators pointing at the holes. A large OPAQUE solid colored reservoir bag below the mask. Tubing runs down. Label below: "Mask"
Circular inset below labeled "Barb fitting": identical to center section.
```

## Edit pass (applied to the base image)

The base image was then passed back to the model with this edit prompt:

```
Recreate this infographic illustration at higher quality and sharper resolution. Make all lines crisper, text sharper, and colors more vibrant. The image should look like a clean vector-style illustration.

Make exactly ONE change to the content:

In the DISS fitting circular inset (bottom left corner), REMOVE the cable/hose entirely. The inset should show ONLY the threaded metal DISS connector by itself — no cable, no hose, no tube attached to it. Just the metal fitting floating in the circle.

Everything else must remain EXACTLY the same: same layout, same people, same poses, same style, same colors, same headers ("BEST — Demand Valve", "GOOD — ClusterO2 Kit", "BASIC — Non-Rebreather Mask"), same star ratings, same "Mouthpiece" and "Mask" labels, same "DISS fitting" and "Barb fitting" text, same barb fitting insets. Only remove the cable from the DISS inset and make the whole image sharper.
```

## Notes

- "Barb outlet" was renamed to "Barb fitting" in an intermediate edit pass
- The model persistently tries to add arrows pointing to NRB mask vents — must explicitly forbid
- The model persistently adds straps to masks — must explicitly forbid
- Three-quarter view with hand holding device to face gives the best results
- Opaque bags must be specified or they look like they contain liquid
- The demand valve must be described as "right at the mouth" or it drifts away
- The ClusterO2 T-junction must be described as having exactly 3 connections or the model adds extra tubes
