# Design and interview guide

This is a guide to understanding and adapting the draft, not a claim that a particular grade is guaranteed. Use your own words in the submission and interview.

## Domain, who and why

**Domain:** Passenger activity at Australian airports and the routes connecting them. Comparisons cover recent domestic activity and the longer-term pandemic disruption/recovery.

**Who:** The average Australian reader interested in travel, geography and national infrastructure. Industry knowledge is not assumed. Technical counting terms are defined on the page.

**Why:** Help readers locate the busiest airports, see that recovery differed between airports, compare activity relative to state population, and identify the main domestic connections. Geography explains the spatial distribution; companion diagrams support more precise comparisons.

## What

- Airports and routes are categorical entities.
- Financial year is temporal/ordered.
- Passenger movements, trips, seats, aircraft trips and population are quantitative.
- Latitude and longitude are spatial quantitative attributes.
- Growth rates, national shares, activity per resident and recovery indices are derived quantitative attributes.
- State is a nominal category. The state choropleth contains aggregated selected-airport activity, not airport-level polygons.

Government sources are BITRE and ABS. OurAirports and Natural Earth supply supporting geographic data. Consult DATA_NOTES.md for dates, calculations and coverage.

## How: idioms, marks and channels

| Panel | Idiom | Marks and channels | Task served |
| --- | --- | --- | --- |
| 1 | Proportional-symbol map | Geoshape areas form the base. Point position uses longitude/latitude. Circle **area** encodes passenger movements. | Locate airports and see where activity is concentrated. |
| 2 | Ranked bar chart | Rectangular/line-like bars. Common x-position and length encode passenger movements. Y-position identifies airports. | Compare passenger counts more precisely than circle areas. |
| 3 | Multi-line time series | Lines and points. X-position encodes financial year; y-position encodes passenger trips; hue identifies domestic/international services. | Compare the long-term trajectories and interruption. |
| 4 | Temporal heatmap | Rectangular areas. X-position encodes year, y-position airport, colour luminance encodes traffic relative to the airport's own 2018–19 baseline. | Compare the depth and pace of recovery across airports. |
| 5 | Dumbbell comparison | Points linked by rules. X-position encodes passenger movements; hue identifies the two years. | Compare before-pandemic and recent airport volume. |
| 6 | Choropleth map | Geographic area marks. Sequential colour luminance encodes selected-airport movements per resident. | Compare states without using misleading raw totals. |
| 7 | Waterfall | Rectangles and text. Y-position encodes cumulative change; bar height encodes a state's contribution; hue distinguishes increases, decreases and the total. | Explain how contributions reconcile to national growth. |
| 8 | Flow map | Geographic line marks over area marks. Position shows endpoints; line width encodes passenger trips in both directions. | Show which places are connected and how heavily those connections are used. |
| 9 | Adjacency matrix | Rectangular areas. Row/column position identifies airport pairs; sequential luminance on a **log scale** encodes passenger trips. | Compare connections without overlapping route lines. |
| 10 | Scatterplot | Points. X-position encodes aircraft trips and y-position passenger trips. | Compare the relationship between passenger and aircraft activity. |
| 11 | Normalised stacked bars | Rectangular areas. Bar segment length encodes the occupied/unoccupied seating share; hue distinguishes the two portions. | Compare seating use across routes. |
| 12 | Treemap | Nested rectangular areas. Rectangle area encodes passenger movements; grouping and hue identify state. | Show how activity is divided between airports within states. |

## Three different map idioms

All three use an Australia-centred **Albers equal-area conic projection**. The chosen southern standard parallels reduce distortion across the country, and area preservation is appropriate for the choropleth. The maps are not intended for measuring exact route distance or navigation.

1. The proportional-symbol map shows airport quantities at geographic point locations.
2. The choropleth fills geographic regions with a normalised quantitative value.
3. The flow map shows connections between geographic points and encodes their volumes with width.

Changing only a colour field on three proportional-symbol maps would not satisfy the brief's requirement for three different map idioms. This draft uses genuinely different encodings.

## Design principles

- Four chapters organise the progression: network → disruption/recovery → regional perspective → connections.
- Large maps carry geographic questions; smaller companion diagrams support exact comparisons.
- Teal consistently indicates domestic activity, while amber distinguishes international travel in the time series and negative contributions in the separately labelled waterfall. Legends explain each local use.
- The choropleth and heatmaps use ordered colour scales for quantities, not arbitrary categorical hues. State hues are categorical in the treemap only.
- Serif headings, sans-serif body text and small monospaced section labels create a hierarchy without changing fonts on every figure.
- Large margins and white figure backgrounds distinguish text and data from the off-white page.
- The page is responsive, uses semantic headings/figures, provides a skip link, and avoids major-section swaps. The chapter links only scroll within the same page.
- Airport year selection and route/hub filtering are purposeful. Tooltips expose exact values and counting units. There are no decorative controls that alter unrelated parts of the story.
- The route matrix uses grey for missing subset coverage, not a zero-valued quantitative colour. The map figure notes explicitly explain exclusions.

## Likely interview questions

**Why use a choropleth rather than circle size for state totals?**

The choropleth asks a regional comparison question using a normalised rate. Raw airport counts would mostly reflect state population, so they are divided by ABS population. Airport-specific volumes remain on the proportional map.

**Can I interpret 9.1 movements per resident as the NT resident flying 9.1 times?**

No. Airport counts include visitors and connections. The measure describes activity relative to a resident population, not individual behaviour or unique travellers.

**Why are some flow-map lines missing?**

The default displays the busiest fifteen routes to manage overlap. The dataset itself includes only sixty-two published competitive routes. Neither an absent line nor a grey matrix cell proves that no service exists.

**Why are there no arrows on the flow map?**

Route traffic combines both directions. Arrows would falsely suggest directional counts that are not available.

**Why does the matrix use a logarithmic colour scale?**

Route volumes range widely. Log colour makes smaller connections distinguishable without letting the busiest corridor consume most of the colour range. Tooltips and labelled legend values preserve exact interpretation. Position and line width in the flow map remain geographic/linear.

**Why are airport movements higher than passenger trips?**

A domestic passenger trip creates one departure and one arrival at two airports. Summing airport activity counts both ends. The two measures should not be summed together.

**What does 100% mean in the recovery heatmap?**

It is the airport's own 2018–19 passenger volume. It is not 100% of Australia's airport traffic, nor an aircraft load factor.

**Why do the historic comparison and current map have different figures?**

They use different service scopes and periods. Historical airport totals include domestic and international activity through 2024–25. The current map is domestic-only, through 2025–26. Both are explicitly labelled.

**What does the waterfall's Other airports bar mean?**

It is an arithmetic residual between the national domestic change and the selected-airport subtotal change. It is not invented airport data. It reconciles the calculation while acknowledging omitted airports.

**What did AI do, and what must I understand myself?**

ChatGPT assisted with development, data preparation, chart design and drafting. You should review the source values and limitations, adapt the design to your sketch, and explain the encodings and code yourself. The brief requires acknowledgement and genuine personal understanding.

## Final alignment still needed

Your hand-drawn sketch was not supplied. Check the story and layout against it. Your later map-idiom lecture notes may refine which non-map diagrams the tutor considers advanced. Two heatmap-style panels can be counted as one chart family; the draft deliberately contains twelve panels to give room for that treatment. Do not count a tooltip, annotation or KPI as another chart.
