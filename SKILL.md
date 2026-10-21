---
name: design-to-sites
description: Convert an existing Figma Design from Desktop, Tablet or Mobile into separate responsive Sites-ready layouts, reconstructing Auto Layout where needed and preparing assets and alt text. Use when converting an existing design for Figma Sites; require explicit confirmation before automatic WCAG 2.2 AA design-level corrections.
---

# Design to Sites

Run in the Figma Agent conversation in Figma Design when the user invokes `/design-to-sites` to convert an existing design. Produce a separate converted version with Desktop, Tablet and Mobile layouts. Do not require the user to design missing breakpoints. This is conversion, not a new site design or code-generation workflow.

Read the embedded [Sites rules](#sites-rules) and [WCAG design checks](#wcag-design-checks) before working. All operational instructions are in this single file; no supporting file needs to be installed or retrieved.

## 1. Inspect without changing the source

Identify the selected or supplied source and any existing responsive layouts. If the source is ambiguous, ask the user. Inspect its visual content and layer structure, dimensions, styles, components, imagery, typography, colours, hierarchy, alignment, spacing and intended reading order. Record a visual baseline at its original size.

Classify Auto Layout as fully implemented, partially implemented, missing, or mixed with absolute/manual positioning. Infer the actual content relationships from the design rather than treating a missing Auto Layout structure as a blocker.

Determine whether the source is Desktop, Tablet or Mobile from its intended use and context, not width alone. Preserve supplied layouts and derive the missing ones:

- Desktop source: prepare Tablet and Mobile.
- Tablet source: prepare Desktop and Mobile.
- Mobile source: prepare Tablet and Desktop.

Check current Sites preset values or the supplied destination's existing breakpoint configuration, as described below. Do not invent widths when these cannot be established; ask the user for the current settings. If the native agent cannot inspect or create a required structure, stop and explain that limitation. Do not silently substitute another product, flattening, code or a different workflow.

## 2. Mandatory accessibility confirmation

Before conversion, display the following text verbatim as a message in the Figma Agent conversation, then stop and wait for the user's answer:

```text
Accessibility check

Design to Sites includes WCAG 2.2 AA design-level checks. Accessibility corrections may make minimal adjustments to colours, contrast, sizing or spacing. Changes will stay as close as possible to the original design while meeting accessibility requirements.

Continue with automatic accessibility corrections?
```

Do not apply any automatic accessibility corrections before an explicit affirmative reply. Do not infer consent from invocation, general permission to convert or silence. Use agent chat, not a custom modal. If the user declines, continue structural conversion and inspection without accessibility corrections; propose asset names and report unresolved accessibility issues instead of making accessibility-related changes.

## 3. Build the converted version separately

Create a clearly identified conversion area and separate converted frames. Source preservation is mandatory: do not destructively restructure the original, rename its assets, modify shared masters or change shared styles/variables in ways that affect it. Source edits require a separate explicit user request. Approval for conversion or accessibility corrections is not approval to change the original.

Retain visual language, content, hierarchy, typography, colour system, appropriate components and overall intent. Keep editable text and original assets. Do not substitute missing fonts or imagery, detach all instances, invent content, or flatten the page. Explain unavailable resources. Use local relationships where needed to avoid changing the source indirectly through shared dependencies.

Reconstruct Auto Layout when absent or incomplete. Adapt sections, columns, grids, wrapping, media and navigation using the embedded Sites rules. Preserve content and functions at every size. Never treat uniform scaling as responsive adaptation. Ask before a major composition, hierarchy, navigation or other UX decision that cannot reasonably be inferred.

On converted layers, apply semantic URL-safe asset naming and prepare separate natural-language alt descriptions or decorative classifications. If corrections were declined, provide proposed names rather than applying accessibility-related renaming. Do not confuse names or written proposals with actual Sites accessibility properties.

## 4. Apply approved corrections within the boundary

Only after the mandatory affirmative reply, correct clear design-level WCAG issues where a minimal adjustment can preserve intent. Use the embedded WCAG criteria and their exceptions, not invented thresholds. Keep a concise record of the issue, evidence and before/after values. Recheck other affected states and backgrounds.

The initial reply does not authorise substantial visual changes. If a correction would significantly alter the palette, brand, composition, content or interaction, explain the proposed change and obtain separate confirmation before applying it. Never use an accessibility check to redesign the work. Do not add visible annotations, audit badges or callouts to the design by default.

## 5. Validate and hand off

Compare a temporary copy of the converted base at the original source width against the baseline, accounting only for approved corrections. Confirm all Desktop, Tablet and Mobile layouts exist, including Mobile-to-Desktop adaptation. Inspect their structure and test intermediate widths for clipping, overflow, reading order, wrapping, media distortion and navigation. Fix conversion regressions within scope; obtain approval if a fix would cross the accessibility or redesign boundary. Verify the original and its shared dependencies remain unchanged.

Return converted frame links, a concise conversion and accessibility summary, unresolved decisions, unverified checks, and an asset-to-alt-text/decorative mapping in the conversation. Include manual Sites steps:

1. Transfer the prepared base into a Sites primary breakpoint, then configure the missing breakpoints and their adaptations using the prepared layouts. Separate Design frames do not automatically establish Sites breakpoint relationships.
2. Verify responsive behaviour, navigation including any hamburger menu, links, interactions and Sites-specific settings on Desktop, Tablet, Mobile and intervening sizes.
3. **Before publishing, check and apply alt text or decorative status in Figma Sites where required.** Prepared descriptions and layer names do not apply those properties. Claim application only if the actual Sites accessibility property was accessible, written and verified.
4. Test the functioning Site for keyboard navigation, screen-reader behaviour, actual focus order, runtime semantics and other checks listed below. Resolve accessibility and publishing warnings before the user publishes.

State that these are design-level checks and do not establish WCAG 2.2 AA conformance of the final website. Do not claim Sites configuration or runtime testing was completed without direct verification.

## Sites rules

<!-- BEGIN embedded Sites rules -->

### Figma Sites behaviour

#### Breakpoint model

Use the destination's configured breakpoints when supplied. Otherwise use Figma Sites' current Desktop, Tablet and Mobile presets, checking the live preset values before conversion. The official preset illustration shows Desktop 1280, Tablet 800 and Mobile 375; these are editable presets, not mandatory universal widths. Do not mistake the documentation's illustrative Mobile 340 example for a preset. If current values cannot be established, ask rather than inventing widths. A Design frame width is a preparation width, not a configured Sites breakpoint. [Figma: breakpoints](https://help.figma.com/hc/en-us/articles/31242797809815-Add-or-delete-breakpoints-in-a-webpage).

#### Primary, secondary and overrides

Desktop is initially primary, but Tablet or Mobile can be made primary. Primary edits cascade to properties not overridden in secondary breakpoints. Secondary edits stay local. Sites shares hierarchy across breakpoints: a secondary breakpoint cannot reparent, group or frame layers. Make structural changes on the primary; use property overrides, visibility or appropriate component variants for adaptations. Hiding at one size must not remove access to content or functions. [Figma: editing across breakpoints](https://help.figma.com/hc/en-us/articles/31242788601879-Add-select-and-edit-objects-across-multiple-breakpoints).

#### Transfer

Author the converted layouts separately in Figma Design. The user copies the prepared base into a Sites primary breakpoint and applies the prepared adaptations there. Three independent Design frames do not automatically become one webpage's connected breakpoints. Do not claim transfer, interactions or breakpoint configuration succeeded without inspecting those actual Sites properties. [Figma: Design to Sites](https://help.figma.com/hc/en-us/articles/35895740494231-Figma-Sites-collection-Move-designs-from-Figma-Design-to-Figma-Sites).

### Conversion guidance from the project workflow

These are responsive preparation practices, not a claim that Sites mandates one layer tree or sizing mode for every design.

- Classify Auto Layout as fully implemented, partially implemented, missing, or mixed with absolute/manual positioning. Infer relationships from visual grouping, positions, spacing, alignment, dimensions, hierarchy, repetition and components. Reconstruct them on a separate copy, including when Auto Layout is absent. Do not blindly wrap every layer.
- Prefer a vertical page flow with nested section frames and content containers. Preserve meaningful reading order, section hierarchy and intended alignment. Use frame padding and gaps rather than stacks of spacer objects unless intentional.
- Fill: use for fluid sections, content columns and wrapping text within an Auto Layout parent. Hug: use for content-driven height, labels and compact controls. Fixed: retain intentional media, icon and control dimensions and each preparation frame's reference width.
- Apply min/max dimensions where content needs a bound, without introducing minimums that force overflow on Mobile. Avoid a Hug parent depending on a Fill child to determine the same axis. Avoid fixed text heights that clip when text wraps.
- Nest rows and stacks to express actual content relationships. Use wrapping where item order and hierarchy remain meaningful. Keep absolute positioning for intentional overlays or decoration; content should otherwise participate in responsive flow.

Figma recommends Auto Layout, section frames that fill their parent width, and min/max widths for responsive Sites content. [Figma: responsive webpage tips](https://help.figma.com/hc/en-us/articles/33257143505175-Tips-for-creating-a-responsive-webpage-in-Figma-Sites).

#### Grids, imagery and components

- Distinguish Auto Layout grid from layout guides: guides do not create responsive flow. Grid has explicit tracks and spans; reducing viewport width does not imply horizontal wrapping automatically. Adapt columns and spans deliberately, or use a wrapping row when that represents the source pattern. [Figma: Auto Layout grid](https://help.figma.com/hc/en-us/articles/31289469907863-Use-the-grid-auto-layout-flow).
- Preserve image content, aspect ratio, focal point and intentional crop. Reassess crops per form factor without replacing assets or obscuring meaningful content. Keep text editable rather than flattening it into imagery.
- Reuse components, variants, styles and variables where appropriate. Keep changes local to the converted version. Editing a shared master or variable can change the original through its instances; do not do so. If isolation requires a structural decision that cannot preserve the source and component intent, ask the user.

#### Adapt all three form factors

| Source | Required missing layouts | Adaptation approach |
| --- | --- | --- |
| Desktop | Tablet and Mobile | Reduce columns and reflow content; preserve priority and reading order; adapt navigation where needed. |
| Tablet | Desktop and Mobile | Derive a wider composition and a narrower flow from the same content groups and design language. |
| Mobile | Tablet and Desktop | Expand containers and infer justified multi-column relationships; do not stretch the Mobile layout or invent content to fill space. |

Preserve visual language, content, hierarchy, typography, colours, appropriate components and overall intent. Never use uniform scaling as responsive adaptation. Preserve supplied layouts where they exist and derive missing ones; do not require the user to design every breakpoint. Ask only about consequential decisions that cannot reasonably be inferred, such as an ambiguous reading order or substantially different wide-screen composition.

Desktop navigation may become a hamburger pattern on Mobile when appropriate. Preserve all destinations and functions, and prepare the control and open/closed layout states. Do not invent a new information architecture. Flag interaction wiring and touch/keyboard behaviour for Sites testing. Hover-only presentation must have an appropriate non-hover path; ask if this needs a new UX decision.

Validate all prepared sizes plus intermediate widths, including the narrower end of the Mobile range. Check overflow, clipping, reflow, order, imagery and navigation. Fix conversion regressions without using them as permission for unapproved accessibility or visual changes.

### Asset names and alt-text preparation

On converted layers only, use semantic URL-safe names: lowercase letters/digits with hyphens, no spaces, unnecessary punctuation or unsafe special characters. Examples: `Hero Image` becomes `hero-image`; `Product Screenshot 01` becomes `product-screenshot-01`. Prefer meaningful distinctions to generic numbering. If image content is uncertain, retain a meaningful contextual name or ask; do not invent a subject. Resolve collisions with a semantic qualifier where possible. Layer naming does not guarantee the exported URL or filename.

Keep a handoff mapping of layer, asset name, human-readable alt text or decorative status. For example: asset `sunset-landscape`; alt text “Sunset over a mountain landscape”. Describe the image's contextual purpose; never merely turn a slug into a sentence. Identify decorative imagery as decorative, and flag uncertain or complex descriptions for review.

**Before publishing, the user must check and apply required alt text or decorative status in Figma Sites.** Draft descriptions and layer names are not Sites accessibility properties. Do not claim they were applied unless the actual property is accessible, written and verified. [Figma: Sites accessibility properties](https://help.figma.com/hc/en-us/articles/31242789265431-Improve-the-accessibility-of-your-site).

<!-- END embedded Sites rules -->

## WCAG design checks

Use the normative [WCAG 2.2 Recommendation](https://www.w3.org/TR/WCAG22/) and the W3C Understanding documents linked below. AA includes applicable A criteria.

<!-- BEGIN embedded WCAG design checks -->

### What the design can show

Use actual colour, opacity, typography and geometry values when available. Record evidence and uncertainty. A screenshot, a layer name or a visually plausible result is not proof of runtime accessibility. Relate Design units to intended CSS pixels before evaluating dimensions; flag an unknown mapping.

| Criterion | Design-level check and limit |
| --- | --- |
| [1.4.3 Contrast (Minimum), AA](https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum.html) | Text normally needs at least 4.5:1; large text at least 3:1. Large means at least 18pt regular or 14pt bold at delivery, or the defined CJK equivalent. Apply the logo/incidental exceptions where justified. Use actual composited colours, not antialiased glyph pixels; do not round a failing ratio into a pass. Unknown font metrics or variable backgrounds need review. |
| [1.4.11 Non-text Contrast, AA](https://www.w3.org/WAI/WCAG22/Understanding/non-text-contrast.html) | Necessary active UI/state cues and meaningful graphic parts need at least 3:1 against adjacent colours. Respect exceptions for inactive controls, unmodified user-agent appearance and essential graphic presentation. Do not impose this on decoration or require every control to have a border. |
| [1.4.1 Use of Color, A](https://www.w3.org/WAI/WCAG22/Understanding/use-of-color.html) | Identify meaning, states or actions conveyed through hue alone. Check for an existing non-colour cue. Propose a label, shape or other cue when meaning is inaccessible; seek approval if adding it changes content or appearance substantially. |
| [2.5.8 Target Size (Minimum), AA](https://www.w3.org/WAI/WCAG22/Understanding/target-size-minimum.html) | Pointer targets need 24 by 24 CSS px, subject to spacing, equivalent control, inline, unmodified user-agent and essential exceptions. For the spacing exception, a 24 CSS px diameter circle centred on each undersized target must intersect neither another target nor another undersized target's circle. Inspect intended hit areas, not just visible icons. Runtime hit areas need verification. Do not present the AAA 44px target criterion as AA. |
| [1.3.1 Info and Relationships, A](https://www.w3.org/WAI/WCAG22/Understanding/info-and-relationships.html) and [2.4.6 Headings and Labels, AA](https://www.w3.org/WAI/WCAG22/Understanding/headings-and-labels.html) | Check represented grouping, hierarchy and descriptive labels. Preserve meaningful sequence. Prepare semantic intent; a Design layer hierarchy does not prove HTML semantics or accessible names. Do not impose a new content hierarchy without approval. |
| [1.4.10 Reflow, AA](https://www.w3.org/WAI/WCAG22/Understanding/reflow.html) | Inspect a temporary layout at 320 CSS px equivalent width for vertically scrolling content, or 256 CSS px equivalent height for horizontally scrolling content. Check loss and two-axis scrolling, respecting content requiring two-dimensional layout. These are accessibility test dimensions, not new Sites presets. Actual zoom/reflow requires runtime testing. |
| [1.4.4 Resize Text, AA](https://www.w3.org/WAI/WCAG22/Understanding/resize-text.html) | Inspect the risk of clipping or lost functions when text grows to 200%, with the criterion's captions/images-of-text exceptions. A temporary Design simulation is a preliminary check; test the functioning Site. |
| [1.4.12 Text Spacing, AA](https://www.w3.org/WAI/WCAG22/Understanding/text-spacing.html) | Where applicable, test tolerance of user overrides: line height 1.5 times font size, paragraph spacing 2 times, letter spacing 0.12 times and word spacing 0.16 times. These are override test values, not mandatory default typography. Use temporary copies; if a property cannot be simulated, flag it for runtime testing. |
| [2.4.7 Focus Visible, AA](https://www.w3.org/WAI/WCAG22/Understanding/focus-visible.html) and [2.4.11 Focus Not Obscured (Minimum), AA](https://www.w3.org/WAI/WCAG22/Understanding/focus-not-obscured-minimum.html) | Review focus states where represented and whether overlays could entirely hide the focused component. Missing representations mean unverified, not a demonstrated runtime failure. Do not impose AAA focus-appearance geometry as AA. Actual visibility and focus order require runtime checks. |
| [1.1.1 Non-text Content, A](https://www.w3.org/WAI/WCAG22/Understanding/non-text-content.html) | Prepare text alternatives by contextual purpose, identify decorative images and flag complex images needing fuller explanation. Keep descriptions separate from asset names. Applying and verifying Sites alt-text/decorative properties remains required before publishing. |

For contrast calculation use WCAG's relative luminance and contrast definitions, including compositing known opacity/backgrounds. If the agent cannot compute or measure a reliable value, report it as unverified rather than guessing. Readability review may flag clipped text and unclear hierarchy; WCAG AA does not prescribe a universal minimum body-font size or font family.

### Correction boundary

1. **Inspection:** may identify issues and prepare proposals before approval. No automatic accessibility corrections yet.
2. **Mandatory approval:** display the exact Accessibility check message in SKILL.md in the Figma Agent conversation and wait for an affirmative reply. Silence is not approval. A modal is unnecessary. Declining corrections does not prevent structural conversion, an audit or alt-text proposals.
3. **Safe corrections after approval:** fix a clear, measurable issue with the smallest change that preserves intent. Examples are a slight local colour adjustment to reach the applicable ratio, enlarging a hit area without changing the icon, or a small spacing adjustment that satisfies the target rule without reordering content. Recheck affected states and neighbouring elements. Record before/after values. Never alter shared styles, variables or masters in a way that changes the source.
4. **Separate approval required:** substantial colour/brand changes, new focus or interaction patterns, new labels/copy, changed hierarchy, overlapping enlarged targets, or any fix with uncertain consequences. Explain the issue and proposed adjustment, then wait. Initial accessibility approval does not authorise redesign. URL-safe naming is a conversion convention, not a WCAG success criterion; do not claim renaming proves accessibility.

Do not apply spacing-override test values to the default design as an automatic fix. If the user declines accessibility changes, preserve the design and report unresolved issues and proposed asset names without applying accessibility-related renaming. Do not introduce visible annotations, audit badges or callouts on the canvas by default.

### Functioning Site testing

Report these as runtime checks, not completed design checks: keyboard navigation and traps, screen-reader output, actual focus order and focus visibility, hover/menu behaviour, target hit areas, browser text resizing and spacing overrides, actual reflow/zoom, semantic HTML, accessible names, form/error behaviour where present, and Sites-specific alt text and decorative status.

At completion provide a concise summary of corrections, evidence, unresolved issues and unverified runtime checks. Passing these design checks never establishes final WCAG 2.2 AA conformance.

<!-- END embedded WCAG design checks -->
