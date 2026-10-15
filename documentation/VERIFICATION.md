# Verification performed

14 October 2026.

- Parsed and rendered all eleven Vega-Lite specifications and the Vega treemap through the bundled Vega runtime.
- Rendered each chart at wide and narrow widths; visually inspected the maps, historical comparisons, waterfall, matrix and treemap. Improved label contrast, legend titles and narrow heatmap labels after inspection.
- Tested the airport-map year signal at both years and the route-map hub/route-limit signals, including Perth with all its published connections.
- Checked airport/route key uniqueness, expected row counts, geographic bounds, population joins, passenger/seat bounds, selected-state totals and the national waterfall reconciliation.
- Compared source seat utilisation with passenger/seat ratios. Retained and documented the one published Brisbane–Emerald discrepancy instead of editing the source value.
- Syntax-checked the page JavaScript and all standalone-preview inline scripts.
- Unit-tested the page loader with its offline bundle: all twelve charts hydrate without network requests. Verified all local asset and documentation links resolve.

## Limits

Full browser layout/interaction QA and the actual GitHub Pages deployment have **not** been performed in this environment. Static chart rendering and loader unit tests do not replace those checks. Follow the README's incognito-window and laptop-width checks immediately after publishing.

The draft has not been checked against the user's hand-drawn sketch because that sketch was not supplied. Later lecture notes and critique feedback still need to be incorporated. The current full BITRE airport workbook was unavailable, so the report-based historical tables should be cross-checked if it becomes available before final submission.
