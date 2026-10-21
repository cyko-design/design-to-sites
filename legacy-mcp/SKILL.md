---
name: figma-sites-prep
description: Prepare Figma Design frames for manual transfer into Figma Sites, preserving their visual design and content while improving Auto Layout, sizing and responsive structure. Use for Design-to-Sites preparation, not website code generation or direct Sites editing.
---

# OUTDATED

Legacy MCP-based version. No longer recommended for normal use; use the Figma-native Skill in the repository root.


# Figma Sites Prep

Author in **Figma Design**. Prepare editable layouts for the user to copy into **Figma Sites**, then finish and publish manually. The current Figma MCP does not support writing to Sites. Do not substitute another website builder or claim the Site has been edited, tested or published.

## Establish scope before restructuring

- Identify the source frame, destination and intended viewport sizes from the request and file. Ask for a missing frame link or ambiguous destination before making changes.
- Establish whether the Design also serves Codex, code generation or another Design-to-Implementation workflow. If unclear, ask before structural edits; inspection can continue.
- **When the same Design may serve both workflows, explicitly confirm the priority and edit target before restructuring.** Explain that Sites-oriented nesting, sizing and component changes may conflict with implementation-oriented structure. Offer a separate Sites preparation copy that preserves the implementation source. Ask: “Should Sites or implementation take priority, and should I use a separate Sites copy or the shared Design?” Do not treat silence as confirmation. An explicit choice already given in this conversation satisfies the safeguard. If implementation takes priority, agree a separate Sites target before proceeding.
- Honour a specified destination or in-place edit request. Otherwise create a clearly named preparation copy in the same Design file, preserving the original. Avoid altering shared component masters outside the agreed target.

## Inspect and preserve

Confirm the connected Figma MCP exposes Design inspection and native write tools, such as `use_figma`, and has edit permission. Follow the client's required Figma tool guidance before using those tools. A read-only integration is insufficient: if writing is unavailable, explain the blocker and provide a scoped preparation plan without claiming edits.

Inspect the layer tree, components, constraints, Auto Layout and sizing. Capture a baseline screenshot at the source width and note text, imagery, typography, colours, spacing, effects, crops and stacking order. Preserve visual design and content unless redesign is explicitly requested. Retain editable text, assets, styles, variables and component relationships where possible. Do not flatten the page, replace missing assets, detach instances wholesale or silently substitute fonts. Report unavailable resources that prevent faithful preparation.

## Prepare the layout

Change structure only where it improves transfer and reflow. Use nested frames rather than groups for layout containers. Keep meaningful section names and reading order; add no unnecessary wrappers.

| Element | Preferred structure and sizing |
| --- | --- |
| Page and sections | Vertical Auto Layout; a fixed reference width for the outer Design frame, Hug height; sections Fill width and Hug height. |
| Content containers | Nested Auto Layout with existing padding, gaps and alignment; Fill available width, with min/max widths where needed to preserve the design. |
| Text | Fill or bounded width for wrapping; Hug height. Use Hug width for short labels where appropriate. |
| Buttons and compact controls | Hug content plus padding; retain fixed dimensions where the design requires them. |
| Cards, columns and repeated items | Auto Layout rows with wrapping and sensible item widths/minimums; nested vertical stacks inside items. |
| Media and decorative layers | Preserve crop and aspect ratio. Use fixed sizing when intentional; reserve absolute positioning for deliberate overlays or decoration. |

Fill requires an Auto Layout parent. Avoid circular sizing, such as a Hug parent relying on a Fill child to determine the same axis. Avoid fixed text heights that clip reflow. Keep intentional fixed sizes rather than applying Fill or Hug indiscriminately.

Reuse existing components and variants. Use local components for repeated patterns when useful; scope changes to avoid unintended effects on other instances. Do not promise that Design components, prototype interactions or responsive rules transfer unchanged.

Enable wrapping only where it preserves the intended layout. For example, a card row may wrap as space narrows while each card keeps a vertical text stack. If mobile needs a different composition, document that change or prepare a separate preview when requested. Design previews do not configure Sites breakpoints or a working hamburger menu.

## Verify in Design

Compare the prepared frame against the baseline at the original width. Inspect actual sizing and nesting, then test reflow on a temporary copy at the requested desktop and mobile widths and an intermediate width. Check clipping, overflow, text wrapping, card order, spacing and image distortion. Correct regressions within scope. Report any unverified width or unresolved difference; do not claim Sites validation from Design-only checks.

## Hand off

Return the prepared frame link, a brief change summary, checks performed and remaining limitations. Give these manual steps:

1. Copy the prepared Design frame into an empty Sites breakpoint, usually the Primary breakpoint. Adjust each breakpoint and preview desktop/mobile behaviour.
2. Finish mobile hamburger navigation where needed, links, interactions and Sites-specific settings, including semantic tags and accessibility labels.
3. **Before publishing, manually add or verify image alt text in Figma Sites.** Inspect every image and media fill, including images inside components. Describe meaningful images by purpose; mark purely decorative images as decorative using Sites accessibility settings. Alt text cannot currently be reliably configured before transfer. Draft descriptions or Design layer names are not applied Sites alt text.
4. Resolve accessibility and publishing warnings, preview the Site, then publish manually.

Always include the alt-text requirement in the handoff. The output is a prepared Design and an explicit finishing checklist; it is not a guarantee of zero-touch conversion.
