# Interactive Essay Tool

A single-file essay template combining David Foster Wallace–style expanding footnotes with Italo Calvino–inspired structural elements.

## Quick Start

1. Clone the repo: `git clone https://github.com/NKAlfredBot/essay-tool.git`
2. Open the folder in VS Code
3. Install the "Live Server" extension (if you don't have it)
4. Copy `blank-essay.html` → rename for your essay
5. Right-click → "Open with Live Server" for live preview
6. Start writing! Use snippets (see below) or copy from `palette.html`

## Files

| File | Purpose |
|------|---------|
| `blank-essay.html` | Minimal starter — start here |
| `essay-template.html` | Full example with all components |
| `palette.html` | Visual component palette with copy buttons |
| `.vscode/html.code-snippets` | VS Code snippets for fast authoring |
| `README.md` | This file |

## VS Code Snippets

With the folder open in VS Code, type these shortcuts then press **Tab**:

| Shortcut | Component |
|----------|-----------|
| `fn` | Basic footnote |
| `fnn` | Nested footnote |
| `div` | Section divider (◆) |
| `h2` | Section heading |
| `pp` | Paragraph |
| `reader` | Reader address block |
| `frame` | Full nested frame |
| `paths` | Multiple paths (3 options) |
| `bq` | Blockquote |
| `link` | Hyperlink |

## Component Palette

Open `palette.html` in your browser for a visual reference with **copy buttons** for each component.

---

## Components

### 1. DFW Footnotes (Expanding)

Inline footnotes that expand when clicked. Can be nested infinitely.

```html
<p>
  Your main text with a 
  <span class="fn" data-fn="1">phrase that has a footnote</span>.
</p>

<aside class="fn-content" data-fn="1">
  <p>The footnote content appears here when clicked.</p>
  <p>Can have multiple paragraphs.</p>
  
  <!-- Nested footnote -->
  <span class="fn" data-fn="1a">More text</span>
  <aside class="fn-content" data-fn="1a">
    <p>A footnote within a footnote.</p>
  </aside>
</aside>
```

**Tips:**
- Use sequential numbering: 1, 2, 3... 
- Nested footnotes: 1a, 1b, 1a-i, etc.
- Place `fn-content` immediately after the paragraph containing the `fn`
- Press **Escape** to close all footnotes

---

### 2. Calvino: Reader Address

Directly addresses the reader. Breaks the fourth wall.

```html
<aside class="reader-address">
  You, reader, have now reached the midpoint. 
  Consider what you expected to find here.
</aside>
```

---

### 3. Calvino: Frame Within Frame

Nested containers that visualize layers of meaning.

```html
<div class="frame frame--outer">
  <span class="frame-label">The Surface</span>
  
  <div class="frame frame--middle">
    <span class="frame-label">The Structure</span>
    
    <div class="frame frame--inner">
      <span class="frame-label">The Core</span>
      <p>The essential truth lives here.</p>
    </div>
  </div>
</div>
```

---

### 4. Calvino: Multiple Paths

Let readers choose different perspectives on the same material.

```html
<div class="paths">
  <button class="path" data-path="craft">The Craft</button>
  <button class="path" data-path="meaning">The Meaning</button>
  <button class="path" data-path="process">The Process</button>
</div>

<div class="path-content" data-path="craft">
  <p>Technical details about how it was made...</p>
</div>

<div class="path-content" data-path="meaning">
  <p>What it represents, what questions it raises...</p>
</div>

<div class="path-content" data-path="process">
  <p>The journey of making it, what surprised you...</p>
</div>
```

---

### 5. Section Divider

Calvino-style diamond separator between sections.

```html
<div class="divider">◆</div>
```

---

### 6. Marginal Notes (Desktop Only)

On wide screens (>1100px), these appear in the margin. On mobile, they appear inline.

```html
<p>
  <span class="marginal">
    Main text continues here
    <span class="marginal-note">A side observation that doesn't interrupt the flow.</span>
  </span>
  and the paragraph goes on.
</p>
```

---

## Structure

```
essay-template.html
├── <head>
│   ├── Meta tags (edit title, description)
│   ├── Google Fonts
│   └── <style> (all CSS inline)
├── <body>
│   ├── .progress-bar (reading progress)
│   ├── .essay (main container)
│   │   ├── .section-label
│   │   ├── h1 (title)
│   │   ├── .subtitle
│   │   ├── p (paragraphs)
│   │   ├── .fn / .fn-content (footnotes)
│   │   ├── .divider
│   │   ├── h2 (section headings)
│   │   ├── .reader-address
│   │   ├── .frame (nested frames)
│   │   ├── .paths / .path-content
│   │   ├── .fn-stats
│   │   └── .colophon
│   └── <script> (all JS inline)
```

---

## Customization

### Colors

Edit the CSS variables in `:root`:

```css
:root {
  --cream: hsl(45, 40%, 96%);      /* Background */
  --ink: hsl(30, 10%, 15%);        /* Text */
  --twilight: hsl(260, 30%, 60%);  /* Headings, accents */
  --fn-blue: hsl(210, 60%, 45%);   /* Footnote markers */
}
```

### Typography

The template uses:
- **EB Garamond** — Body text
- **IBM Plex Mono** — Footnotes, stats
- **Inter** — Labels, UI elements

Change in both the Google Fonts link and the `--font-*` variables.

---

## Deployment

The file is self-contained. No build step needed.

**Options:**
1. **Static hosting:** Upload to Netlify, Vercel, GitHub Pages
2. **Personal site:** Add to your existing site's directory
3. **Substack:** Use the "Import" feature or embed via iframe

---

## Credits

Design components adapted from the [Artist Style Guides](https://github.com/NKAlfredBot/artist-style-guides) project.

Inspired by:
- David Foster Wallace's recursive footnotes
- Italo Calvino's *If on a winter's night a traveler*
- *Six Memos for the Next Millennium*
