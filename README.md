# EDA Lab + Homework — FAANG-Level Hands-On

**Goal:** Build strong intuition for Exploratory Data Analysis (EDA) as it’s used in real ML work: validating data assumptions, finding leakage, discovering slices, and making high-signal plots and summaries.

**Outcome:** Students can quickly diagnose dataset issues (missingness, outliers, imbalance, shift), produce defensible summary tables/plots, and articulate next modeling steps.

---

# How to Start

1. **Fork** this repository.
2. Open `eda_student_lab.ipynb` in **Google Colab** (or local Jupyter).
3. Complete all **TODO** sections.
4. **Restart runtime → Run All**.
5. Push changes and submit a **Pull Request**.

⚠️ Do **NOT** edit notebooks directly on GitHub.

---

## Lab Rules (FAANG Style)

- ✅ Always state the **data grain** (one row per what?)
- ✅ Check **missingness**, **duplicates**, **label imbalance**, and **outliers** early
- ✅ Separate **train/test thinking** even in EDA: avoid “peeking” at future data
- ✅ Produce 1–2 **high-signal plots** per question (avoid plot spam)
- ✅ Every claim should have a number/table/plot behind it

---

# Out of Scope

- Training a production-quality model
- Hyperparameter tuning

---

# Notebook Rules

- Do **NOT** rename the notebook
- Do **NOT** delete TODOs
- Do **NOT** hardcode outputs
- Notebook must run **top-to-bottom**

---

# Dataset

This lab uses a **small synthetic user + subscription dataset** embedded in the notebook.

## Why?

- Offline-first and runnable anywhere
- Still captures real EDA pitfalls: missing values, heavy tails, leakage-y columns, and slice performance issues

---

## Section 1 — Sanity Checks (Must Do)

### Task 1.1: Data grain + schema

- Identify the grain (one row per user?)
- Check dtypes and basic validity constraints

**Checkpoint Questions:**

- What would break if the grain is wrong?
- Which columns are categorical vs numerical vs time?

---

### Task 1.2: Missingness + duplicates

- Missingness table (% missing per column)
- Duplicate row checks (and duplicate key checks)

**FAANG Gotcha:**

- “No missing values” can still be wrong if missing is encoded as `"unknown"`, `-1`, empty string.

---

## Section 2 — Distribution + Outliers

### Task 2.1: Numeric distributions

- Summaries (mean/median/std/quantiles)
- Identify heavy tails / suspicious spikes

### Task 2.2: Outlier handling (EDA-only)

- Decide whether to clip/winsorize/log-transform (and justify)

**Interview Angle:**

- Outliers can be signal (fraud, whales) — don’t blindly delete.

---

## Section 3 — Target + Slices

### Task 3.1: Label imbalance

- Compute positive rate
- What metric would you use and why?

### Task 3.2: Slice analysis

- Compare churn rate across at least 3 slices (country, plan, tenure bucket)

**FAANG Gotcha:**

- Simpson’s paradox: slice trends can flip when aggregating.

---

## Section 4 — Leakage + Time

### Task 4.1: Find a leakage-prone feature

- Identify at least one column that would not exist at prediction time
- Explain how it inflates offline metrics

---

## Section 5 — Homework (Write-up)

In 10–15 bullets:

- Top 5 data issues/risks you found
- Top 3 features you would create next (and why)
- What would you do before training any model?

---

## Submission Expectations

Students must submit:

- Completed notebook (runs top-to-bottom)
- Answers to all **Checkpoint/Explain** prompts
- A short “EDA report” section (bullet list)

---

## FAANG Interview Evaluation Rubric

| Skill                           | Evaluated |
|--------------------------------|-----------|
| Data sanity checks + grain      | ✅        |
| Missingness/duplicates/outliers | ✅        |
| Slice analysis                  | ✅        |
| Leakage awareness               | ✅        |
| Communication clarity           | ✅        |

---

## Stretch Problems (Optional)

- Implement a simple drift check between two time windows
- Add a bootstrapped confidence interval for churn rate per slice
- Create a single-page “EDA summary table” suitable for a design doc
