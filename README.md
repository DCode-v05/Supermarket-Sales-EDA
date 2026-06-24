# Supermarket Sales — Exploratory Data Analysis

**A clean, notebook-based walk through 1,000 supermarket transactions: cleaning, profiling, and visualizing what actually drives cost and gross income.**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white) ![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=flat&logo=jupyter&logoColor=white) ![pandas](https://img.shields.io/badge/pandas-150458?style=flat&logo=pandas&logoColor=white) ![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat&logo=numpy&logoColor=white) ![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=flat&logo=python&logoColor=white)

## Overview

This is an exploratory data analysis of the well-known **Supermarket Sales** dataset — 1,000 transactions from three branches of a retail chain, recorded over three months in 2019. The notebook loads the raw CSV, checks it for nulls and dtype issues, does light cleaning, splits the numeric and categorical columns, and then plots two grids of bar charts that break down **cost of goods sold (COGS)** and **gross income** across the main categorical dimensions (branch, city, product line, payment method, customer type, quantity).

I built this as Task-1 of the iQube student internship, where it was the first assignment in a graded ML/DS track (EDA → classification → regression → deep learning). The goal was analysis and visualization, not modeling, so there's no train/test split or predictor here — it's a focused, reproducible EDA with a formal PDF report as the deliverable.

## Key Features

- Loads the 1,000-row, 17-column `supermarket_sales.csv` and inspects it with `head()`, `info()`, and a full `describe(include="all").T` profile of every column.
- Null check across the whole frame (`isnull()`) followed by a `dropna()` pass — the dataset is already complete, so this is a defensive cleaning step.
- Light data normalization: rounds `Total`, `gross margin percentage`, and `gross income` for readability, and recodes the `Gender` column from `Female`/`Male` to `F`/`M`.
- Separates the frame into categorical (`select_dtypes(include=["object"])`) and numeric (`int64`/`float64`) subsets so each gets analyzed on its own terms.
- Two 3×2 Matplotlib figure grids (6 subplots each), one for COGS and one for gross income, each broken down by Branch, Quantity, Product line, City, Payment, and Customer type.
- Exports the two figures to disk as `EDA1.png` (COGS) and `EDA2.png` (gross income) so the visuals stand alone outside the notebook.

## How It Works

The whole analysis lives in one notebook, `EDA of Supermarket Sales.ipynb`, run top to bottom in 11 cells. It splits into four stages.

### 1. Load and inspect

The notebook reads the CSV into a pandas DataFrame and runs the standard first-look trio: `head()` to eyeball rows, `info()` to confirm 1,000 non-null entries across 17 columns and their dtypes, and `isnull()` to scan for missing values. The columns cover the full transaction: `Invoice ID`, `Branch`, `City`, `Customer type`, `Gender`, `Product line`, `Unit price`, `Quantity`, `Tax 5%`, `Total`, `Date`, `Time`, `Payment`, `cogs`, `gross margin percentage`, `gross income`, and `Rating`.

### 2. Clean and normalize

A `dropna()` removes any null rows (none here, but it keeps the pipeline safe). Then a few columns get tidied: monetary fields are rounded, and `Gender` is collapsed to single-letter codes so labels read cleaner on the plots. This is deliberate, minimal preprocessing — nothing that changes the meaning of the data.

### 3. Profile and split

`describe(include="all").T` produces a transposed summary that covers both numeric stats (mean, std, quartiles) and categorical frequencies (unique counts, top value, freq) in one table — for example, Branch `A` is the most common with 340 of 1,000 records. The frame is then split by dtype into `marstr` (the object/categorical columns) and `marnum` (the numeric columns) for targeted analysis.

### 4. Visualize COGS and gross income

The two plotting cells each build a `plt.subplots(3, 2, figsize=(30, 20))` grid with a bold figure title, then draw six bar charts:

- **Cost of goods sold** vs Branch, Quantity, Product line, City, Payment, and Customer type → saved as `EDA1.png`.
- **Gross income** vs the same six categories → saved as `EDA2.png`.

Each subplot gets its own color, axis labels, and title, and the finished figures are written out with `fig.savefig(...)`. The result is a single-glance comparison of how cost and margin distribute across every categorical cut of the business.

## Results / Highlights

- **Dataset:** 1,000 transactions, 17 columns, zero missing values after the cleaning pass.
- **Coverage:** 3 branches (A/B/C), 3 cities (Yangon, Naypyitaw, Mandalay), 6 product lines, 3 payment methods (Ewallet, Cash, Credit card), and two customer types (Member/Normal).
- **Output:** 12 bar charts across two 3×2 grids (3000×2000 px each), exported as `EDA1.png` and `EDA2.png`.
- **Deliverable:** a formal EDA write-up was submitted alongside the notebook for the internship task.

## Tech Stack

- **Language:** Python
- **Libraries:** pandas, NumPy, Matplotlib
- **Environment:** Jupyter Notebook

## Getting Started

### Prerequisites

- Python 3.x
- Jupyter Notebook (or JupyterLab)

### Installation

```bash
git clone https://github.com/DCode-v05/Supermarket-Sales.git
cd Supermarket-Sales
pip install pandas numpy matplotlib jupyter
```

### Running

```bash
jupyter notebook "EDA of Supermarket Sales.ipynb"
```

## Usage

Open the notebook and run the cells in order from top to bottom. Each cell is self-contained and commented, so you can follow the flow from raw load through to the saved figures. The dataset (`supermarket_sales.csv`) ships with the repo, so nothing needs to be downloaded. Running the last two cells regenerates `EDA1.png` and `EDA2.png` in the project root.

> Note: the notebook reads the CSV via a relative path (`../EDA/supermarket_sales.csv`). If you run it from the repo root, point that `pd.read_csv(...)` call at `supermarket_sales.csv` instead.

## Project Structure

```
Supermarket-Sales/
├── EDA of Supermarket Sales.ipynb   # Main analysis notebook (11 cells)
├── supermarket_sales.csv            # Dataset — 1,000 rows × 17 columns
├── EDA1.png                         # COGS breakdown across 6 categories
├── EDA2.png                         # Gross-income breakdown across 6 categories
└── README.md                        # Project documentation
```

---

## Contact

<table>
  <tr><td><b>Portfolio:</b> <a href="https://www.denistan.me">Denistan</a></td><td><b>LinkedIn:</b> <a href="https://www.linkedin.com/in/denistanb">denistanb</a></td></tr>
  <tr><td><b>GitHub:</b> <a href="https://github.com/DCode-v05">DCode-v05</a></td><td><b>LeetCode:</b> <a href="https://leetcode.com/u/Denistan_B">Denistan_B</a></td></tr>
  <tr><td colspan="2" align="center"><b>Email:</b> <a href="mailto:denistanb05@gmail.com">denistanb05@gmail.com</a></td></tr>
</table>

Made with ❤️ by **Denistan B**
