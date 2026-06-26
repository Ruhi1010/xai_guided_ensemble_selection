# xai_guided_ensemble_selection

# Proposed Framework: Explanation Guided Ensemble Selection (XGES)

## Input
- Dataset `D`
- Model set `M`
- Sampling size `s`
- Number of selected models `k`

## Output
- Optimized stacked ensemble `E`

---

## Step 1: Data Preparation

- Load dataset `D`
- Split dataset into Train and Test using stratified sampling
- Apply SMOTE to training data
- Scale features using standardization

---

## Step 2: Train Candidate Models

For each model `m` in `M`:

- Train `m` using balanced training data
- Store trained model

---

## Step 3: Performance Evaluation

For each trained model `m`:

- Predict probabilities on test set
- Compute AUPRC score
- Save performance score

---

## Step 4: Create Stratified Subset

- Sample subset `S` from training data
- Maintain class distribution

---

## Step 5: Generate Explanations

For each model `m`:

- Apply SHAP on subset `S`
- Extract feature importance vector

---

## Step 6: Compute Stability

For each model `m`:

- Perform k-fold analysis on subset `S`
- Measure variance of feature importance
- Compute stability score

---

## Step 7: Compute Diversity

For each pair of models `(m_i, m_j)`:

- Compare explanation vectors
- Calculate similarity score
- Convert to diversity score

---

## Step 8: Model Ranking

For each model `m`:

```text
Score(m) =
    α × Performance
  + β × Stability
  + γ × Diversity
```

---

## Step 9: Model Selection

- Rank models by `Score`
- Select top-`k` models

---

## Step 10: Stacking

- Train selected base models
- Generate predictions
- Train meta-learner using predictions

---

## Step 11: Final Evaluation

- Evaluate ensemble on test data

---

## Return

- Ensemble `E`