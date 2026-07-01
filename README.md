# San Diego Parking Meter Revenue Dashboard

Interactive Power BI dashboard analyzing daily parking meter revenue across
San Diego, built on public transaction and location data from the City of
San Diego Open Data Portal. The project covers the full workflow from raw
data cleaning through an interactive reporting layer.

## What This Answers

- Which zones/areas generate the most parking revenue?
- How does revenue shift by season and day of week?
- Where geographically is parking demand concentrated?
- How has revenue trended year over year (2023–2026)?

## How It's Built

Data was pulled from two City of San Diego datasets — daily meter
transactions and meter locations. Each year's transaction file (2023–2026)
was loaded, cleaned, and typed individually in Power Query, then appended
into a single fact table. That table was modeled in Power BI as a star
schema alongside location and date dimension tables. DAX measures handle
the year-over-year and trend calculations, and the final dashboard is
built around a map view, revenue rankings, and time-based trend charts.

## Tools

- Power BI Desktop (data modeling, DAX, visuals)
- Power Query / M (data cleaning and transformation)
- Git / GitHub

## Repo Contents

- `dashboard/` — the .pbix file
- `docs/` — data model diagram and data dictionary
- `screenshots/` — dashboard preview images
- `README.md`

## License

MIT

## About Me

Hi, I'm Lauren Rabin. I graduated from UC Santa Barbara in 2024 with a degree in Statistics and Data Science. Since then I've been working in healthcare where data is a big part of my day to day, and honestly it's the part I enjoy most. This project is my way of continuing to build on that and grow into a more technical data role.

Connect with me on [LinkedIn](https://www.linkedin.com/in/laurenrabin).
