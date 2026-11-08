# Supermarket Sales EDA

Exploratory data analysis of the Supermarket Sales dataset: 1,000 transactions from three branches (Yangon, Naypyitaw, Mandalay) over three months in 2019.

## What the notebook does

1. Loads `supermarket_sales.csv`, checks types and nulls, and drops any rows with missing values.
2. Rounds `Total`, `gross income` and `gross margin percentage` and shortens the gender labels to `F` and `M`.
3. Prints summary statistics and splits the columns into text and numeric.
4. Draws two grids of six bar charts each, for cost of goods sold (`cogs`) and for `gross income`, against branch, quantity, product line, city, payment method and customer type.

The two figures are in the repo as `EDA1.png` (cogs) and `EDA2.png` (gross income). The notebook only plots and draws no conclusions in text.

![COGS charts](EDA1.png)

![Gross income charts](EDA2.png)

## Running it

```bash
pip install pandas numpy matplotlib jupyter
jupyter notebook "EDA of Supermarket Sales.ipynb"
```

Start Jupyter from the repo root: the notebook reads `supermarket_sales.csv` from the current folder.
