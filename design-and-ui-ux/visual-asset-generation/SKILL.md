---
name: Visual Asset Generation
description: Generate production-ready visual assets — app icons, favicons, OG images, logos, and wordmarks — by routing prompts to 30+ image generation models via the prompt-to-asset MCP server. Zero API key required for first run via free tiers.
license: MIT
metadata:
  author: AI Agent Skills Community
  version: 1.0.0
---

# Visual Asset Generation

This skill enables the agent to produce production-ready visual assets for any project by writing precise prompts and calling the [prompt-to-asset](https://github.com/MohamedAbdallah-14/prompt-to-asset) MCP server. The server routes requests across 30+ image generation models and returns file-ready outputs at correct dimensions for each asset type. No API key is required for initial runs — the server uses free tiers automatically.

## Asset Type Specifications

| Asset | Dimensions | Format | Notes |
|-------|------------|--------|-------|
| App icon | 1024×1024 px | PNG | Simple shape readable at 16 px, no text |
| Favicon | 32×32 px | PNG/ICO | Single recognizable shape, high contrast |
| OG image | 1200×630 px | PNG/JPG | Text-safe zone: center 800×400 |
| Logo mark | 512×512 px | SVG/PNG | Works on light and dark backgrounds |
| Wordmark | 1200×300 px | SVG/PNG | Legible at small sizes |
| Social banner | 1500×500 px | PNG/JPG | Twitter/X header ratio |

## Workflow

1. **Read project context**: Check the README, any existing brand assets, and the project name. Infer tone, color direction, and use case from the project description.

2. **Identify asset type(s)**: Confirm which assets are needed and their target contexts (web, mobile, social, print).

3. **Draft the prompt**: Write a prompt matching the asset specification. Lead with style, specify medium, name colors explicitly, describe composition, and add a negative prompt for icons to exclude gradients, shadows, and text.

4. **Call prompt-to-asset**: Invoke the MCP server with the prompt and target dimensions. Install if not present: `npm install -g prompt-to-asset`.

5. **Review and iterate**: Inspect the output. If it misses the mark — wrong style, wrong proportions, off-brand color — adjust the prompt and call again. One or two iterations typically converges.

6. **Save to the correct path**: Place assets in `assets/`, `public/`, or `src/assets/` as appropriate for the project type. Use descriptive filenames: `icon-1024.png`, `og-image.jpg`, `favicon.ico`.

7. **Report**: Return the file path and the final prompt used so the result is reproducible.

## Usage

Provide the agent with your project name, a brief description, the asset type(s) needed, and any color or style preferences. The agent will infer missing brand details from the project context, draft a prompt, generate the asset, and save it to the right location.

Install prompt-to-asset: `npm install -g prompt-to-asset`

## Examples

### Example 1: App Icon for a CLI Tool

**User Request**: "Generate an app icon for 'unslop', a CLI that strips AI writing patterns from content."

**Agent Response**:

**Prompt drafted**:
`Flat vector app icon, surgical scalpel slicing through a speech bubble filled with wavy lines, electric red on white, minimal, bold, no gradients, no text, no shadows`

**MCP call**: `prompt-to-asset --prompt "..." --width 1024 --height 1024 --format png`

**Output saved**: `assets/icon-1024.png`

**Favicon variant prompt**: `Flat vector icon, red scalpel silhouette, high contrast on white, 32x32, single recognizable shape`

---

### Example 2: OG Image for an Open-Source Library

**User Request**: "Create an OG image for a GitHub repo called 'NovaByte' — a cloud infrastructure library for DevOps teams."

**Agent Response**:

**Prompt drafted**:
`Wide horizontal marketing image, dark navy background #0A2540, bold white text area center-left with subtle glow, abstract geometric network nodes right side, electric teal #00D4AA accent lines, 1200x630, clean tech aesthetic`

**MCP call**: `prompt-to-asset --prompt "..." --width 1200 --height 630 --format jpg`

**Output saved**: `public/og-image.jpg`

---

### Example 3: Logo Mark Variants

**User Request**: "Generate a logo mark for 'GreenLeaf Organics' — an organic food brand. Should work light and dark."

**Agent Response**:

**Light background prompt**:
`Minimal vector logo, stylized leaf silhouette inside a thin circle, forest green #2D6A4F on white, clean geometric lines, no gradients, no text, scalable`

**Dark background prompt**:
`Minimal vector logo, stylized leaf silhouette inside a thin circle, mint green #95D5B2 on transparent dark background, clean geometric lines, no gradients, no text`

Both outputs saved: `assets/logo-light.png`, `assets/logo-dark.png`

## Best Practices

- **Lead with style**: "flat vector", "minimal geometric", "photorealistic product shot" — this sets the generation model's visual register immediately.
- **Name colors with hex codes**: "electric blue #0066FF and white" produces far more consistent results than "blue".
- **Negative prompts save iterations**: For icons, always add "no gradients, no shadows, no text" to avoid common AI generation defaults that hurt readability at small sizes.
- **Test at actual render size**: A 1024 px app icon that looks good at full resolution may be illegible as a 16 px favicon. Review at the intended display size before signing off.
- **Infer brand tone from the project name**: A security tool benefits from dark, high-contrast palettes. A productivity tool benefits from clean whites and accent colors. Read the README first.

## Edge Cases

- **prompt-to-asset not installed**: Run `npm install -g prompt-to-asset` before calling the MCP server. Verify with `prompt-to-asset --version`.
- **Free tier exhausted**: The server cycles across 30+ models. If one model's free tier is exhausted for the session, the server falls back to the next available model automatically.
- **Asset needs to match existing brand exactly**: Collect the existing brand's hex color codes and typeface names before prompting. Pass them verbatim in the prompt.
- **Multiple asset types needed**: Generate assets in order from largest to smallest — icon first, then OG image, then favicon. Each iteration builds prompt vocabulary for the next.
