# Layout Specification — 4-Section Character Sheet

This document defines the exact per-section rules for the character sheet image. Reproduce these rules in the image-generation brief (Step 4 of SKILL.md).

## Frame

- **Aspect ratio:** 16:9
- **Background:** clean white, natural lighting
- **Global lighting:** neutral (soft, even, no harsh directional light unless the art style demands it)
- **Division:** the frame is split horizontally into **4 equal-width columns**. From viewer-left to viewer-right: Section 1, Section 2, Section 3, Section 4.

## Perspective convention (critical — state this in the brief)

All "left" and "right" labels below are from the **subject's** point of view, not the viewer's.

- Subject's **right** side → appears on the viewer's **left** side of the frame.
- Subject's **left** side → appears on the viewer's **right** side of the frame.

The image-generation brief must include this disambiguation verbatim. Image models routinely confuse subject-relative and camera-relative orientation, and a single misread flips half the sheet.

## Pose baseline (apply to all full-body views)

- **Humanoid:** A-pose. Arms held 30–45° away from the torso. Feet shoulder-width apart. Head level. Neutral expression unless the character concept demands otherwise.
- **Quadruped:** standing, all four limbs grounded, body facing the indicated camera direction, head level.
- **Avian / winged:** standing or perched, wings folded or held in resting position (not spread).
- **Aquatic / serpentine / abstract / chimeric:** the most natural neutral "at rest" posture for the body plan. No motion lines, no dynamic flow.

Forbid: action poses, combat stances, mid-stride motion, exaggerated emoting, "hero shots", floating, or anything that would obscure the silhouette.

## Section 1 — Subject's right-side three-quarter, full body

- **Camera position:** 45° to the subject's right and slightly elevated to subject eye-level.
- **What must read clearly:** the subject's **right** side — right eye, right ear/horn/antenna, right side of jaw or snout, right shoulder, right flank, right hip, right limb structure. Surface flow (fur direction, scale pattern, fabric drape) on the right side.
- **Shadow direction:** consistent with a soft frontal-right key light hitting the visible right side.
- **Full body:** the entire figure from head to feet (or equivalent terminal anatomy) fits within the section with comfortable margin.

## Section 2 — Front, full body

- **Camera position:** dead-center frontal, at subject's chest height.
- **What must read clearly:** bilateral symmetry (or asymmetry, if intentional), face, chest, abdomen, hands, feet, frontal silhouette. Both eyes visible. Centerline features (medallion, belt buckle, sternum marking, etc.) on the vertical axis of the section.
- **Shadow direction:** soft, even, slightly from above. No strong directional shadow that would hide either side.

## Section 3 — Rear, full body

- **Camera position:** directly behind the subject, at the same elevation as Section 2.
- **What must read clearly:** back surface, occiput (back of head), shoulder blades or wing roots, spine, tail (if present), shell or carapace (if present), heel and posterior limb structure. Hair flow, fur whorl, cape drape, or wing fold from behind.
- **Pose:** same neutral baseline as Sections 1 and 2 — do NOT re-pose for the rear view.

## Section 4 — Head close-up triptych (vertical 3-row split)

Section 4 is subdivided into **three equal-height rows**, all framed from the top of the neck/collar to the crown of the head. The body below the neck is not shown in Section 4.

### 4a — Top row: subject's right three-quarter face

- 45° from the subject's right, head-and-neck framing.
- Emphasize: right-side facial structure, right brow, right cheek, right ear, right horn or other side-specific feature, right-side surface detail.

### 4b — Middle row: front face

- Dead-center frontal, head-and-neck framing.
- Emphasize: bilateral facial structure, both eyes, nose/snout/beak center, mouth, frontal forehead and chin detail. Any centerline facial markings should be on the section's vertical axis.

### 4c — Bottom row: subject's left three-quarter face

- 45° from the subject's left, head-and-neck framing.
- Emphasize: left-side facial structure, left brow, left cheek, left ear, left horn or other side-specific feature, left-side surface detail.

## Anti-mirroring constraint (state this verbatim in the brief)

The 4 main sections and the 3 face close-ups together form **7 structurally distinct camera setups**. None of them may be produced by flipping another horizontally.

A correct sheet shows real geometric difference between views:
- Different parts of the anatomy are visible.
- Silhouettes have different outlines.
- Surface flow (fur, scales, fabric folds) runs in genuinely different directions.
- Cast shadows fall on different sides.

If two views look like mirror images of each other, the sheet is wrong — the model has cheated. Call this out explicitly in the brief.

## Consistency constraint (state this verbatim in the brief)

Across all 7 views, the following must remain identical:
- Body proportions and scale relationships (head-to-body ratio, limb length, etc.)
- Color palette (every named color from the design spec appears in the same role across all views)
- Markings, scars, tattoos, freckles, asymmetric features — in the correct location on the body
- Clothing, props, and equipment — same items, same wear, same condition
- Apparent age, weight, and overall vibe

The sheet must read as **one individual photographed/painted from seven angles**, not seven similar individuals.

## Style adherence

The chosen art style applies globally and uniformly. Do not switch styles between sections. If the style is `hyper-realistic photo`, every section is a photo. If the style is `flat 2D anime`, every section is flat 2D anime. No mixing.
