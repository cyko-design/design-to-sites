# Sites rules

Checked against official Figma documentation on 21 October 2026. Figma-native Skills accept one Markdown file, not bundled references. The operational rules below are also embedded in the root SKILL.md so installation does not depend on loading this file.

## Figma Sites behaviour

### Breakpoint model

Use the destination's configured breakpoints when supplied. Otherwise use Figma Sites' current Desktop, Tablet and Mobile presets, checking the live preset values before conversion. The official preset illustration shows Desktop 1280, Tablet 800 and Mobile 375; these are editable presets, not mandatory universal widths. Do not mistake the documentation's illustrative Mobile 340 example for a preset. If current values cannot be established, ask rather than inventing widths. A Design frame width is a preparation width, not a configured Sites breakpoint. [Figma: breakpoints](https://help.figma.com/hc/en-us/articles/31242797809815-Add-or-delete-breakpoints-in-a-webpage).

### Primary, secondary and overrides

Desktop is initially primary, but Tablet or Mobile can be made primary. Primary edits cascade to properties not overridden in secondary breakpoints. Secondary edits stay local. Sites shares hierarchy across breakpoints: a secondary breakpoint cannot reparent, group or frame layers. Make structural changes on the primary; use property overrides, visibility or appropriate component variants for adaptations. Hiding at one size must not remove access to content or functions. [Figma: editing across breakpoints](https://help.figma.com/hc/en-us/articles/31242788601879-Add-select-and-edit-objects-across-multiple-breakpoints).

### Transfer

Author the converted layouts separately in Figma Design. The user copies the prepared base into a Sites primary breakpoint and applies the prepared adaptations there. Three independent Design frames do not automatically become one webpage's connected breakpoints. Do not claim transfer, interactions or breakpoint configuration succeeded without inspecting those actual Sites properties. [Figma: Design to Sites](https://help.figma.com/hc/en-us/articles/35895740494231-Figma-Sites-collection-Move-designs-from-Figma-Design-to-Figma-Sites).

## Conversion guidance from the project workflow

These are responsive preparation practices, not a claim that Sites mandates one layer tree or sizing mode for every design.

- Classify Auto Layout as fully implemented, partially implemented, missing, or mixed with absolute/manual positioning. Infer relationships from visual grouping, positions, spacing, alignment, dimensions, hierarchy, repetition and components. Reconstruct them on a separate copy, including when Auto Layout is absent. Do not blindly wrap every layer.
- Prefer a vertical page flow with nested section frames and content containers. Preserve meaningful reading order, section hierarchy and intended alignment. Use frame padding and gaps rather than stacks of spacer objects unless intentional.
- Fill: use for fluid sections, content columns and wrapping text within an Auto Layout parent. Hug: use for content-driven height, labels and compact controls. Fixed: retain intentional media, icon and control dimensions and each preparation frame's reference width.
- Apply min/max dimensions where content needs a bound, without introducing minimums that force overflow on Mobile. Avoid a Hug parent depending on a Fill child to determine the same axis. Avoid fixed text heights that clip when text wraps.
- Nest rows and stacks to express actual content relationships. Use wrapping where item order and hierarchy remain meaningful. Keep absolute positioning for intentional overlays or decoration; content should otherwise participate in responsive flow.

Figma recommends Auto Layout, section frames that fill their parent width, and min/max widths for responsive Sites content. [Figma: responsive webpage tips](https://help.figma.com/hc/en-us/articles/33257143505175-Tips-for-creating-a-responsive-webpage-in-Figma-Sites).

### Grids, imagery and components

- Distinguish Auto Layout grid from layout guides: guides do not create responsive flow. Grid has explicit tracks and spans; reducing viewport width does not imply horizontal wrapping automatically. Adapt columns and spans deliberately, or use a wrapping row when that represents the source pattern. [Figma: Auto Layout grid](https://help.figma.com/hc/en-us/articles/31289469907863-Use-the-grid-auto-layout-flow).
- Preserve image content, aspect ratio, focal point and intentional crop. Reassess crops per form factor without replacing assets or obscuring meaningful content. Keep text editable rather than flattening it into imagery.
- Reuse components, variants, styles and variables where appropriate. Keep changes local to the converted version. Editing a shared master or variable can change the original through its instances; do not do so. If isolation requires a structural decision that cannot preserve the source and component intent, ask the user.

### Adapt all three form factors

| Source | Required missing layouts | Adaptation approach |
| --- | --- | --- |
| Desktop | Tablet and Mobile | Reduce columns and reflow content; preserve priority and reading order; adapt navigation where needed. |
| Tablet | Desktop and Mobile | Derive a wider composition and a narrower flow from the same content groups and design language. |
| Mobile | Tablet and Desktop | Expand containers and infer justified multi-column relationships; do not stretch the Mobile layout or invent content to fill space. |

Preserve visual language, content, hierarchy, typography, colours, appropriate components and overall intent. Never use uniform scaling as responsive adaptation. Preserve supplied layouts where they exist and derive missing ones; do not require the user to design every breakpoint. Ask only about consequential decisions that cannot reasonably be inferred, such as an ambiguous reading order or substantially different wide-screen composition.

Desktop navigation may become a hamburger pattern on Mobile when appropriate. Preserve all destinations and functions, and prepare the control and open/closed layout states. Do not invent a new information architecture. Flag interaction wiring and touch/keyboard behaviour for Sites testing. Hover-only presentation must have an appropriate non-hover path; ask if this needs a new UX decision.

Validate all prepared sizes plus intermediate widths, including the narrower end of the Mobile range. Check overflow, clipping, reflow, order, imagery and navigation. Fix conversion regressions without using them as permission for unapproved accessibility or visual changes.

## Asset names and alt-text preparation

On converted layers only, use semantic URL-safe names: lowercase letters/digits with hyphens, no spaces, unnecessary punctuation or unsafe special characters. Examples: `Hero Image` becomes `hero-image`; `Product Screenshot 01` becomes `product-screenshot-01`. Prefer meaningful distinctions to generic numbering. If image content is uncertain, retain a meaningful contextual name or ask; do not invent a subject. Resolve collisions with a semantic qualifier where possible. Layer naming does not guarantee the exported URL or filename.

Keep a handoff mapping of layer, asset name, human-readable alt text or decorative status. For example: asset `sunset-landscape`; alt text “Sunset over a mountain landscape”. Describe the image's contextual purpose; never merely turn a slug into a sentence. Identify decorative imagery as decorative, and flag uncertain or complex descriptions for review.

**Before publishing, the user must check and apply required alt text or decorative status in Figma Sites.** Draft descriptions and layer names are not Sites accessibility properties. Do not claim they were applied unless the actual property is accessible, written and verified. [Figma: Sites accessibility properties](https://help.figma.com/hc/en-us/articles/31242789265431-Improve-the-accessibility-of-your-site).
