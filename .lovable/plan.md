

## Plan: Rename to RedFlag Grapher, Multi-Select, Fix Points & Background

### 1. Rename app to "RedFlag Grapher"
- `index.html`: Update `<title>` and og:title to "RedFlag Grapher"
- `src/pages/Index.tsx`: Add a header bar above the toolbar with "RedFlag Grapher" as the app title
- `src/lib/presets.ts`: Update default preset title from "Universal Hot Crazy Matrix" to "RedFlag Grapher"

### 2. Fix background image alignment (start at 0,0 not centered)
- `src/components/MatrixCanvas.tsx`: Change background image `preserveAspectRatio` from `"xMidYMid slice"` to `"xMinYMax slice"` so the image anchors at the bottom-left (0,0 origin of the matrix)

### 3. Fix points rendering off-chart
- The CSV placement jitter ranges in `PLACEMENT_MAP` sometimes produce values at the exact boundary (0 or 10) which can render at the edge of padding. Clamp all imported point coordinates to stay within `[xMin + 0.2, xMax - 0.2]` and `[yMin + 0.2, yMax - 0.2]` after jitter
- In `MatrixCanvas.tsx`, clamp point rendering coordinates to stay within the canvas area (between PADDING and PADDING + CANVAS_SIZE)

### 4. Multi-select and group drag
- `src/components/MatrixCanvas.tsx`:
  - Add `selectedIds: Set<string>` state for tracking selected points
  - Shift+click a point to toggle it in/out of selection
  - Click without shift to select only that point (clear others)
  - When dragging a selected point, move ALL selected points by the same delta
  - Visual indicator: selected points get a highlight ring/outline
  - Click on empty canvas area to deselect all
- `src/pages/Index.tsx`: Update `handlePointMove` to accept batch moves; pass `onPointsMove` callback that updates multiple points at once

### Files touched
- `index.html` -- title
- `src/pages/Index.tsx` -- header title bar, batch point move handler
- `src/components/MatrixCanvas.tsx` -- background alignment fix, multi-select + group drag, point clamping
- `src/lib/presets.ts` -- default title
- `src/lib/csvUtils.ts` -- clamp imported coordinates

