# Marathon Training Analysis

Exploratory analysis of Strava running activities comparing my 2024 and 2025 marathon preparation.

## Questions

- How did weekly training mileage differ between the two years?
- How does the comparison change when weeks are aligned to race day?
- What can pace and average heart rate add to the picture?

## Approach

The [analysis notebook](notebooks/strava_notebook.ipynb) filters running activities, selects relevant fields, parses dates, converts distance from kilometers to miles and moving time from seconds to minutes, and derives pace in minutes per mile. It aggregates mileage, pace, and heart rate by week and plots training volume against the two race dates.

**Stack:** Python, pandas, NumPy, Matplotlib, Seaborn, Jupyter.

## Project status

Work in progress. The notebook contains saved exploratory outputs, but has a malformed run-filter expression and cells that reference variables before they are defined. It does not yet run cleanly from top to bottom. Predictive modeling and conclusions about race performance have not been established.

## Data and setup

The notebook expects a Strava activity export at `data/activities.csv`, relative to the repository root. That file is not included in the repository; viewing the saved notebook outputs does not require it.

Required columns: `Activity Type`, `Distance`, `Moving Time`, `Average Heart Rate`, `Activity Date`, `Elevation Gain`, and `Activity Description`. The current calculations assume distance in kilometers and moving time in seconds; verify these units for any replacement export.

```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install jupyter pandas numpy matplotlib seaborn
jupyter notebook notebooks/strava_notebook.ipynb
```

Execution currently requires the notebook fixes described above and a compatible input CSV.

## Next improvements

- Repair cell execution order and the run filter, then verify a fresh-kernel run.
- Validate missing values, zero-distance activities, and input units.
- Make race-relative week alignment and the training window consistent across comparisons.
- Distinguish mean activity pace from distance-weighted pace.
- Add a small synthetic dataset and reusable transformation functions for reproducibility.
- Summarize findings with explicit limits: a single runner's observational data cannot establish why race outcomes differed.
