# Utah District Finder

A free, single-page civic tool that looks up every political district for any Utah address — congressional, state legislative, school board, precinct, county, and municipality — in one place.

**Live site:** ([https://srobb1.github.io/utah-district-finder/](https://srobb1.github.io/utah-district-finder/))

---

## What it does

Enter any Utah street address and instantly see:

- U.S. Congressional District
- Utah State Senate District
- Utah State House District
- State School Board District
- Voting Precinct (with VISTA ID)
- County
- Municipality (or "Unincorporated" for rural addresses)

Each result links directly to the relevant official roster or representative page. The app also supports address autocomplete and GPS-based location lookup.

---

## Why this exists

Finding your political districts in Utah requires visiting multiple different websites, none of which are easy to use. This tool consolidates everything into a single address lookup backed by authoritative state data.

---

## Data sources

All district data is queried live from the **Utah Geospatial Resource Center (UGRC)** State Geographic Information Datasource (SGID). District boundaries reflect the 2026 court-ordered congressional redistricting and the 2022 post-census redistricting for state legislative districts.

| District | SGID Table | Field |
|---|---|---|
| U.S. Congressional | `political.district_combination_areas_2026` | `congress` |
| Utah Senate | `political.district_combination_areas_2026` | `senate` |
| Utah House | `political.district_combination_areas_2026` | `house` |
| State School Board | `political.district_combination_areas_2026` | `school` |
| Voting Precinct | `political.vista_ballot_areas` | `precinctid`, `vistaid` |
| County | `boundaries.county_boundaries` | `name` |
| Municipality | `boundaries.municipal_boundaries` | `name` |

Geocoding uses the [UGRC geocoding API](https://api.mapserv.utah.gov). Address autocomplete uses [Nominatim / OpenStreetMap](https://nominatim.openstreetmap.org) (no key required).

---

## Running locally

This is a single HTML file with no build step or dependencies.

1. Clone the repo:
   ```bash
   git clone https://github.com/yourusername/your-repo-name.git
   cd your-repo-name
   ```

2. Serve it locally (required — opening the file directly will cause CORS errors):
   ```bash
   python3 -m http.server 8000
   ```

3. Open [http://localhost:8000](http://localhost:8000) in your browser.

4. Get a free UGRC API key at [developer.mapserv.utah.gov](https://developer.mapserv.utah.gov) and register it to `localhost` for local development, or your GitHub Pages URL for production.

---

## Embedding on another site

The app can be embedded as an iframe on any website:

```html
<iframe
  src="https://yourusername.github.io/your-repo-name"
  width="100%"
  height="800"
  frameborder="0">
</iframe>
```

---

## Deployment

This site is hosted on **GitHub Pages** for free. Any push to the `main` branch automatically deploys.

To deploy your own copy:
1. Fork this repo
2. Enable GitHub Pages in Settings → Pages → Deploy from branch → main
3. Get a UGRC API key registered to your GitHub Pages URL
4. Update `DEFAULT_ADDRESS` in `index.html` if desired

---

## If something breaks

District boundary data occasionally changes table names after redistricting. The **About This Data** section at the bottom of the app lists every table name and links directly to the UGRC product page for each layer. The debug log (also at the bottom) shows raw API responses.

If a district returns "Not found," compare the table names in `index.html` against the current UGRC SGID documentation.

---

## Contributing

Issues and pull requests welcome. If you extend this for another state or add features, please open a PR — the goal is to make civic data accessible to everyone.

---

## License

MIT © 2026 [Your Name]

---

*Built with the [Utah UGRC API](https://api.mapserv.utah.gov) and [OpenStreetMap Nominatim](https://nominatim.openstreetmap.org). Not affiliated with the State of Utah or UGRC.*


## What it does

Enter any Utah street address and instantly see:

- U.S. Congressional District
- Utah State Senate District
- Utah State House District
- State School Board District
- Voting Precinct (with VISTA ID)
- County
- Municipality (or "Unincorporated" for rural addresses)

Each result links directly to the relevant official roster or representative page. The app also supports address autocomplete and GPS-based location lookup.

---

## Why this exists

Finding your political districts in Utah requires visiting multiple different websites, none of which are easy to use. This tool consolidates everything into a single address lookup backed by authoritative state data.

---

## Data sources

All district data is queried live from the **Utah Geospatial Resource Center (UGRC)** State Geographic Information Datasource (SGID). District boundaries reflect the 2026 court-ordered congressional redistricting and the 2022 post-census redistricting for state legislative districts.

| District | SGID Table | Field |
|---|---|---|
| U.S. Congressional | `political.district_combination_areas_2026` | `congress` |
| Utah Senate | `political.district_combination_areas_2026` | `senate` |
| Utah House | `political.district_combination_areas_2026` | `house` |
| State School Board | `political.district_combination_areas_2026` | `school` |
| Voting Precinct | `political.vista_ballot_areas` | `precinctid`, `vistaid` |
| County | `boundaries.county_boundaries` | `name` |
| Municipality | `boundaries.municipal_boundaries` | `name` |

Geocoding uses the [UGRC geocoding API](https://api.mapserv.utah.gov). Address autocomplete uses [Nominatim / OpenStreetMap](https://nominatim.openstreetmap.org) (no key required).

---

## Running locally

This is a single HTML file with no build step or dependencies.

1. Clone the repo:
   ```bash
   git clone https://github.com/yourusername/your-repo-name.git
   cd your-repo-name
   ```

2. Serve it locally (required — opening the file directly will cause CORS errors):
   ```bash
   python3 -m http.server 8000
   ```

3. Open [http://localhost:8000](http://localhost:8000) in your browser.

4. Get a free UGRC API key at [developer.mapserv.utah.gov](https://developer.mapserv.utah.gov) and register it to `localhost` for local development, or your GitHub Pages URL for production.

---

## Embedding on another site

The app can be embedded as an iframe on any website:

```html
<iframe
  src="https://yourusername.github.io/your-repo-name"
  width="100%"
  height="800"
  frameborder="0">
</iframe>
```

---

## Deployment

This site is hosted on **GitHub Pages** for free. Any push to the `main` branch automatically deploys.

To deploy your own copy:
1. Fork this repo
2. Enable GitHub Pages in Settings → Pages → Deploy from branch → main
3. Get a UGRC API key registered to your GitHub Pages URL
4. Update `DEFAULT_ADDRESS` in `index.html` if desired

---

## If something breaks

District boundary data occasionally changes table names after redistricting. The **About This Data** section at the bottom of the app lists every table name and links directly to the UGRC product page for each layer. The debug log (also at the bottom) shows raw API responses.

If a district returns "Not found," compare the table names in `index.html` against the current UGRC SGID documentation.

---

## Contributing

Issues and pull requests welcome. If you extend this for another state or add features, please open a PR — the goal is to make civic data accessible to everyone.

---

## License

MIT © 2026 [Your Name]

---

*Built with the [Utah UGRC API](https://api.mapserv.utah.gov) and [OpenStreetMap Nominatim](https://nominatim.openstreetmap.org). Not affiliated with the State of Utah or UGRC.*
