The Effect of Coreset on Demographic Bias

Introduction:
This project investigates whether coreset-based data selection can reduce demographic bias in text classification tasks without sacrificing model performance. It evaluates multiple transformer models across three datasets with demographic annotations.

Overview:
Performance and fairness of Baseline Models (BM) — trained on the full dataset — are compared with coreset-trained models that use only 25% of the data. Both approaches are evaluated across demographic splits (whole/males/females for PAN16 and BIOS, and whole/AA/white for FDCL18).

- Active Learning (AL): Selects high-uncertainty (entropy-based) samples.
- K-Center Greedy (KCG): Maximizes diversity by selecting distant samples in embedding space.
- K-Means: Selects data points closest to cluster centroids.

Models Used:
- BERT
- RoBERTa
- DistilRoBERTa

Datasets:
- PAN16: Binary mention detection, annotated with gender (Male/Female).
- FDCL18: Tweet classification (4 labels), annotated with dialect (White/African-American).
- BIOS: Profession classification (28 labels), annotated with gender.

Each dataset was evaluated in three configurations:
- Whole data
- Demographic-specific data (e.g., only Female or Male subsets for PAN16/BIOS, or AA/White for FDCL18)

Methodology:
Accuracy Gap Analysis, where accuracy gaps between demographic groups are analyzed based on specific train-test configurations.

Training-Testing Configurations:
Fairness and generalization are evaluated by training and testing across various demographic splits:

PAN16 & BIOS (Gender-Based Splits):

Training    | Test
------------|-----------
whole       | whole
whole       | males
whole       | females
males       | whole
males       | males
males       | females
females     | whole
females     | males
females     | females

FDCL18 (Dialect-Based Splits):

Training    | Test
------------|-----------
whole       | whole
whole       | white
whole       | AA
white       | whole
white       | white
white       | AA
AA          | whole
AA          | white
AA          | AA


Focused Comparisons:
PAN16 & BIOS (Gender-Based Bias Analysis):
- males-males vs females-males
- females-females vs males-females
Note: These comparisons are prioritized for fairness analysis, although other configurations are also evaluated for completeness.

FDCL18 (Dialect-Based Bias Analysis):
- white-white vs AA-white
- AA-AA vs white-AA
Note: These comparisons are prioritized for fairness analysis, although other configurations are also evaluated for completeness.