

## Interactive Custom Matrix Builder

### Core Matrix Canvas
- Interactive 10x10 grid with customizable X and Y axis labels (e.g., "Hot" / "Crazy", or anything the user wants)
- Diagonal "threshold line" that can be toggled on/off
- Draggable data point labels on the canvas
- Zoom and pan support for crowded matrices
- Click on a data point to edit its name or coordinates inline

### Zone System
- Default zones: No-Go, Fun, Danger, Date, Wife/Marriage, Unicorn (matching the classic layout)
- Fully editable zone names, colors, and boundaries
- Add/remove zones with a simple UI
- 3 built-in presets: Classic Hot-Crazy, Enterprise Browser, and a blank template

### CSV Data Import
- Upload CSV with columns: name, x, y (and optional fields like category, notes)
- Preview table of imported data before placing on matrix
- Validation with error highlighting for out-of-range values
- Manual "Add Point" button for one-off entries
- Edit/delete points from a sidebar data table

### Background Customization
- 4-5 color scheme presets (Classic, Dark Mode, Pastel, Neon, Monochrome) that style all zones
- Custom color picker for individual zone colors
- Upload a custom background image with opacity slider so the grid remains visible

### Export
- **PNG**: High-res raster image download
- **SVG**: Scalable vector export
- **PDF**: Print-ready document export
- **CSV**: Re-export current data points for re-import later

### Additional Features
- **Undo/Redo** for drag operations and edits
- **Tooltip on hover** showing point name and exact coordinates
- **Search/filter** to highlight specific points on a crowded matrix
- **Dark mode toggle** for the whole app UI
- **Share link** that encodes the current state in a URL (no backend needed, uses URL hash)
- **Responsive layout** with sidebar for controls, main area for the canvas

### Layout
- Left sidebar: Data table, CSV upload, add point form, zone editor
- Center: Interactive matrix canvas
- Top toolbar: Presets, background settings, export buttons, undo/redo
- All data stays in-browser (localStorage optional for session persistence)

