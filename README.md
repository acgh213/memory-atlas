# Memory Atlas

**A Hindsight memory visualization** — an interactive D3.js-powered atlas for exploring, navigating, and understanding long-term memory data. Visualizes temporal patterns, semantic relationships, entity connections, and topic structures across a corpus of thoughts, sessions, and reflections with a dark, scholarly aesthetic.

> *"The shape of what I remember."*

---

## Overview

Memory Atlas is a single-page visualization frontend that consumes Hindsight memory data and renders it across five interconnected views. Each view offers a different lens on the same underlying memory corpus — from the organic clustering of a force-directed graph to the structured chronology of a timeline. Built entirely client-side with D3.js v7 bundled inline.

---

## Features

### 1. Force-Directed Memory Graph — *"The Shape of What I Remember"*
An interactive, zoomable force graph where each node represents a single memory (observation, experience, or world fact). Nodes are connected by edges when they share entities or topics. Drag nodes to explore, hover for tooltips with full text and timestamps.

- **Physics simulation** — d3-force with charge, link, collision, and centering forces
- **Color-coded by type** — observation (gold), experience (lavender), world (rose)
- **Node sizing** — proportional to text length
- **Zoom & pan** — scale from 0.3× to 4×
- **Legend** — type key in the top-right corner

### 2. Timeline — *"When I Remembered"*
A chronological scatter plot mapping memories across time, arranged into three horizontal rows by memory type. Each dot is a memory; hover to inspect.

- **Temporal axis** — time-scaled with formatted tick labels
- **Row layout** — observation, experience, and world in separate bands
- **Hover expansion** — dots scale up on interaction
- **Alternating row backgrounds** — subtle visual guidance

### 3. Topic Constellation — *"Constellation of Thought"*
A circular celestial map of topics, arranged as stars. Topic frequency determines star size; connecting lines reveal co-occurrence relationships between topics across memories.

- **Radial layout** — even angular distribution around a center
- **Pulsing glow** — animated outer halos with staggered delay
- **Edge weight** — line thickness encodes co-occurrence strength
- **Labels** — topic name and count displayed above each node

### 4. Entity Web — *"The People in My Mind"*
A network visualization of named entities (people, concepts) connected by shared memories. Entity size reflects total mentions; edge labels show co-occurrence counts.

- **Central hub layout** — primary entity at center, others arranged around
- **Proportional sizing** — node radius scales with mention count
- **Animated halos** — slow pulse on each entity node
- **Edge annotations** — numeric co-occurrence labels on connections

### 5. Searchable Memory Stream — *"The Full Stream"*
A paginated, filterable, searchable chronological list of every memory. Search across all memory text, filter by type, and load more with pagination.

- **Full-text search** — real-time filtering as you type
- **Type filter buttons** — observation / experience / world with visual active state
- **Pagination** — 20 memories per page with "Load more" button
- **Fade-in animation** — staggered card entrance on render
- **Entity tags** — inline entity badges on each card
- **Result count** — always shows how many memories match current filters

---

## Screenshots

| View | Preview |
|------|---------|
| **Force Graph** | ![Force Graph](https://via.placeholder.com/800x450?text=Memory+Atlas+-+Force+Graph+View) |
| **Timeline** | ![Timeline](https://via.placeholder.com/800x250?text=Memory+Atlas+-+Timeline+View) |
| **Topic Constellation** | ![Topic Constellation](https://via.placeholder.com/800x450?text=Memory+Atlas+-+Topic+Constellation) |
| **Entity Web** | ![Entity Web](https://via.placeholder.com/800x350?text=Memory+Atlas+-+Entity+Web) |
| **Memory Stream** | ![Memory Stream](https://via.placeholder.com/800x400?text=Memory+Atlas+-+Memory+Stream) |

> Screenshots are placeholders. Replace with actual captures of the running atlas.

---

## Architecture

```
┌─────────────────────────────────────────────────────┐
│                 Memory Atlas (index.html)            │
│                                                      │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌────────┐ │
│  │  Force   │ │ Timeline │ │  Topic   │ │ Entity │ │
│  │  Graph   │ │          │ │Constell. │ │  Web   │ │
│  └──────────┘ └──────────┘ └──────────┘ └────────┘ │
│  ┌────────────────────────────────────────────────┐ │
│  │            Memory Stream (search/filter)        │ │
│  └────────────────────────────────────────────────┘ │
│                                                      │
│  Engine: D3.js v7 (bundled inline)                   │
│  Data:   Inline JSON from Hindsight memory system    │
│  Style:  Dark academic theme, serif typography       │
└─────────────────────────────────────────────────────┘
```

- **Frontend**: HTML5, CSS3, Vanilla JavaScript
- **Visualization**: D3.js v7.9.0 (bundled inline — no CDN dependency)
- **Data format**: Inline JSON with `total_memories`, `fact_types`, `dates`, `entities`, `topics`, and `memories` arrays
- **Typography**: Georgia, Times New Roman, serif — scholarly aesthetic
- **Styling**: Dark background (`#0a0a0f`), muted gold/lavender/rose accents, custom scrollbars, backdrop blur tooltips
- **Build**: None — served directly as a single HTML file
- **Deployment**: Zero server dependencies, fully client-side, static anywhere

---

## Data Format

Memory Atlas expects a global `DATA` object with the following shape:

```js
{
  "total_memories": 151,
  "fact_types": {
    "observation": 68,
    "experience": 49,
    "world": 34
  },
  "dates": {
    "2026-04-24": 5,
    "2026-04-25": 146
  },
  "entities": {
    "Vesper": 82,
    "Cassie": 55,
    "Avocado": 4,
    "Bridget": 4
  },
  "topics": {
    "memory": 22,
    "model": 22,
    "research": 19,
    "hindsight": 15
  },
  "memories": [
    {
      "id": "uuid",
      "text": "Memory content...",
      "context": "Optional context string",
      "date": "2026-04-25T19:24:17.542947+00:00",
      "fact_type": "observation|experience|world",
      "involving": "Optional entity string"
    }
  ]
}
```

Data is currently embedded inline in `index.html`. For dynamic usage, replace the `DATA` assignment with a fetch from a Hindsight API endpoint.

---

## Setup

### Prerequisites

- A modern web browser (Chrome, Firefox, Safari, Edge)
- Any static file server (or none — `index.html` can open directly)

### Quick Start

1. **Clone the repository:**

   ```bash
   git clone https://github.com/acgh213/memory-atlas.git
   cd memory-atlas
   ```

2. **Open directly (no server needed):**

   ```bash
   open index.html    # macOS
   xdg-open index.html  # Linux
   start index.html   # Windows
   ```

3. **Or serve with any HTTP server:**

   Using Python:
   ```bash
   cd memory-atlas
   python3 -m http.server 8901
   ```

   Using Node.js:
   ```bash
   cd memory-atlas
   npx serve .
   ```

   Using Flask (if you have it installed):
   ```bash
   cd memory-atlas
   python3 -c "from flask import Flask, send_from_directory; app = Flask(__name__); app.add_url_rule('/<path:path>', 'static', lambda path: send_from_directory('.', path)); app.add_url_rule('/', 'index', lambda: send_from_directory('.', 'index.html')); app.run(port=8889)"
   ```

4. Open your browser to the local server address.

### Replacing Data

To visualize your own Hindsight memory data, replace the `DATA` object in `index.html` (around line 287) with your own JSON. The entity extraction and topic detection use a hardcoded allowlist — update `knownEntities` and `knownTopics` arrays (around lines 308-309) to match your data.

---

## Customization

### Styling

Colors, fonts, and spacing are controlled via CSS variables and the `typeColors` / `typeLabels` objects in the script. The dark academic palette can be adjusted by modifying:

- `body` background and text colors
- `typeColors` object: `observation`, `experience`, `world` color values
- `--` CSS custom properties in the style block

### Visualization Parameters

Each visualization section is an IIFE (Immediately Invoked Function Expression) in the script:

- **Force graph**: Adjust `forceLink().distance()`, `forceManyBody().strength()`, `forceCollide().radius()` in `buildHerd()`
- **Timeline**: Change `rowH`, margins, dot sizing in `buildTimeline()`
- **Topic Constellation**: Tweak `radius`, `angle`, node sizing in `buildTopicConstellation()`
- **Entity Web**: Modify `positions`, `nodeSizes`, colors in `buildEntityWeb()`
- **Memory Stream**: Change `PAGE_SIZE` in `buildStream()`

---

## GitHub

[https://github.com/acgh213/memory-atlas](https://github.com/acgh213/memory-atlas)

---

## License

MIT
