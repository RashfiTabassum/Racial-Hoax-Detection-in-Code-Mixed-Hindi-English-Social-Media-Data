# Racial Hoax Detection in Code-Mixed Hindi-English Social Media Data

An approach to the shared task **"Detecting Racial Hoaxes in Code-Mixed Hindi-English
Social Media Data"** at **LT-EDI@LDK 2025** (Fifth Workshop on Language Technology
for Equality, Diversity and Inclusion, co-located with the 5th Conference on
Language, Data and Knowledge), organized by DravidianLangTech.

- Competition page: https://codalab.lisn.upsaclay.fr/competitions/21885

## Task
Binary classification of code-mixed Hindi-English social media comments as racial
hoax or not. Racial hoaxes falsely blame a person or community for a crime or
incident because of their race, religion or background. Systems are ranked by
**macro-F1**.

## Dataset
HoaxMixPlus: 5,105 code-mixed Hindi-English YouTube comments.
Train: 3,060 | Validation: 1,021 | Test: labels withheld.
The classes are imbalanced (about 24% minority class).

## Approach
- Fine-tuned `google/muril-base-cased` (MuRIL) and `ai4bharat/indic-bert` (IndicBERT)
  (5 epochs, learning rate 1e-5, batch size 4, max length 128)
- Minority-class oversampling to handle class imbalance
- Ensembling: logit averaging and F1-weighted averaging

## Results (validation set)
| Model              | Accuracy | Macro-F1 |
|--------------------|----------|----------|
| MuRIL              | 0.785    | 0.700    |
| IndicBERT          | 0.777    | 0.690    |
| Ensemble (average) | 0.792    | 0.713    |
| Weighted ensemble  | 0.792    | 0.713    |
