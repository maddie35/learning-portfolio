# Learning Portfolio — Maddie Reardon

Portfolio site for Maddie Reardon, senior learning designer. Static HTML, no build step, no dependencies.

## Pages

| File | Purpose |
| --- | --- |
| `index.html` | Home, with the work index |
| `about.html` | Background, beliefs, skills |
| `writing.html` | Essays, linking to PDFs in `assets/writing/` |
| `work-monday.html` | Case study — monday.com rollout training |
| `work-cybersecurity.html` | Case study — cybersecurity awareness training |
| `work-workday.html` | Case study — tooling overhaul training |

`assets/styles.css` holds the design tokens and component classes (`.blueprint`, `.btn`, `.tag`, `.card`). It is the source of truth for the look — retune variables in `:root` rather than overriding at the page level.

## Local preview

```bash
python3 -m http.server 8000
```

Then open <http://localhost:8000>. Opening the files directly with `file://` also works, since there is no JavaScript.

## Publishing with GitHub Pages

Settings → Pages → Source: *Deploy from a branch* → `main` / `/ (root)`.

The site will be served at `https://maddie35.github.io/learning-portfolio/`. `.nojekyll` is included so Jekyll does not reprocess the files.

## Notes on the export

This originated as a Claude Design project. Two things changed on the way in:

- **The React runtime was removed.** The original pages wrapped their markup in `<x-dc>` and loaded `support.js`, which fetched React from a CDN at runtime and re-rendered the page. None of the six pages had any interactive logic, so the markup is now served directly as HTML. It renders identically, without the blank-page risk if the CDN is unreachable, and search engines and link previews can read it.
- **`lang="en"`, `<title>`, and meta descriptions were added.** The exported pages had none. A missing `lang` attribute is a WCAG 2.1 failure (3.1.1 Language of Page), which matters more than usual on an accessibility specialist's own site.

## Known trade-offs

- `assets/monday-training-clip.mp4` is 14 MB and `assets/maddie-reardon.png` is 3.5 MB at 1536×2048, displayed at roughly a third of that width. Both are worth compressing before this gets much traffic.
- The four essay PDFs are page captures without a text layer, so their contents are not selectable or screen-reader accessible. HTML versions would be a genuine improvement.
