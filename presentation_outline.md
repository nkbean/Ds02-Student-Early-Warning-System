# Demo-day slides outline (ds-02-student-early-warning)
Make `reports/presentation.pdf` from this outline **after** running the notebook (charts are in `reports/figures/`).

| Slide | Title | Content |
|---|---|---|
| 1 | The question | Academic office wants to flag likely failures right after the midterm; positive class = fail; metric = recall. |
| 2 | The data | 500 students × 10 columns; biggest problem fixed: FinalScore leakage (07_leakage.png); ParentEducation 25% missing → "Unknown". |
| 3 | Key insights | 05_midterm.png, 02_attendance.png: one sentence each. |
| 4 | The model | Baseline "everyone fails" vs tuned decision tree (08_tuning.png); why a tree: rules the office can read. |
| 5 | Results | Recall __ for at-risk; confusion matrix 09_confusion_matrix.png explained as students caught / missed. |
| 6 | Recommendation | 3 warning-sign rules from 10_tree.png; run after every midterm; limits. |
