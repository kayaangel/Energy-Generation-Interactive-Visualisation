# Map Deck Visualization

## Summary
This R Markdown file contains a comprehensive case study on USA power plant energy production (2013–2019). It builds an interactive Shiny dashboard with spatial visualization and time-series analysis.

#### Video Demo of Dashboard
[![Watch the video](https://raw.githubusercontent.com/kayaangel/Advanced-visualisation/main/Video_Demo_Thumnail.png)](https://github.com/kayaangel/Advanced-visualisation/main/Video_Demo.mp4)

## Key Sections

### Data Preparation

* Only USA data (excluding Alaska/Hawaii) is used from the Global Power Plant Database.
* Missing values are cleaned from "generation" data across 2013–2019.
* Only relevant columns are selected for visualisation.

### Spatial Processing

* Power plant locations are converted to spatial features (sf objects) using ESRI:54030 projection.
* A 10km × 10km grid is created for spatial aggregation.

### Grid Aggregation

* Generation data is aggregated by grid cell and fuel type.
* The dominant fuel type is identified per cell (highest generation).
* Colours are assigned based on fuel source using RColorBrewer palettes.
* Grids are precomputed upfront for all years for instant slider updates. This is the most computationally intensive section.

### Interactive Dashboard (Shiny App)

* Map: 3D mapdeck visualization showing grid cells colored by dominant fuel type, with elevation representing total generation
* Slider: Year selector (2013–2019) with auto-animation
* Filter: Toggle by specific fuel source or view all
* Legend: Dynamic legend showing fuel types in current view
* Line Chart: Time-series plot tracking generation trends by fuel type from 2013 to the selected year

### Technical Details

* Uses mapdeck for interactive 3D maps with Mapbox (requires API token from Secret.R)
* Applies spatial joins and aggregations with sf package
* Leverages dplyr and tidyr for data manipulation
* Color-coded by primary fuel type for quick visual distinction
