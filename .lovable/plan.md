

## Plan: Fix Build Error + Add "Place in Zone" Feature

### 1. Fix syntax error in `MatrixCanvas.tsx` (line 295-296)
The points `.map()` is missing its closing `})}`. Line 295 has `);` but the map's closing bracket is missing before the placement overlay block starts at line 296.

**Fix**: Add `})}` after line 295, before the placement mode overlay.

### 2. Add "Place in Zone" button to sidebar selection controls (`MatrixSidebar.tsx`)
Next to "Place on Chart" and "Distribute", add a **"Place in Zone"** button that opens a dropdown/select of available zones. When a zone is selected, the selected points are randomly distributed within that zone's bounds (x1,y1 → x2,y2) with jitter.

- Add a `Select` component listing zones by name
- On zone selection, call a new `onPlaceInZone(zoneId: string)` callback

### 3. Add `handlePlaceInZone` in `Index.tsx`
- Takes a zone ID, finds zone bounds (x1,y1,x2,y2)
- Distributes selected points randomly within those bounds using `Math.random()` scaling
- Calls `batchUpdatePoints`

### Files touched
- `src/components/MatrixCanvas.tsx` — fix missing `})}`
- `src/components/MatrixSidebar.tsx` — add zone placement dropdown button
- `src/pages/Index.tsx` — add `handlePlaceInZone` handler, pass to sidebar

