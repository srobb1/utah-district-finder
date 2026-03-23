# Utah District Finder

A free civic tool that looks up every political district for any Utah address — congressional, state legislative, school board, precinct, county, and municipality — in one place.

**Live site:** [srobb1.github.io/utah-district-finder](https://srobb1.github.io/utah-district-finder)

---

## Tools

| Tool | Description |
|---|---|
| [index.html](https://srobb1.github.io/utah-district-finder/) | Single address lookup |
| [batch.html](https://srobb1.github.io/utah-district-finder/batch.html) | Batch CSV lookup — upload a list, download results |
| [embed.html](https://srobb1.github.io/utah-district-finder/embed.html) | Lightweight widget for embedding via iframe |

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

The **batch tool** accepts a CSV in any of these formats and auto-detects which one you're using:

| Format | Columns |
|---|---|
| A — Single column | `address` — e.g. `3572 N Morgan Valley Dr, Morgan, UT 84050` |
| B — Street + zone | `street`, `city` or `zip` |
| C — Split street | `street_number`, `street_name`, `city`, `zip` |

Results can be downloaded as CSV or TSV with all district columns appended to your original data.

---

## Why this exists

Finding your political districts in Utah requires visiting multiple different websites, none of which are easy to use. This tool consolidates everything into a single address lookup backed by authoritative state data.

---

## API key

The live site at `srobb1.github.io` uses a baked-in UGRC API key registered to that domain. Visitors don't need their own key.

If you fork this repo and deploy it elsewhere, the app will automatically prompt users for their own UGRC API key registered to your domain. Keys are free at [developer.mapserv.utah.gov](https://developer.mapserv.utah.gov) and take about 2 minutes to create. Update the `OWNER_DOMAIN` and `OWNER_API_KEY` constants near the top of `index.html` and `batch.html` to use your own key silently on your domain.

> **Note on the batch tool and API usage:** Each address in a batch lookup generates up to 7 API calls (1 geocode + 6 district queries). The batch tool throttles requests to ~4 addresses per second to be courteous to UGRC's free service. For very large lists (500+ addresses), consider emailing UGRC at `ugrc-developers@utah.gov` to give them a heads up. They've noted the API is not rate limited but ask users to be fair.

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

No build step or dependencies required — just two HTML files.

1. Clone the repo:
   ```bash
   git clone https://github.com/srobb1/utah-district-finder.git
   cd utah-district-finder
   ```

2. Serve it locally (required — opening files directly causes CORS errors):
   ```bash
   python3 -m http.server 8000
   ```

3. Open [http://localhost:8000](http://localhost:8000) in your browser.

4. Get a free UGRC API key at [developer.mapserv.utah.gov](https://developer.mapserv.utah.gov), register it to `localhost`, and paste it when prompted.

---

## Embedding on another site

Use `embed.html` for the cleanest iframe experience — it's a stripped-down widget with just the address input and results, no header, footer, or debug panel. Because the iframe always loads from `srobb1.github.io`, the owner API key is used automatically — no key setup needed for embedders.

```html
<iframe
  src="https://srobb1.github.io/utah-district-finder/embed.html"
  width="100%"
  height="520"
  frameborder="0"
  title="Utah District Finder">
</iframe>
```

The full pages can also be embedded if you prefer:

```html
<!-- Full single address tool -->
<iframe
  src="https://srobb1.github.io/utah-district-finder/"
  width="100%"
  height="800"
  frameborder="0">
</iframe>
```

See [embed-test.html](https://srobb1.github.io/utah-district-finder/embed-test.html) for a live demo of the widget embedded in a mock county website.

---

## Deployment

Hosted on **GitHub Pages** for free. Any push to `main` automatically deploys.

To deploy your own copy:
1. Fork this repo
2. Enable GitHub Pages in Settings → Pages → Deploy from branch → main
3. Get a UGRC API key registered to your GitHub Pages URL (e.g. `yourname.github.io`)
4. Update `OWNER_DOMAIN` and `OWNER_API_KEY` in both `index.html` and `batch.html`
5. Optionally set `DEFAULT_ADDRESS` in `index.html` to pre-fill your own address

---

## If something breaks

District boundary data occasionally changes table names after redistricting. The **About This Data** section at the bottom of the app lists every table name and links directly to the UGRC product page for each layer. The debug log (also at the bottom of the single address tool) shows raw API responses.

If a district returns "Not found," compare the table names in `index.html` against the current UGRC SGID documentation at [gis.utah.gov/products/sgid/political](https://gis.utah.gov/products/sgid/political/).

---

## Contributing

Issues and pull requests welcome. If you extend this for another state or add features, please open a PR — the goal is to make civic data accessible to everyone.

---

## License

MIT © 2026 Sofia Robb

---

*Built with the [Utah UGRC API](https://api.mapserv.utah.gov) and [OpenStreetMap Nominatim](https://nominatim.openstreetmap.org). Not affiliated with the State of Utah or UGRC.*
