

## Plan: Placement-Based CSV Import, Point/Zone Enhancements, Dark Mode, and More

### 1. Smart placement-based CSV import (`src/lib/csvUtils.ts`)
- When CSV has no numeric x/y columns but has a text column with placement hints (like "Suggested_Matrix_Placement"), parse quadrant keywords ("Marry", "Hot", "Crazy", "Fun", "Danger", "Unicorn", "No-Go", "Date", "Wife") to derive approximate x,y coordinates
- Map each quadrant keyword to a coordinate range, then jitter points randomly within that range so they don't overlap
- Keep existing numeric column detection as fallback -- placement parsing is a new fallback when no numeric columns are found

### 2. Remove Enterprise Browser preset (`src/lib/presets.ts`)
- Delete the `enterprise-browser` entry from `PRESETS` array, keep only `hot-crazy` and `blank`

### 3. Auto-distribute "Sort Points" button (`src/lib/distributePoints.ts`, `src/components/MatrixSidebar.tsx`)
- New utility that re-spaces all current points into a non-overlapping grid within axis bounds
- Add "Distribute" button below Import CSV in sidebar

### 4. Point icon/image upload (`src/types/matrix.ts`, `src/components/MatrixSidebar.tsx`, `src/components/MatrixCanvas.tsx`)
- Add `iconUrl?: string` to `DataPoint` type
- Add image upload button per point in sidebar edit mode
- Render icon as SVG `<image>` on canvas when set, fall back to circle

### 5. Enhanced point editing (`src/components/MatrixSidebar.tsx`)
- Expand inline edit to allow changing x, y, category, and name together (not just name)

### 6. Zone image with opacity (`src/types/matrix.ts`, `src/components/MatrixSidebar.tsx`, `src/components/MatrixCanvas.tsx`)
- Add `imageUrl?: string` and `imageOpacity?: number` to `Zone` type
- Add image upload and opacity slider per zone in sidebar
- Render zone image clipped to zone bounds in SVG

### 7. More color schemes (`src/lib/presets.ts`)
- Add `ocean`, `sunset`, `forest`, `cyberpunk` schemes

### 8. Application dark mode (`src/pages/Index.tsx`, `src/components/MatrixToolbar.tsx`)
- Add Moon/Sun toggle button in toolbar that toggles `dark` class on `<html>`
- Persist preference in localStorage
- Ensure canvas SVG text uses CSS-variable-aware colors

### Files touched
- `src/types/matrix.ts` -- add `iconUrl` to DataPoint, `imageUrl`/`imageOpacity` to Zone
- `src/lib/csvUtils.ts` -- placement keyword parsing with jittered coordinate mapping
- `src/lib/presets.ts` -- remove enterprise preset, add 4 color schemes
- `src/lib/distributePoints.ts` -- new file, grid distribution utility
- `src/components/MatrixSidebar.tsx` -- distribute button, enhanced edit UI, point icon upload, zone image upload + opacity
- `src/components/MatrixCanvas.tsx` -- render point icons, zone images with clip paths
- `src/components/MatrixToolbar.tsx` -- dark mode toggle
- `src/pages/Index.tsx` -- dark mode state management

