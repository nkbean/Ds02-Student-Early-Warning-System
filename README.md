# Student Early-Warning System

**Team:** _add names_, _add names_, _add names_
**Brief:** DS-02 (Intermediate)  ·  **Dataset:** Course dataset `student_performance.csv`, 500 students × 10 columns

## The question
A school's academic office wants to flag students likely to fail the final exam right after the midterm. **Using only information available right after the midterm, which students are at risk of failing, and what are the warning signs?** Target: `Result` (positive class = **at-risk / fail**). Success metric: **recall for at-risk students**, because missing a failing student costs far more than giving extra help to one who would pass.

## Key results
- **Leakage found:** Result = FinalScore ≥ 50 (__% match), so FinalScore was removed _✍️ fill in after running the notebook_
- Baseline "everyone fails": accuracy __, recall 1.00 but useless for targeting
- Decision tree (depth __): recall __, precision __, F1 __
- Three warning signs: __, __, __


## Approach
1. **Cleaning:** ParentEducation (126 missing, 25%) kept as an "Unknown" category; StudyHours (18) and Attendance (28) filled with the training median inside the pipeline; text columns one-hot encoded; stratified split for the imbalanced classes.
2. **EDA:** 6 charts (class balance, attendance, study hours, internet, midterm, parental education) plus the leakage chart, each with a written insight.
3. **Model:** stratified 80/20 split with `random_state=42`; baseline = predict everyone fails; decision tree tuned on max_depth 2–8 by CV F1; confusion matrix, precision/recall/F1, depth-3 tree turned into warning-sign rules; Logistic Regression and class_weight='balanced' as stretch goals.

## How to run
```bash
pip install -r requirements.txt
jupyter notebook notebooks/analysis.ipynb
```
Open `notebooks/analysis.ipynb` and choose **Run All** (Kernel → Restart & Run All). The notebook reads `data/student_performance.csv` and saves the charts to `reports/figures/`.

> ⚠️ Put the course file in `data/` before running (it is not included yet).

**Google Colab:** open the notebook in Colab and choose Runtime → Run all; a **Choose Files** button appears, so upload `data/student_performance.csv`.

## Repository structure
```
ds-02-student-early-warning/
├── README.md
├── data/
│   └── student_performance.csv
├── notebooks/
│   └── analysis.ipynb      # full notebook, outputs visible
├── reports/
│   ├── figures/            # key charts saved with plt.savefig()
│   └── presentation.pdf    # demo-day slides
└── requirements.txt
```

## Limitations
- 500 students from one course dataset.
- Study hours are self-reported; 25% of parental education is unknown.
- A flag is a prompt for a conversation with the student, not a label.

## AI usage
Claude (Anthropic) was used as an assistant to draft notebook code, chart code and documentation text, and to suggest checks (for example data-quality and leakage checks). Every team member re-ran the notebook, checked each result against the outputs, and can explain every cell and decision in their own words. The team is responsible for the final content.
