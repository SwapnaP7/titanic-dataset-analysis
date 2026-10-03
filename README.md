# Titanic Dataset Analysis

## Overview

Exploratory data analysis (EDA) of the Kaggle Titanic training dataset (891 passengers). The project checks data quality, handles missing values and explores how survival relates to sex, passenger class, age, family size and fare. It uses Python, pandas and Matplotlib in one Jupyter notebook: [`notebooks/titanic_analysis.ipynb`](notebooks/titanic_analysis.ipynb). No machine-learning model is built.

## Dataset

- **File:** `data/train.csv` (Kaggle's Titanic training set, unmodified)
- **Size:** 891 rows, 12 columns
- **Columns:** `PassengerId`, `Survived`, `Pclass`, `Name`, `Sex`, `Age`, `SibSp`, `Parch`, `Ticket`, `Fare`, `Cabin`, `Embarked`
- **Target:** `Survived` (0 = did not survive, 1 = survived), the recorded outcome in the file
- The file is not a complete passenger list of the ship.

## Data Quality

- No duplicate rows; `PassengerId` is unique; `Survived`, `Pclass`, `Sex` and `Embarked` contain only the expected values.
- **Missing values:**
  - `Cabin`: 687 missing (77.1%), too sparse, so it is dropped.
  - `Age`: 177 missing (19.9%), not imputed; age analysis uses the 714 known ages.
  - `Embarked`: 2 missing; the column is not used.
- `Name` and `Ticket` are not analysed and are dropped.
- 15 passengers have a fare of 0; this cannot be verified, so it is kept as recorded.

## Analysis Performed

- Overall survival distribution
- Survival by sex
- Survival by passenger class (also split by sex)
- Age analysis (survivors vs non-survivors and survival by age group)
- Family-size analysis (`FamilySize = SibSp + Parch + 1`)
- Fare analysis (fare by class and survival by fare quartile)

## Key Findings

These are observed rates in this dataset; they do not establish causes.

- 342 of 891 passengers (38.4%) survived.
- 74.2% of women survived versus 18.9% of men.
- Survival was 63.0% in 1st class, 47.3% in 2nd and 24.2% in 3rd; 1st class is higher than 3rd class for both women and men.
- Children under 16 had the highest age-group survival rate (59.0%).
- Passengers travelling alone survived at 30.4%, family sizes 2 to 4 at 55.3% to 72.4%; larger families are too small to interpret reliably.
- Survival rises with fare quartile (19.7% to 58.1%), but fare is closely tied to passenger class.

## Visualizations

- Survival distribution
- Survival rate by sex
- Survival rate by passenger class
- Age distribution and survival rate by age group
- Survival rate by family size

## Technologies

Python, pandas, Matplotlib, Jupyter Notebook.

## Project Structure

```text
titanic-dataset-analysis/
├── README.md
├── requirements.txt
├── .gitignore
├── data/
│   └── train.csv
└── notebooks/
    └── titanic_analysis.ipynb
```

## How to Run

```bash
git clone https://github.com/<your-username>/titanic-dataset-analysis.git
cd titanic-dataset-analysis
python -m venv .venv
```

Activate the environment.

Linux/macOS:

```bash
source .venv/bin/activate
```

Windows:

```powershell
.venv\Scripts\activate
```

Then:

```bash
pip install -r requirements.txt
jupyter notebook notebooks/titanic_analysis.ipynb
```

## Dataset Source

Kaggle, *Titanic - Machine Learning from Disaster*, `train.csv`: https://www.kaggle.com/c/titanic/data

The copy in `data/train.csv` was obtained from public GitHub mirrors of the Kaggle file (three independent copies had identical contents) rather than downloaded from Kaggle directly. Kaggle competition data is subject to Kaggle's terms; it is included here for educational reproducibility.
