# NASA Exoplanet Explorer

An interactive visualization tool for exploring **6,150 confirmed exoplanets** from the NASA Exoplanet Archive. Search by name, filter by planetary type, and view procedurally generated renderings of distant worlds — all in a single self-contained HTML file.

**[Launch the Explorer](https://troutm8.github.io/exoplanets/Exoplanet_Explorer.html)**

---

## Overview

This project packages the full NASA Exoplanet Archive dataset into a lightweight, browser-based exploration tool. Every confirmed exoplanet in the archive is searchable and viewable with detailed statistics, a procedural planet rendering, and a side-by-side size comparison with Earth and Jupiter.

No server, no API calls, no dependencies — just open the HTML file in any modern browser.

---

## Features

### Searchable Database
Type any planet name, host star, or constellation into the search bar to instantly filter across all 6,150 confirmed exoplanets. Results appear in a dropdown with key metadata for quick identification.

### Procedural Planet Rendering
Each planet is rendered on an HTML5 canvas using its real physical data. The visualization engine classifies planets into categories and generates appropriate surface features:

- **Gas Giants** — Atmospheric bands, storm spots, and cloud layers. Larger storms appear on more massive planets.
- **Habitable Worlds** — Continents, oceans, and cloud wisps rendered in blues and greens.
- **Lava Worlds** — Glowing magma cracks across a dark, superheated surface.
- **Ice Worlds** — Pale blue surfaces with fracture patterns.
- **Rocky Worlds** — Cratered terrain in earthy tones.
- **Neptune-like** — Smooth blue atmospheres with subtle banding.

The host star is also rendered with accurate color derived from stellar temperature (using the stellar classification color spectrum from blue-white O-type stars through red M-type dwarfs).

### Planet Classification Filters
One-click filter buttons categorize the full dataset into meaningful groups:

| Filter | Criteria |
|---|---|
| **All Planets** | Full dataset of 6,150 confirmed exoplanets |
| **Habitable Zone** | 293 planets orbiting within their star's habitable zone |
| **Hot Jupiters** | Gas giants (>0.3 M_J) with orbital periods under 10 days |
| **Super-Earths** | Planets between 1–10 Earth masses with radius < 2.5 Earth radii |
| **Earth-like** | Habitable zone planets with radius between 0.5–1.6 Earth radii |
| **Gas Giants** | Planets exceeding 1 Jupiter mass |

### Detailed Statistics Panel
For every selected planet, the tool displays:

- **Mass** — In Jupiter masses and Earth masses
- **Radius** — In Jupiter radii and Earth radii
- **Orbital Period** — In days and years
- **Equilibrium Temperature** — In Kelvin and Celsius
- **Semi-major Axis** — Distance from host star in AU
- **Distance from Earth** — In parsecs and light-years
- **Stellar Temperature** — Host star surface temperature in Kelvin
- **Stellar Radius** — Host star radius in solar radii
- **Habitable Zone Status** — Whether the planet orbits within the habitable zone
- **Discovery Method & Year** — How and when the planet was confirmed
- **Coordinates** — Right ascension and declination
- **Constellation** — The constellation where the planet is located

### Size Comparison
A visual side-by-side comparison shows the selected planet's radius relative to Earth and Jupiter, rendered as proportionally scaled circles.

### Orbital Context Bars
Logarithmic bar charts provide intuitive context for orbital period, distance from the host star, and distance from Earth.

### Random Planet Discovery
A "Random Planet" button selects a random world from the current filter set — a great way to stumble upon interesting planets you might not have searched for.

---

## Data

### Source
All data is sourced from the [NASA Exoplanet Archive](https://exoplanetarchive.ipac.caltech.edu/), a service of the NASA Exoplanet Science Institute (NExScI) operated by the California Institute of Technology under contract with NASA.

### Spreadsheet Structure
The file `NASA_Exoplanet_Archive.xlsx` contains two sheets:

**Confirmed Exoplanets** (6,150 rows) with the following columns:

| Column | Description | Unit |
|---|---|---|
| Planet Name | Official IAU designation | — |
| Host Star | Name of the host star | — |
| Discovery Method | Detection technique used | — |
| Discovery Year | Year of confirmed discovery | — |
| Orbital Period | Time to complete one orbit | days |
| Distance | Distance from Earth | parsecs |
| Mass | Planetary mass | Jupiter masses (M_J) |
| Radius | Planetary radius | Jupiter radii (R_J) |
| Eq. Temp | Equilibrium temperature | Kelvin |
| Semi-major Axis | Orbital distance from star | AU |
| Stellar Temp | Host star surface temperature | Kelvin |
| Stellar Radius | Host star radius | Solar radii (R_☉) |
| RA | Right ascension | HMS |
| Dec | Declination | DMS |
| Habitable Zone | Whether planet is in the HZ | Yes/No |
| Constellation | Constellation location | — |

**Summary & Statistics** — Aggregate breakdowns by discovery method, discovery year, habitable zone status, and other distributions.

### Discovery Methods Represented

| Method | Count |
|---|---|
| Transit | 4,517 |
| Radial Velocity | 1,182 |
| Microlensing | 275 |
| Imaging | 94 |
| Transit Timing Variations | 39 |
| Eclipse Timing Variations | 17 |
| Orbital Brightness Modulation | 9 |
| Pulsar Timing | 8 |
| Astrometry | 6 |
| Pulsation Timing Variations | 2 |
| Disk Kinematics | 1 |

---

## Files

```
├── README.md                        # This file
├── Exoplanet_Explorer.html          # Interactive visualization tool (~988 KB)
└── NASA_Exoplanet_Archive.xlsx      # Full dataset spreadsheet (~663 KB)
```

---

## Usage

### Online (GitHub Pages)
Visit **[troutm8.github.io/exoplanets/Exoplanet_Explorer.html](https://troutm8.github.io/exoplanets/Exoplanet_Explorer.html)** — no installation required.

### Local
1. Clone the repository:
   ```bash
   git clone https://github.com/troutm8/exoplanets.git
   ```
2. Open `Exoplanet_Explorer.html` in any modern web browser.

That's it. The entire dataset is embedded in the HTML file, so no server or internet connection is needed after download.

---

## Technical Details

### Architecture
The explorer is a single self-contained HTML file with no external dependencies (aside from Google Fonts for typography). All 6,150 planet records are embedded as a compact JSON array, parsed at load time into JavaScript objects.

### Rendering Engine
Planet visuals are drawn on an HTML5 `<canvas>` element using the 2D rendering context. The engine uses:

- **Seeded pseudo-random number generation** (Mulberry32 PRNG) keyed to each planet's name, ensuring the same planet always renders identically across sessions.
- **Radial gradients** for planetary bodies, atmospheres, and stellar objects.
- **Procedural surface detail** — bands, craters, continents, lava cracks, and ice fractures are generated algorithmically based on planetary classification.
- **Physically-motivated coloring** — Star colors map from stellar effective temperature using the standard spectral classification color scale. Planet colors derive from equilibrium temperature, mass, and radius.

### Performance
The embedded dataset is approximately 955 KB in compact JSON format. Initial page load parses all records in well under a second on modern hardware. Search filtering operates on the full in-memory dataset with no perceptible latency.

### Browser Compatibility
Tested and functional in all modern browsers: Chrome, Firefox, Safari, and Edge. Requires JavaScript enabled and HTML5 Canvas support.

---

## Interesting Planets to Explore

Here are some starting points for exploration:

- **Kepler-442 b** — A near-Earth-sized planet in the habitable zone of a K-type star, one of the most promising candidates for habitability.
- **TRAPPIST-1 e** — Part of the famous seven-planet system, orbiting in the habitable zone of an ultracool dwarf star just 12 parsecs away.
- **HD 209458 b** (Osiris) — The first exoplanet observed transiting its star and the first with an atmosphere detected, a textbook hot Jupiter.
- **51 Peg b** (Dimidium) — The first exoplanet discovered orbiting a Sun-like star (1995 Nobel Prize in Physics).
- **Kepler-16 b** — A circumbinary planet orbiting two stars, like Tatooine from Star Wars.

Use the "Habitable Zone" filter to browse all 293 planets that could potentially support liquid water.

---

## License

The NASA Exoplanet Archive data is publicly available and provided by NASA/IPAC/NExScI. The visualization tool and this repository are provided as-is for educational and exploratory purposes.

---

## Acknowledgments

- **NASA Exoplanet Archive** — For maintaining the comprehensive and publicly accessible database of confirmed exoplanets.
- **NASA Exoplanet Science Institute (NExScI)** — Operated by Caltech under contract with NASA.
- Built with the assistance of **Claude** (Anthropic).
