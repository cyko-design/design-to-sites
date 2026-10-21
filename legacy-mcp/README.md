OUTDATED

This is the legacy MCP-based version of Design to Sites and is no longer recommended for normal use. Use the Figma-native Skill in the repository root instead.

Historical instructions below are retained for reference. The original ZIP is archived here and retains its original contents; it is not the Figma-native installer.

# Figma Sites Prep

Prepare Figma Design layouts for manual transfer into Figma Sites, preserving visual design and content while improving Auto Layout, Fill/Hug/fixed sizing, nesting, responsive wrapping and component reuse.

**Workflow:** Figma Design → Prepared layout → Manual copy to Figma Sites → Final adjustments → Publish

## Required before publishing: image alt text

**Manually add or verify image alt text in Figma Sites after transfer and before publishing. This workflow cannot reliably configure Sites alt text in Figma Design.**

Check every image, including media fills and component images. Describe meaningful images and mark purely decorative images as decorative in Sites accessibility settings. Suggested descriptions and Design layer names do not set Sites alt text. Resolve accessibility and publishing warnings before publishing. See [Figma's accessibility guide](https://help.figma.com/hc/en-us/articles/31242789265431-Improve-the-accessibility-of-your-site).

## Requirements

This Skill uses the portable `SKILL.md` format and should be compatible with **ChatGPT, Claude and other AI agents that support Agent Skills**, provided they can inspect and edit Figma Design through MCP. Check your chosen agent's installation instructions and supported Figma tools.

| User | AI agent |
| --- | --- |
| Access to Figma Design **and Figma Sites**, with edit permission for both files. Performs the transfer, finishing checks and publication. | Skills available; Figma MCP connected and authorised, exposing native Design write tools with edit access to the target Design file. A read-only connection is insufficient. |

The [current Figma MCP tools](https://developers.figma.com/docs/figma-mcp-server/tools-and-prompts/) do not provide Sites write access. Installing this Skill does not grant permissions or add tools. Availability depends on the account and connected client.

## Install

Download [figma-sites-prep.zip](figma-sites-prep.zip). The ZIP contains one top-level `figma-sites-prep/` folder with [SKILL.md](SKILL.md) and this README. To package a clone, run from the directory containing the repository folder:

```sh
zip figma-sites-prep.zip figma-sites-prep/SKILL.md figma-sites-prep/README.md
```

### ChatGPT

1. Open **Skills → New Skill → Upload from your computer** and upload the ZIP. The [official installation walkthrough](https://developers.openai.com/cookbook/examples/chatgpt/chatgpt_prompt_guide/chatgpt_prompt_guide) opens Skills from the profile menu; entry points may vary.
2. Connect and authorise Figma, then start a new chat.

### Claude

1. Enable **Code execution and file creation** in **Settings → Capabilities**. On Team or Enterprise, check that your organisation permits Skills and code execution.
2. Open **Customize → Skills → + → Create skill → Upload a skill**, then upload the ZIP.
3. Toggle the Skill on, connect and authorise Figma with native Design write tools, then use the prompt below.

See [Claude's official Skills installation guide](https://support.claude.com/en/articles/12512180-use-skills-in-claude) for current steps and account requirements.

### Other AI agents

Follow your chosen agent's official instructions for installing `SKILL.md` packages and connecting Figma MCP. Some agents load a local skill folder rather than a ZIP. Installing the Skill cannot enable unavailable Skills features or Design write tools.

## Use

> Use Figma Sites Prep to prepare this Figma Design frame for Sites: [Figma Design frame URL]. Preserve its visual design and content. Create a separate preparation copy. This copy is for Sites only.

Include a destination link if needed. Your AI agent prepares the layout in **Figma Design**; you [copy it into Figma Sites](https://help.figma.com/hc/en-us/articles/35895740494231-Figma-Sites-collection-Move-designs-from-Figma-Design-to-Figma-Sites) manually.

**Also using the Design with Codex or another implementation workflow?** Say so first. The Skill requires explicit confirmation of priority and edit target before restructuring, because Sites-oriented structure may conflict with implementation needs. A separate Sites copy preserves the shared source.

## After transfer

Expect adjustments to responsive breakpoints, wrapping, mobile hamburger navigation, links, interactions and Sites-specific settings. Preview desktop and mobile, complete the **required alt-text review above**, and resolve publishing warnings. The Skill minimises manual work; final Sites behaviour requires verification in Sites.

