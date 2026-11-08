# Food-Dataset-by-Yumul-JGK

# Rule-based AI for identifying ultra-processed foods
CPU5006 Artificial Intelligence, Assessment S1. John Gareth Kyle C. Yumul

## Research question
To what extent can nutrient-based rule systems identify ultra-processed foods (NOVA group 4) in Open Food Facts data, and does a forward-chaining engine with derived facts outperform a flat threshold lookup?

## What is here
- `notebooks/A1.ipynb`: all code, in order. Cells 1-4 load, clean and split the data and run Algorithm A. Cells 5-8 are development-set exploration. Cell 9 builds Algorithm B. Cell 10 is the final test-set evaluation (run once). Cell 11 checks that B equals a flat rewrite of its rules.
- `data/sample_openfoodfacts.csv`: a sample of the data. Full file: https://www.kaggle.com/datasets/kanchana1990/global-food-nutrition-database10k-products

## Method in brief
- Data: Open Food Facts snapshot, 9,804 products, 8,366 after cleaning; 70/30 stratified split, seed 42 (5,856 development, 2,510 test).
- Algorithm A: UK front-of-pack cut-offs (Department of Health, 2016); predicts ultra-processed if at least k = 3 nutrients are red.
- Algorithm B: forward-chaining engine that excludes ingredient-like and all-green products.
- No machine learning model is trained. scikit-learn is used only for the split and the metrics.

## Test-set results
| | Accuracy | Precision | Recall | F1 | MCC |
|---|---|---|---|---|---|
| Baseline (all ultra-processed) | 0.594 | 0.594 | 1.000 | 0.746 | 0.000 |
| Algorithm A (k = 3) | 0.485 | 0.816 | 0.172 | 0.284 | 0.171 |
| Algorithm B | 0.642 | 0.643 | 0.895 | 0.748 | 0.217 |

## How to run
Open the notebook in Google Colab, run Cell 1 and upload the CSV, then run the cells in order. Results in the paper come from the full file.

## Data and licence
Data from Open Food Facts, released under the Open Database Licence (ODbL); attribution: Open Food Facts contributors. https://www.kaggle.com/datasets/kanchana1990/global-food-nutrition-database10k-products and https://opendatacommons.org/licenses/dbcl/1-0/

## AI assistance
Code was written with assistance from Claude (Anthropic) and reviewed by the author; this is noted in code comments.
