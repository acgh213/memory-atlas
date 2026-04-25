# Memory Atlas

**A hindsight visualization** — an interactive D3.js-powered atlas for exploring and navigating memory data. Visualizes temporal patterns, relationships, and connections across a corpus of thoughts, sessions, and reflections with a dark, scholarly aesthetic.

## Features

- **Interactive D3 Visualization** — Zoomable, pannable atlas of memory nodes
- **Temporal Navigation** — Explore memories across time with smooth transitions
- **Node Relationships** — Visualize connections and associations between entries
- **Search & Filter** — Find and isolate specific memories or patterns
- **Responsive Design** — Adapts to any screen size with a dark academic theme
- **Custom Styling** — Serif typography, muted palette, custom scrollbars
- **Zero Server Dependencies** — Fully client-side, static deployment

## Screenshots

<!-- TODO: Add screenshots of the atlas -->

| Atlas Overview | Node Detail | Temporal View |
|----------------|-------------|---------------|
| ![Screenshot](https://via.placeholder.com/400x250?text=Memory+Atlas+Overview) | ![Screenshot](https://via.placeholder.com/400x250?text=Node+Detail) | ![Screenshot](https://via.placeholder.com/400x250?text=Temporal+View) |

## Tech Stack

- **Frontend:** HTML5, CSS3, Vanilla JavaScript
- **Visualization:** D3.js v7 (bundled inline)
- **Typography:** Georgia, Times New Roman, serif
- **Build:** None — served directly as a single HTML file

## Setup

1. **Clone the repository:**
   ```bash
   git clone https://github.com/acgh213/memory-atlas.git ~/memory-atlas
   cd ~/memory-atlas
   ```

2. No dependencies to install. The atlas is a single self-contained HTML file with D3.js bundled inline.

## Run

**Serve with any static file server:**

Using Python:
```bash
cd ~/memory-atlas
python3 -m http.server 8901
```

Using Node.js (npx):
```bash
cd ~/memory-atlas
npx serve .
```

Open your browser to the local server address.

## GitHub

[https://github.com/acgh213/memory-atlas](https://github.com/acgh213/memory-atlas)

## License

MIT
