# CPE_Project_BRQ — Thailand Road Accident Analysis (2019–2022)

## Project summary

This project analyzes 81,735 road accident records in Thailand (2019–2022) to identify
the main factors associated with accident severity and to predict it using machine
learning. We engineered a 3-class target :  Fatal, Injury, and Property Damage
Only, from raw fatality/injury counts, and trained three classification models
(Logistic Regression, Decision Tree, Random Forest) to predict severity from contextual
and environmental features (vehicle type, weather, road type, time of day, province).
The goal is to surface actionable patterns that could support road safety policy and
awareness in Thailand.

---

## Group

| | |
|---|---|
| **Group name** | BRQ |
| **Members** | Baptiste LORTON, Romain BARDET, Quentin COUPÉ |
| **Course** | CPE393 — Introduction to Data Science with Python |
| **Semester** | Summer 2026 |
| **Institution** | King Mongkut's University of Technology Thonburi (KMUTT) |
---

## Team contribution

| Member | Code | Report sections | Slides | Oral |
|---|---|---|---|---|
| Baptiste LORTON | Data quality, cleaning, target engineering, correlation heatmap | 2, 3, 9 | 3, 4, 5, 14 | Introduction + data + Responsible AI |
| Romain BARDET | EDA visualisations, geospatial map, feature engineering | 4, 5 | 6, 7, 8, 9 | EDA + Feature Engineering |
| Quentin COUPÉ | Train-test split, ML pipelines, metrics, confusion matrix, feature importances | 6, 7 | 10, 11, 12, 13 | Models + Results + Evaluation |

---

## Dataset

| | |
|---|---|
| **Source** | Kaggle "Thailand Road Accident (2019–2022)" |
| **Original provider** | Office of the Permanent Secretary, Ministry of Transport, Thailand |
| **Size** | 81,735 rows × 18 columns |
| **Format** | CSV |
| **Download link** | See `data_link.txt` |

---

## Repository structure

```
CPE_Project_BRQ/
├── README.md                          # This file
├── project_notebook.ipynb             # Main notebook
├── project_summary.pdf                # Written report
├── presentation_slides.pptx           # Presentation slides
├── requirements.txt                   # Python dependencies
├── data_link.txt                      # Dataset download link and instructions
└── data/
    └── thai_road_accident_2019_2022_1_.csv   # Dataset
```

---

## How to run

### Option A — Google Colab (recommended)

1. Open [Google Colab](https://colab.research.google.com)
2. Upload `project_notebook.ipynb` via File → Upload notebook
3. Upload `thai_road_accident_2019_2022_1_.csv` to the Colab session storage
4. Run all cells in order via Runtime → Run all


### Option B — Local Jupyter

1. Clone this repository:
```bash
git clone <repository URL>
cd FinalProjetDataScience
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Place the dataset CSV in the same folder as the notebook, then launch:
```bash
jupyter notebook project_notebook.ipynb
```

4. Run all cells in order (Kernel → Restart & Run All).

> The notebook is fully reproducible, all models use `random_state=42`.

---

## Main results

| Model | Accuracy | Precision (macro) | Recall (macro) | F1 (macro) |
|---|---|---|---|---|
| Logistic Regression | 0.586 | 0.568 | 0.473 | 0.473 |
| Decision Tree | 0.582 | 0.572 | 0.490 | 0.494 |
| Random Forest | 0.595 | 0.604 | 0.476 | 0.472 |

- Random Forest achieved the best overall accuracy and macro-precision.
- Decision Tree achieved the best macro-recall and macro-F1.
- All models struggle to detect the Fatal class (recall 9–19%), this reflects the
  difficulty of predicting rare, severe outcomes from contextual features alone, and is
  discussed honestly in Section 9 (Responsible AI) of the report.

---

## Key limitations

- `report_datetime` is unreliable (59% of reports filed >30 days after the incident)
  and was excluded from all temporal analysis.
- `presumed_cause` is dominated by "speeding" (~74%), likely a reporting artefact, and
  was excluded from the model to avoid reinforcing this bias.
- Reporting coverage may not be uniform across agencies, provinces, or years.
- The model is intended for descriptive/policy-insight purposes only, not for
  real-time triage or individual-level prediction.

---

## Required libraries

See `requirements.txt` for full details. Main dependencies:

```
pandas >= 2.0
numpy >= 1.24
matplotlib >= 3.7
seaborn >= 0.12
scikit-learn >= 1.3
jupyter >= 1.0
```
