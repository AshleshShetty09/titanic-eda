# Titanic EDA — Who Survived, and Why?

A reproducible exploratory data analysis (EDA) of the classic Titanic
passenger manifest. No predictive model here — the point is clean,
well-reasoned handling of a small but genuinely messy dataset (missing
`Age`, a mostly-empty `Cabin` column, mixed numeric/categorical types),
plus a short, readable set of findings.

## What's here

```
titanic-eda/
├── data/
│   └── titanic.csv           # raw dataset (891 passengers, 12 columns)
├── notebooks/
│   └── titanic_eda.ipynb     # the analysis
├── requirements.txt
└── README.md
```

## Running it

```bash
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook notebooks/titanic_eda.ipynb
```

Then **Kernel → Restart & Run All**. Everything — including loading the
CSV from the relative path `data/titanic.csv` — runs top to bottom with no
manual steps and no absolute paths.

## What the notebook does

1. **Load** — one cell, relative path, no config needed.
2. **Inspect** — shape, dtypes, missing-value counts before any changes.
3. **Clean** — each transformation (imputing `Age` by class/sex median,
   collapsing `Cabin` into a `has_cabin` flag, filling the 2 missing
   `Embarked` values, dropping identifier columns) is commented with the
   reasoning behind it, not just the mechanics.
4. **Explore** — survival broken down by sex, class, age, fare, family
   size, and port of embarkation, plus a correlation matrix.
5. **Findings** — a ~150-word summary of who survived and why, and what
   to try next with more time (title extraction from names, interaction
   effects, a baseline classifier).

## Data source

The dataset is the canonical Titanic passenger list as distributed by the
[pandas project](https://github.com/pandas-dev/pandas/blob/master/doc/data/titanic.csv).
A copy is checked into `data/titanic.csv` so the notebook runs offline and
reproducibly for anyone who clones this repo.
