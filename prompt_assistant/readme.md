# Prompt Assistant

**Date:** 2026-05-25  
**Artifact type:** Single-file HTML prototype + archival slide deck  

## Purpose

The tool is designed to help creators write structured, paste-ready prompts for the Sora 2 web app while reducing omissions in key prompt components such as scene, subject, camera language, style, lighting, mood, action beats, dialogue, and sound.


## Structured prompt builder

The interface guides the user through the main prompt ingredients:

1. Scene
2. Subject details
3. Cinematography
4. Style + palette
5. Lighting
6. Mood + pace
7. Action beats
8. Dialogue
9. Background sound
10. Constraints / avoid

Optional sections can be toggled on or off, allowing the user to keep prompts compact or detailed depending on the creative task.

## Suggestions

Several fields include a **suggestion** button to quickly fill a field with a plausible starting point. These suggestions are intended as scaffolding, not final creative direction.

## Editable generated prompt

The generated prompt appears in a fixed top editor on the right side of the interface. It is intentionally editable so the user can refine the output before copying or saving it.

## Prompt versioning

The right side includes a version history:

- The newest generated prompt stays fixed at the top.
- Previously generated or saved prompts appear below as numbered versions.
- Each saved version can be loaded, copied, or deleted.
- The full history can be downloaded as a `.txt` file.

## CSV export

The **Export CSV** action saves the current form settings and the current prompt text. This is useful for archival, handoff, research notes, or comparing prompt iterations.

## Image palette extraction

The Style section includes an image palette extractor:

- Select a local image, or load an image from a URL.
- Click **Extract 5 colors**.
- The tool lists five dominant colors with hex codes and preview swatches.
- Click a swatch to append that color to the Style palette field.
- Click **Use all in Style** to add the full extracted palette.

Local images work reliably. URL-based extraction can fail if the remote site blocks browser canvas access through CORS restrictions.

## Language and theme controls

The interface includes:

- **EN / FR** toggle for bilingual workflow.
- **Dark / Light** theme toggle.
- Keyboard shortcuts:
  - `Ctrl + Enter`: generate prompt
  - `Ctrl + Shift + C`: copy prompt
  - `Ctrl + Shift + E`: export CSV

## Technical notes

- The prototype is a **single HTML file** containing HTML, CSS, and JavaScript.
- There are **no external dependencies**.
- Data is processed client-side in the browser.
- Theme, language, and prompt versions are stored in `localStorage`.
- The image palette extractor uses browser canvas analysis on a downsampled image.
- The tool does not send user content to any server.

## Known limitations

- URL image extraction may fail because of CORS restrictions. The recommended workaround is to download the image and use the local image selector.
- Language switching updates the interface and future prompt generation; it does not automatically translate an already generated prompt.
- The dominant-color extraction is designed for practical creative use, not scientific color quantization.
- Version history is stored in the browser. Clearing site data or using another browser/device will not preserve versions unless exported.

## Customization notes

To customize the tool, open `sora_prompt_builder.html` in a text editor and search for these JavaScript objects:

- `options`: dropdown values for shot type, camera movement, lens, style, lighting, mood, and pace.
- `suggestions`: random field suggestions in English and French.
- `i18n`: user-interface labels and prompt labels for EN/FR.

Suggested future extensions:

- Import/export full session as JSON.
- Add a prompt quality checklist.
- Add a “compress prompt” mode for short prompt variants.
- Add visual thumbnails for saved prompt versions.
- Add a team-specific style vocabulary or Creative Lab preset library.

