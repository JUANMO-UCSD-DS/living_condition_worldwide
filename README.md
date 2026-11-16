# Living Conditions and Development (1960–2020)

This project is a static data-visualization dashboard built with D3 that explores how living conditions and development have changed across countries from 1960 to 2020.

The page combines five charts that examine:

- fertility rates
- internet access by income group
- electricity access by country
- population aging
- research and development spending as a share of GDP

## Project question

How have living conditions and development changed across countries from 1960 to 2020?



## Live project

This project is a client-side web app with no backend. It loads local CSV files from the `data/` directory and renders interactive charts in the browser using D3 v7.

## Project structure

```text
.
├── index.html                 # main page
├── css/
│   ├── aging.css
│   ├── electricity.css
│   ├── research.css
│   └── style.css
├── data/
│   ├── electricity_access.csv
│   ├── fertility_world.csv
│   ├── internet_income.csv
│   ├── population_aging.csv
│   └── research_development.csv
├── graphs/
│   ├── agingChart.js
│   ├── electricityChart.js
│   ├── fertilityChart.js
│   ├── internetChart.js
│   ├── main.js
│   └── researchChart.js
├── scripts/
│   └── prepare_data.py
├── README.md
└── .gitignore                # if present in your repo
```

## What is included

1. Fertility rate trend for the world (1960–2019)
2. Internet usage by income group (~2000 vs ~2019)
3. Electricity access by country (2000 vs 2019)
4. Population aging (1960–2020 snapshot comparisons)
5. Average research and development spending (% of GDP)

## Data source

The project uses World Bank indicator data assembled from the repository below:

- https://github.com/light-and-salt/World-Bank-Data-by-Indicators

The preprocessing script downloads and filters the relevant CSVs and saves the smaller, chart-ready files into `data/`.

## Run locally

Because browsers block `file://` requests for local CSVs, serve the project with a small local web server:

```bash
cd /path/to/UCSD_BANK_DATA
python3 -m http.server 8000
```

Then open:

```text
http://localhost:8000
```

## Regenerate the data

If you want to refresh the processed CSV files from the upstream World Bank data source:

```bash
python3 scripts/prepare_data.py
```

This script uses Python's built-in standard library only and prints which years and coverage are available for each dataset.

## Deploy to GitHub Pages

This site is static and compatible with GitHub Pages:

1. Push the repo to GitHub.
2. Open the repository settings.
3. Go to Pages.
4. Select a branch (for example `main` or `master`) and deploy from the root directory.

The project uses relative paths, so it works from the repo root or a docs folder as long as the paths remain relative.

## Notes on the data

- Fertility data uses the World Bank "World" series and covers most years from 1960 to 2019.
- Internet access data is grouped by income level and compares values near 2000 and 2019, using the closest available year within a small tolerance when needed.
- Electricity and aging data are filtered to valid country-level observations and grouped by the target comparison years.
- Research and development data is averaged across countries for each year to produce a broad trend line.

## Technical notes

- Built using plain HTML, CSS, JavaScript, and D3 v7
- No backend or server-side processing required
- Charts are responsive and redraw on window resize
- All visualization logic is in the JavaScript files under `graphs/`

## Future enhancements

Possible extensions include:

- interactive dropdown filters by country or region
- hover tooltips with precise values and labels
- more direct interactivity for the country-level maps and timeline charts
