# draft_options_ssac
# Draft Picks as Options Contracts

Data pipeline and analysis for the paper *"Draft Picks as Derivative Contracts: Applying Options Pricing Theory to NFL Draft Pick Valuation and Trade Analysis"* (Matt Burkett, Ph.D. — UVA Systems Engineering).

The pipeline runs end to end: data acquisition → Black-Scholes pricing → Greeks → mispricing analysis → publication figures.

## Data Sources

- nflverse `draft_picks.csv` — pick history 1980–2024
- nflverse `rosters.csv` — career AV per player, 2006–2019
- nflverse `draft_values.csv` — Johnson, Hill, Stuart, OTC, PFF charts
- Federal Reserve H.15 — 10-yr Treasury annual averages (hardcoded)
- NFL CBA / public records — salary cap by year (hardcoded)
- OverTheCap.com — rookie slot values, modeled from public anchor points

nflverse data is downloaded automatically on first run; an internet connection is required.

## Requirements

- Python 3.9+
- Packages listed in `requirements.txt` (pandas, numpy, requests, matplotlib, seaborn, scipy, statsmodels)

## Setup

```bash
git clone <repo-url>
cd <repo-name>
chmod +x setup.sh
./setup.sh
source draft_options/bin/activate
```

`setup.sh` creates a virtual environment named `draft_options` and installs all dependencies. It is safe to re-run.

<details>
<summary>Manual setup (or Windows)</summary>

```bash
python3 -m venv draft_options
source draft_options/bin/activate        # Windows: draft_options\Scripts\activate
pip install -r requirements.txt
```

</details>

## Running the Pipeline

```bash
python draft_options_pipeline.py
```

Outputs:

- `data/` — downloaded and processed datasets
- `figures/` — publication-quality figures (PNG, 150 dpi)

## Repository Structure

```
├── draft_options_pipeline.py   # full pipeline
├── requirements.txt            # Python dependencies
├── setup.sh                    # environment setup script
├── data/                       # created at runtime
└── figures/                    # created at runtime
```
