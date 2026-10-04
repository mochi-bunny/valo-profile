# valo-profile

A single-page, Valorant-themed portfolio site. Dark sidebar nav with keyboard shortcuts, an interactive canvas background (a rotating, glowing "flower" mandala), an agent-reveal-style player card, and scroll reveals.

## Quick start

Content is data-driven: `index.html` fetches `data.json` and fills in the hero, skills, education, experience, projects, extracurriculars, and contact sections. Styling lives in `style2.css`.

```
python -m http.server 8000
```

then open `http://localhost:8000/index.html`. (Opening `index.html` directly by double-clicking uses a `file://` URL, where `fetch()` is blocked — you'll see the fallback markup baked into the HTML instead of your `data.json` content.)

## What to edit

- **Content** — almost everything (name, tagline, skills, education, experience, projects, extracurriculars, contact, links) lives in [`data.json`](data.json). Edit that file; you shouldn't need to touch the HTML for content changes.
- **Project media** — each project in `data.json` has a `media` slot shown under the title in a fixed 4:3 frame (shown whole, never cropped — leftover space is filled with a blurred copy of the image, so card size never changes). Set `"src"` to an image/GIF or a video (`.mp4`, `.webm`, `.mov` — plays muted on a loop), plus `"alt"` text; videos also accept an optional `"poster"` thumbnail. Leave `src` empty for no media — if at least one project has media, the others show a blank frame so the cards stay aligned.
- **Player card photo** — drop a headshot named `profile.jpg` next to `index.html`. Falls back to initials automatically if it's missing.
- **Sidebar nav** — number keys `0`–`5` jump to the matching section (`0` = home, `1`–`5` = the five sidebar links, in order).
- **Colors / type sizes** — the CSS custom properties at the top of [`style2.css`](style2.css) (`--accent`, `--ink`, `--bone`, `--fs-*`, etc.).
- **Background mandala** — the `NeonMandala.create('#seal', {...})` call near the end of `index.html` — every visual parameter (fold count, petal shape, rotation style, colors, glow) is exposed there.

## Other files in this repo

- `Kill_Contract.webp`, `download.gif`, `profile.jpg` — image assets used by the site.

Looking for a simpler, single-file template with no `data.json`/build step at all? See [mochi-bunny/valorant-portfolio-template](https://github.com/mochi-bunny/valorant-portfolio-template) — same visual style, everything hardcoded in one HTML file you can open and edit directly.
