# Paper String

Paper String is a professional browser-based photo and graphic editing workspace built around the core loop:

**Create → Edit → Save → Export**

Secondary flow:

**Templates → Select → Edit → Save → Export**

This repository currently contains the UI/UX foundation and a self-contained interactive product prototype.

## Product boundaries

Paper String is not a social network, public publishing platform, viewer, generic AI dashboard, or template marketplace.

The editor is the primary product surface. Multiple canvases are editing surfaces, not presentation pages.

## What is included

- Product information architecture
- Blank-project and template-project flows
- Private Projects workspace
- Dedicated Templates area with clearly marked development placeholders
- Responsive creative editor layout
- Canvas setup with arbitrary width/height
- Multi-canvas page strip
- Layer stack and layer states
- Tool rail including selection, image, text, shape, brush, eraser, crop, and selection
- Persistent undo/redo controls
- Save-state communication
- Export flow without low/medium/high quality choices
- Responsive desktop / tablet / mobile behavior
- Foundational accessibility states and reduced-motion support

## Design documentation

See docs/PAPER-STRING-UX.md for the full UI/UX architecture, user flows, design system, responsive strategy, state model, and interaction specifications.

## Prototype

Open index.html in a browser. The prototype is self-contained and does not depend on an external UI library or network API.
