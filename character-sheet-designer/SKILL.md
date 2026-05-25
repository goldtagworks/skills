---
name: character-sheet-designer
description: Design a single coherent character from user-specified traits and produce a structured 4-section character sheet specification ready for image generation. Use this skill whenever the user asks to create a character sheet, character turnaround, character reference, character lineup, character concept sheet, character model sheet, or any multi-view character reference image — even if they don't use the exact phrase "character sheet". Also trigger when the user says things like "design a character with these features and make a sheet", "generate a turnaround for...", "I need a character reference image of...", or describes a creature/person/monster and wants a sheet-style visual reference. Do NOT trigger for single-pose illustrations, single portraits, or scene compositions — only multi-view reference sheets.
---

# Character Sheet Designer

A strict workflow for designing one fully-specified character and producing the exact image-generation brief required for a 4-section character sheet at 16:9 aspect ratio.

## Workflow

This skill has 4 sequential steps. Do not skip, reorder, or merge them. Each step has explicit rules — follow them literally.

### Step 1 — Ask the user (verbatim)

The very first response when this skill triggers must be **exactly** this Korean sentence, with nothing before or after it:

```
캐릭터의 특징들을 나열하고, 캐릭터 시트의 art style을 입력해주세요.
```

Do not add greetings, explanations, examples, or follow-up questions. Do not translate. Do not paraphrase. Then stop and wait for the user's reply.

**Exception:** If the user's very first message already contains a list of character traits (and optionally an art style), you may skip the prompt and go directly to Step 2. Use judgment — a vague "make me a dragon character sheet" does NOT count as sufficient traits; ask Step 1's question. A message like "elderly female elf wizard, silver hair, scarred left eye, wears tattered indigo robes, holds a crooked staff, melancholic mood, art style: oil painting" DOES count.

### Step 2 — Design the character

Take the user's traits and build a single, fully-specified character. Rules:

- **Reflect every user-specified trait exactly.** Never silently drop, soften, or re-interpret a trait. If a trait conflicts with another (e.g. "tiny giant"), pick the most charitable reading and note the interpretation in one short line.
- **Fill in unspecified elements** (silhouette details, color palette, materials, textures, mood, props, scale, age cues, etc.) so the final character is internally consistent and visually distinctive. Choose details that harmonize with the user's specified traits — don't invent contradictions.
- **One character only.** Not variations, not a family, not "options A/B/C". A single, finished concept.
- **Match anatomy to type.** Humanoid, quadruped, avian, aquatic, mixed/chimeric, mechanical, abstract — pick the structure that fits the concept and stay consistent across all four sections.

Output the design as a compact spec block before moving to Step 3. Use this exact structure:

```
## Character Design

- **Name / Concept:** <short label>
- **Type:** <humanoid | quadruped | avian | aquatic | chimeric | monstrous | mechanical | other>
- **Silhouette:** <overall shape, scale, posture tendency>
- **Head / Face:** <features, expression default>
- **Body:** <build, anatomy, key structural features>
- **Surface:** <skin / fur / scales / armor / cloth — color, texture, material>
- **Palette:** <3–5 colors with brief role: primary / secondary / accent>
- **Props / Equipment:** <items worn or carried, or "none">
- **Mood / Aura:** <one-line tonal description>
- **User-specified traits honored:** <bullet list quoting the user's exact trait keywords>
- **Inferred details (filled in):** <bullet list of additions you made>
```

### Step 3 — Determine art style

- If the user specified an art style → use it **verbatim**. Don't normalize or "improve" it.
- If the user did not specify one → default to `hyper-realistic photo`.

State the chosen style on one line:

```
**Art style:** <style as a single phrase>
```

### Step 4 — Produce the image-generation brief

Output a single, copy-pasteable English brief that an image generator (GPT Image 2, Midjourney, Sora, Imagen, etc.) can consume directly. Read `references/layout-spec.md` for the full layout sub-rules before writing the brief — those rules (camera angles, viewer-left vs. character-left, anti-mirroring, close-up framing) must be reproduced faithfully in the brief.

**At the end of Step 4, output exactly this line on its own to mark where image generation happens:**

```
[여기서 GPT Image 2 호출 — 위 프롬프트를 사용해 이미지를 생성하세요]
```

Do not attempt to call any image-generation tool yourself. Do not produce SVG mockups or placeholder visuals. The marker line is the deliverable hand-off.

## Output structure for Step 2–4 (single response)

After the user replies to Step 1, your **single next response** must contain all three remaining steps in this exact order:

1. `## Character Design` block (Step 2)
2. `**Art style:**` line (Step 3)
3. `## Image Generation Brief` block containing the English brief (Step 4)
4. The `[여기서 GPT Image 2 호출 …]` marker line

No preamble, no closing remarks, no "Let me know if…" lines.

## The image generation brief — required content

The brief in Step 4 is the actual product of this skill. It must be in **English** (image models perform better in English) and must include, in order:

1. **One-line subject summary** — who/what the character is, anchored to the design spec.
2. **Style directive** — the chosen art style, applied globally.
3. **Global rendering conditions** — verbatim: 16:9 aspect ratio, clean white background with natural lighting, neutral overall lighting, no text or watermarks.
4. **Pose rule** — A-pose for humanoids (arms 30–45° from body), standing frontal for quadrupeds, most natural neutral standing pose for other body plans. Explicitly forbid action poses or exaggerated gestures.
5. **Viewer-perspective disambiguation** — verbatim warning: "All left/right references below are from the SUBJECT's point of view. Subject's right side = viewer's left side of frame. Subject's left side = viewer's right side of frame."
6. **Section layout** — the image is divided horizontally into 4 equal-width sections. Describe each section per `references/layout-spec.md`.
7. **Consistency constraint** — verbatim: "The same individual must be recognizable across all sections. Maintain identical proportions, markings, color palette, and identifying details. Do NOT generate any section by mirroring another — each view must show genuinely different geometry, silhouette, surface flow, and shadow direction."
8. **Style reinforcement** — restate the chosen art style on the final line.

Keep the brief tight and declarative. Avoid hedging language ("perhaps", "could be"). Use imperative sentences the image model can act on.

## Common failure modes to avoid

- **Skipping Step 1.** The user must be asked unless their first message already contains substantive traits. Don't assume.
- **Dropping user traits.** If the user said "three eyes", the brief must say "three eyes" — not "multiple eyes" or "unusual eyes".
- **Over-designing.** Inferred details should support the user's traits, not overshadow them. If the user gave 10 specific traits, you should add 3–5 supporting details, not 30.
- **Action posing.** Sheets are reference material. Neutral poses only.
- **Mirroring.** The 4 main sections plus the 3 face close-ups are 7 structurally distinct views. Make this explicit in the brief.
- **Producing an actual image.** This skill does not generate images. It produces the brief and the hand-off marker.
- **Style drift.** If the user said "watercolor", every section is watercolor. Don't mix styles across sections.

## Reference

- `references/layout-spec.md` — Detailed per-section camera, framing, and emphasis rules. Read this before writing the brief in Step 4.
