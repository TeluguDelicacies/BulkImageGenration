# Product Image Generation Workflow v2

This is the improved workflow with hardened prompts based on iterative testing and refinement.

---

## 1. File Naming

Rename your label image files to match the product name. Avoid spaces or special characters; use underscores `_` or hyphens `-`.

- **Good**: `sambar_premix_label.png`, `avisaginjala_kaaram.jpg`
- **Bad**: `IMG_2024.jpg`, `label final v2.png`

---

## 2. The Input File (Manifest)

Create a JSON file (e.g., `manifest.json` for PET bottles, `glassmanifest.json` for Glass bottles) that lists the details for each product.

### JSON Format (Recommended)

```json
[
  {
    "product_name": "Sambar Premix",
    "label_file": "Sambar Premix.png",
    "bottle_type": "PET",
    "content_hex_code": "#FFD699",
    "texture": "fine powder"
  },
  {
    "product_name": "Avisaginjala Kaaram",
    "label_file": "Avisaginjala Kaaram.png",
    "bottle_type": "Glass",
    "content_hex_code": "#993300",
    "texture": "fine granular powder"
  }
]
```

---

## 3. Reference Image

> **IMPORTANT**: Before generating any Glass bottle image, always reference `Reference Image.png` in this folder to ensure correct bottle shape and viewing angle.

---

## 4. Validated Prompts (Hardened)

These are the exact internal prompts to use. Variables are marked with `[BRACKETS]`.

---

### PET Bottle Prompt

> **Variables**: `[HEX_CODE]`, `[TEXTURE]`, `[LABEL_IMAGE_REFERENCE]`

```text
A photorealistic professional product photograph of a single tall, cylindrical clear PET plastic jar (proportions roughly 1.7:1 height to width) with a bright yellow opaque plastic screw-on lid, sitting centered on a clean white surface against a solid dark blue studio background.

The jar is filled with [TEXTURE] that has an approximate color matching hex code [HEX_CODE].

Affixed centrally onto the curved front plastic surface is the exact label shown in [LABEL_IMAGE_REFERENCE].

CRITICAL INSTRUCTION: The label is a horizontal strip (50mm tall) that is significantly shorter than the jar (160mm tall). There must be substantial visible space of clear plastic and powder both above and below the label. The label sits in the vertical center of the jar.

CRITICAL WRAPPING: The label must wrap realistically around the cylinder. ONLY the central 40% of the label design (the main logo/title) should be visible on the front face. The left and right sides (nutrition facts, side text) MUST curve away and disappear from view. Do not squeeze the entire label onto the front face.

The lighting is professional studio softbox lighting from the top-left, creating a vertical specular highlight along the length of the cylindrical jar to emphasize its roundness. Eye-level view. Square aspect ratio.

A rectangular matte paper label referenced from [LABEL_IMAGE_REFERENCE] is applied to the front face.

Front Face: The label covers about 40% of the jar's circumference. It is clearly visible on the front face, but the edges curve slightly away from the camera. It does not wrap all the way around the sides.
Curvature: The left and right edges of the label follow the cylinder's curve naturally.
```

---

### Glass Bottle Prompt (HARDENED v3 — with Reference Pre-Analysis)

> **Variables**: `[HEX_CODE]`, `[TEXTURE]`, `[LABEL_IMAGE_REFERENCE]`

```text
PRE-GENERATION REFERENCE CHECK (MANDATORY):
Before generating, carefully study the provided reference image:
1. Observe the PROPORTIONS — height-to-width ratio of the glass container.
2. Observe the GEOMETRY — sharp 90° corners, flat sides, no curves.
3. Observe the LABEL PLACEMENT — how it wraps around the front and sides.
4. Observe the LID — thin, subtle gold metal cap.
5. Observe the FILL LEVEL — powder stops below the neck with visible air gap.

Now, with a fresh mind and the reference proportions internalized, proceed:

---

Product photography of a single PREMIUM SQUARE GLASS JAR.

GEOMETRY & FORM (STRICT):
- The object is a PERFECT GEOMETRIC RECTANGULAR PRISM (like a glass brick).
- 4 PERFECTLY FLAT vertical faces from bottom to top.
- Corners are EXACT 90° breaks with near-zero radius — razor sharp edges.
- NO rounding, NO facets, NO bevels, NO curves.
- NOT cylindrical, NOT hexagonal, NOT decorative.
- The camera view is a precise STRAIGHT-ON FRONT ELEVATION (Orthographic style).
- The front face appears as a perfect square with no perspective distortion.

LID:
- Thin, subtle gold metal lid.
- Lid height must be no more than 10% of total container height.
- Must not dominate the silhouette.

CONTENTS:
- The jar contains [TEXTURE] matching hex color [HEX_CODE].
- FILL PHYSICS: The powder settles naturally, stopping at the shoulder line.
- HEADSPACE: A distinct, clean air gap is visible between the texture and the gold lid.

LABEL MAPPING (SOURCE FIDELITY):
- The provided image [LABEL_IMAGE_REFERENCE] is applied as a physical matte paper label.
- WRAPPING PHYSICS: The label spans the full width of the front face. The label edges physically bend 90 degrees around the sharp corners and continue onto the side panels.
- VISIBILITY: The "Nutrition/Ingredients" sections are on the side panels, foreshortened and turning away from the camera view.
- TEXTURE: High-quality matte paper finish, not glossy.
- HEIGHT: The label must NOT stretch to cover the full jar height. Visible glass/product should be above and below the label.

LIGHTING & SCENE:
- Background: Deep matte blue (#1a2744).
- Lighting: Softbox top-left with "Rim Lighting" to define the sharp vertical glass edges.
- Reflections: Clean studio reflections on the gold metal lid.

AUTO-FAIL CONDITIONS (Regenerate if any occur):
- Any curved glass profile
- Label does not show sharp fold creases at corners
- Powder reaches lid
- Front face is not perfectly square
- Container looks like a jar instead of a glass brick
```

---

## 5. Pre-Generation Checklist

Before generating each image, confirm:

1. ✅ **Prompt Review**: Using the correct prompt (PET or Glass).
2. ✅ **Product Details**: Name, Color (Hex), Texture from manifest.
3. ✅ **Bottle Shape**: PET = Cylindrical, Glass = Square Cube (NOT faceted).
4. ✅ **Visibility**: PET = curved wrap, Glass = Single flat front face visible.
5. ✅ **Label**: Correct `.png` file. Matte paper. Text clarity. Critical wrapping applied.

---

## 6. Output Organization

Generated images should be saved to appropriately named folders:

- `Ready to Use/` - PET bottle images (Premix products)
- `Ready to Eat/` - Glass bottle images (Kaaram/Podi products)

---

## 7. Known Issues & Fixes

| Issue | Cause | Fix |
|-------|-------|-----|
| Hexagonal/faceted bottle | AI interprets "rounded corners" loosely | Add explicit negatives: "NO FACETED GLASS. NO HEXAGONAL SHAPE." |
| Side panels visible | Wrong camera angle | Specify "ORTHOGRAPHIC FRONT ANGLE" and "ABSOLUTELY NO SIDE PANELS VISIBLE" |
| Label curved across facets | Wrong bottle shape | Enforce "single, uninterrupted flat plane" |
| Wrong background color | Vague description | Use explicit hex code: "#1a2744" |
