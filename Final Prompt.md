# Systematic Image Generation Workflow

## 📋 The Golden Rule: One Product, Three Containers
To ensure absolute consistency in product color, texture, and visual identity, we process one product at a time across all three formats before moving to the next.

### 🛡️ Consistency Checklist
- **Color**: Use the exact `[HEX_CODE]` from `glassmanifest.json`.
- **Texture**: Use the exact `[TEXTURE]` description from `glassmanifest.json`.
- **Labels**:
  - **PET / Glass**: Paged from `Labels for Pet Jar and Glass/`
  - **Standup Pouch**: Paged from `Labels for a Standup pouch/`

### 🔄 Execution Steps
1. **Selection**: Pick next product from `glassmanifest.json`.
2. **PET Generation**: Generate Squat PET Jar image.
3. **Glass Generation**: Generate Premium Glass Jar image.
4. **Pouch Generation**: Generate Standup Pouch image.
5. **Verification**: Confirm all three match in color and texture.

---

# Final Prompt Templates

All three container type prompts for product image generation.

---

## Variables Reference

| Variable | Description |
|----------|-------------|
| `[TEXTURE]` | e.g., "fine powder", "coarse granular powder", "fibrus powder with specks" |
| `[HEX_CODE]` | The product color, e.g., `#993300` |
| `[LABEL_IMAGE_REFERENCE]` | The label filename, e.g., `Avisaginjala Kaaram.png` |

---

## 1. PET Jar (Stubby/Squat) — Blue Lid

```text
PROPORTIONS & LABEL COVERAGE (CRITICAL):
- JAR RATIO: The jar is "squat and wide" (approx 1:1 aspect ratio), not a tall narrow tube.
- LABEL HEIGHT: The label is a "Central Band." It does NOT cover the whole jar height.
- GAPS: There is a significant strip of clear plastic visible ABOVE the label (showing the powder) and a strip of clear plastic visible BELOW the label.
- WRAP: The label wraps 360 degrees, disappearing around the curve.

Product photography of a single STANDARD CLEAR PET JAR with a blue lid.

GEOMETRY & FORM (CYLINDRICAL):
- The object is a standard cylindrical plastic food jar.
- WALLS: The sides are perfectly vertical and round (Cylinder). 
- MATERIAL: High-clarity PET Plastic (Not glass). The walls are thin and transparent with realistic plastic refraction.
- LID: A glossy COBALT BLUE screw-top lid. The side of the lid has a distinct vertical "ribbed" grip texture. The top of the lid is smooth.

CONTENTS:
- The jar contains [TEXTURE] matching hex color [HEX_CODE].
- FILL PHYSICS: The powder is visible through the clear plastic.
- HEADSPACE: The fill level is approximately 85%, leaving a visible air gap between the powder and the blue lid.

LABEL MAPPING (CURVED WRAP):
- The provided image [LABEL_IMAGE_REFERENCE] is applied as a physical paper label.
- WRAPPING PHYSICS: The label wraps naturally around the CURVE of the cylinder.
- VISIBILITY: The "Teepi Gurtu" logo and "Telugu Delicacies" branding are centered on the front curve.
- FORESHORTENING: The text on the far left and right edges (Ingredients/Nutrition) curves away from the camera and becomes foreshortened/compressed by the perspective.
- TEXTURE: Semi-gloss paper label finish.

LIGHTING & SCENE:
- Background: Clean white or light grey gradient to match a catalog style.
- LIGHT SHAPING: A tall, vertical softbox highlight runs down the entire length of the left side of the cylinder (defining the round shape).
- REFLECTIONS: Plastic-like gloss on the jar shoulder and the blue lid.
```

---

## 2. Glass Jar — Square Premium with Gold Lid

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

GEOMETRY & FORM (STRICT - ORTHOGRAPHIC):
- The object is a PERFECT SQUARE FRONT FACE of a glass brick.
- PROPORTIONS: The main glass body (excluding the neck and lid) must be EXACTLY as tall as it is wide (1:1 aspect ratio). It looks like a perfect cube from the front.
- CAMERA ANGLE: 100% DEAD-CENTER FRONT VIEW.
- SIDE VISIBILITY: 0.0% of the side panels, top glass thickness, or bottom glass thickness should be visible.
- PERSPECTIVE: Zero perspective distortion. The silhouette of the glass body is a perfect square with razor-sharp 90-degree corners.
- MATERIAL: Thick clear glass. Only the front face is visible.

LID & NECK (MATCH REFERENCE - CRITICAL):
- LID: A premium, polished warm gold metal twist-off lid. 
- LID SHAPE: The lid has a flat top and a smooth, slightly rounded vertical skirt that overlaps the glass neck.
- NECK: There is a visible, short recessed cylindrical glass neck between the lid and the square shoulder of the jar.
- SHOULDER: The glass shoulder transitions from the cylindrical neck to the sharp square corners of the main body with a subtle, tight curve.
- PROPORTIONS: The lid height is approximately 1/12th of the total container height. The visible neck is approximately 1/15th of the total height.

CONTENTS:
- The jar contains [TEXTURE] matching hex color [HEX_CODE].
- FILL PHYSICS: The powder settles naturally, stopping at the shoulder line.
- HEADSPACE: A distinct, clean air gap is visible between the texture and the gold lid.

LABEL MAPPING (SOURCE FIDELITY - CRITICAL):
- The provided image [LABEL_IMAGE_REFERENCE] is applied as a physical matte paper label.
- VERTICAL PLACEMENT: The label must be PERFECTLY CENTERED vertically on the front face of the jar.
- LABEL HEIGHT: Ensure the ENTIRE vertical content of the label (from top to bottom inclusive) is visible on the front face. Do not crop the bottom part or the "Telugu Delicacies" branding.
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
- Bottom part of label (Telugu Delicacies) is cropped or missing
- Container looks like a jar instead of a glass brick
```

---

## 3. Standup Pouch — Flexible Film Doy-Pack

```text
Product photography of a single STANDUP POUCH (doy-pack style).

STRUCTURE & FORM (CRITICAL):
- VIEW: 100% DEAD-CENTER FRONT VIEW. NO rotation.
- The object is a FLEXIBLE STANDUP POUCH (Doy-pack).
- TRANSPARENCY: The pouch body is made of CRYSTAL CLEAR, 100% TRANSPARENT plastic film.
- SHAPE: Wide, stable gusseted bottom that allows it to stand upright (visible as base support).
- SIDES: Vertical heat-sealed fins (8mm) made of clear plastic.
- TOP: Horizontal heat-seal with a clear plastic zipper visible.
- MATERIAL: High-clarity transparent film. NOT metallic, NOT opaque, NOT matte.
- PRODUCT VISIBILITY: The [TEXTURE] is fully visible through the clear film surrounding the label.

FILL STATE:
- The pouch appears FILLED with product, giving it a naturally plump, rounded shape.
- The product inside is [TEXTURE] matching hex color [HEX_CODE].
- VOLUME: The pouch looks approximately 80% full, with a gentle dome at the top below the zipper.

LABEL/PRINT MAPPING (STICKER - CRITICAL):
- TYPE: The provided image [LABEL_IMAGE_REFERENCE] is applied as a LARGE OPAQUE WHITE MATTE STICKER.
- OPACITY: The label area is NOT transparent. It is a solid white paper sticker.
- PLACEMENT: Centered on the front face.
- CONVEX CURVE: Because the pouch is filled, the sticker follows the natural convex "bulge" of the transparent film.
- VISIBILITY: All text on the sticker must be sharp and legible.

LIGHTING & SCENE:
- Background: Clean white or light grey gradient for catalog/e-commerce style.
- Lighting: Professional softbox from top-left, creating a soft highlight along the top edge and left shoulder of the pouch.
- REFLECTIONS: Subtle highlights on the clear plastic edges define the shape.
- ANGLE: 100% FRONT-FACING.

AUTO-FAIL CONDITIONS (Regenerate if any occur):
- Pouch is angled/rotated (must be 100% front-on)
- Label is transparent (must be an opaque white sticker)
- Pouch looks flat/empty
- Bottom gusset is not visible or pouch cannot stand
```
