# CUUBE 3D Assembly Viewer

An interactive 3D model of the CUUBE building that assembles itself layer by layer. Visitors can drag to rotate, scroll to zoom, scrub the timeline, or jump to the exploded and assembled views.

## Files

| File | What it is |
|---|---|
| `index.html` | The whole viewer in one self-contained file: HTML, CSS and JavaScript. The CUUBE logo is embedded inside it as base64, so no other files are needed to run it. |
| `assets/cuube-logo.png` | The same logo as a standalone transparent PNG (1400 × 487), in case you'd rather load it from a file. |
| `README.md` | This file, including all on-page copy. |

## Running it

- Serve the folder from any web server, or open `index.html` directly in a browser.
- The only external dependencies are three.js r128, loaded from `cdnjs.cloudflare.com`, and the Montserrat font from Google Fonts.
- To embed the viewer in an existing page, put it in an `<iframe>`. The viewer is full-screen and uses fixed positioning, so it works best in its own container.

## Page copy

All visible text, so it can be reviewed or edited in one place.

### Header (HTML, around line 84)

| Element | Copy |
|---|---|
| Browser tab `<title>` | How the CUUBE goes together |
| Headline `<h1>` | How the CUUBE goes together |
| Subhead `<p>` | A permanent steel monopitch building, one layer at a time. Drag to turn it. |

The subhead is hidden on screens narrower than 760px.

### Assembly steps (JavaScript, `const STEPS`, around line 105)

Each step has a heading (`h`) and a description (`d`). The description appears while that step is active.

| # | Heading | Description |
|---|---|---|
| 1 | A solid, level base | Concrete slab and walkway built for daily foot traffic |
| 2 | Move-in-ready interior | Finished floor ready for classrooms, offices or labs |
| 3 | Seismic-rated steel moment frame | Bolt-together – no field welds |
| 4 | R-35 insulated wall panels | Ships on standard trucks |
| 5 | Daylight-filled spaces | Full-height glass doors and a clerestory band bring in natural light |
| 6 | Power from above | Standing seam roof with solar panels and a deep shading overhang |

The six steps are tied to the six animated layers. If you add or remove a step, the timeline (`const S`) and the layer code must change to match.

### Controls

| Element | Copy |
|---|---|
| Button | Exploded |
| Button | Assembled |
| Play/pause button (screen-reader label) | Play / Pause |
| Timeline slider (screen-reader label) | Animation timeline |
| Controls group (screen-reader label) | Animation controls |

### Accessibility and fallback text

| Element | Copy |
|---|---|
| 3D canvas `aria-label` | 3D model of the CUUBE building assembling layer by layer. Drag to rotate. |
| Error message if three.js fails to load | The 3D viewer could not load. Check your connection and reload the page. |

## Colors

### Building model (JavaScript, `const C`)

| Part | Hex |
|---|---|
| Wall panels | `#EFEDE9` |
| Brown base band | `#5E3622` |
| Roof | `#2B3352` |
| Roof edge | `#262E4A` |
| Door awnings | `#2E3656` |
| Solar panels | `#7B7F86` |
| Window and door frames | `#1B1E23` |
| Glass | gradient from `#5A6068` to `#16191D` |

### Page interface (CSS variables)

| Variable | Light mode | Dark mode |
|---|---|---|
| `--navy` | `#1F3A6E` | `#8FB0E8` |
| `--goldbar` | `#C9A227` | `#D9B24A` |
| `--gold` | `#9A7414` | `#E0BC5A` |
| `--bg` | `#E7ECF2` | `#0D1626` |
| `--ink` | `#14213A` | `#E6EBF2` |

## Notes

- **Logo:** the logo appears on the west end wall. The `addLogo()` function places it, and `LOGO_SRC` holds the embedded image. To use the separate PNG instead, set `LOGO_SRC = 'assets/cuube-logo.png'` and serve the folder from a web server. Opening the file directly from disk with an external image can be blocked by the browser.
- **Windows and doors:** each wall's openings are defined in `sides.<wall>.open` as `[left, bottom, right, top, kind, columns, rows]`.
- **Content to confirm:** step 6 mentions solar panels, which were added to match the latest renderings. Confirm this before the page goes live.
