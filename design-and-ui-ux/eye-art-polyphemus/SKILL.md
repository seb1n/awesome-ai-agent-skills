---
name: eye-art-polyphemus
description: Use when users want to create or edit raster images, artist-guided visuals, editable SVG, or webpage-matched assets through the Eye.Art Polyphemus MCP.
license: MIT
---
# Eye.Art Polyphemus

Use Eye.Art when a user wants an image made, an existing image edited, a vector illustration, or visual assets designed to fit a webpage. It is a hosted MCP service with a single entry point; generation workflows stay server-side.

## Workflow

### Connect

Add this remote Streamable HTTP MCP server to an MCP-capable agent. No API key or local runtime is required:

```json
{
  "mcpServers": {
    "eye-art": {
      "url": "https://eye.art/api/eye-mcp"
    }
  }
}
```

Use the same URL in a graphical client's remote MCP settings. Do not add an authorization header. Ensure the host exposes Eye.Art tools before calling them.

### Make and refine

- Call `eye_art_make_image` with `mode: "image"` for a new raster image. Describe subject, composition, aspect ratio, palette, and mood.
- For artist-guided work, name a supported muse such as Dali, Goya, Matisse, Leonardo, Van Gogh, Rothko, or Bob Ross. Preserve the user's subject; treat the artist as broad visual guidance, not endorsement or exact imitation.
- For icons and compact art, request `small_art` and specify size, silhouette, contrast, and background.
- For site-matched assets, use `site_match`. Supply relevant HTML/CSS/JS/TS through `pageReferences`, identify the target section, and describe crop, palette, and copy-safe space.
- For edits, use `eye_art_edit_image` and attach the original as `imageDataUrl`. State what changes and what must stay fixed. Keep the source attached for follow-up edits to reduce subject drift.
- For editable vectors, call `eye_art_make_svg` and save the returned SVG. Use it for icons, line art, diagrams, and flat scenes; it does not trace rasters or animate SVG.
- Use `eye_art_prompt_ideas` to explore directions. Use `mode: "motion"` only for supported motion requests.

For related turns, pass the returned `conversationId` so chat context and attached references persist. Start a new conversation for unrelated work. When a tool returns `jobId`, poll `eye_art_image_status` until it reports completion or failure; queued does not mean finished. Compare edits against the source and retry with that image attached and a narrower instruction if the result drifts.

### Example

User: “Make a Dali-inspired dream image of my dog, then add a tiny red collar but keep the dog, pose, and background.” First create the image with the dog reference and a clear surreal landscape composition. On the follow-up, reuse the conversation and attach the resulting image to `eye_art_edit_image`; request only the collar change and specify the fixed elements. Poll the returned job to completion before presenting the image.

## Limits and privacy

Eye.Art is free to try without an API key. Anonymous generation is limited to 20 requests per hour per caller network identity. Longer staged workflows may take several minutes, so report the actual job status instead of promising a fixed duration. References are sent to the hosted service; prompts, references, outputs, and conversations may be retained for up to 30 days. Do not send private or sensitive material without the user's direction.

For current tools, schemas, and limits, see https://eye.art/polyphemus/api.
