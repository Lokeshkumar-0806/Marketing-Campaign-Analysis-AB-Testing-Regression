# Marketing Campaign Analysis | A/B Testing & Regression

## Business problem
Compare Facebook Ads and Google Ads (AdWords) to identify which channel generates more conversions and inform marketing budget allocation.

## Dataset
365 matched daily observations, 17 columns, January–December 2025, with no missing values. The supplied CSV includes campaign names, views, clicks, conversions, advertising costs, CTR, conversion rate and CPC. The filename contains 2026, but the recorded dates are in 2025. Dataset provenance and redistribution permissions have not been established.

## Tools
Python, Pandas, NumPy, Matplotlib, Seaborn, SciPy, scikit-learn and Jupyter Notebook.

## Methodology
1. Inspect data types, missing values and descriptive statistics; parse dates.
2. Compare campaign visibility, engagement and conversion distributions.
3. Group daily conversions into performance tiers and visualize their frequencies.
4. Calculate Pearson correlations between clicks and conversions.
5. Apply a paired t-test to matched daily conversion counts at a 5% significance level.
6. Fit a simple linear regression model to estimate Facebook conversions from clicks.

## Key findings
| Daily metric | Facebook | Google Ads |
|---|---:|---:|
| Mean views | 2,364.04 | 4,793.39 |
| Mean clicks | 43.62 | 59.37 |
| Mean conversions | 11.25 | 5.59 |
| Click–conversion correlation | 0.91 | 0.56 |

Facebook generated approximately twice as many daily conversions despite lower traffic volume.

## Hypothesis testing
- H0: Mean Facebook conversions are less than or equal to mean Google Ads conversions.
- H1: Mean Facebook conversions are greater than mean Google Ads conversions.
- Paired t-statistic: 34.5309.
- Reported two-sided p-value: 6.819677418824742e-117.
- Significance level: 0.05.

The positive statistic and extremely small p-value support higher average Facebook conversions. The notebook uses a two-sided test by default despite stating a directional hypothesis; a one-sided paired test would align with H1. This is a comparison of historical paired observations, not evidence of a randomized controlled A/B experiment.

## Linear regression
| Metric | Result |
|---|---:|
| R² (in-sample) | 0.8222 |
| Mean squared error | 1.38 |
| Expected conversions at 50 clicks | 12.71 |
| Expected conversions at 80 clicks | 19.55 |

R² represents explained variance, not prediction accuracy. The model is evaluated on training data, so out-of-sample performance remains unverified.

## Business recommendations
- Prioritize Facebook for further controlled budget-allocation experiments.
- Investigate Google Ads targeting and landing-page performance.
- Validate cost per acquisition and return on ad spend before reallocating budget; conversion counts alone do not establish profitability.
- Use regression estimates for preliminary planning, then validate on held-out data.

## Repository structure
```text
Marketing-Campaign-Analysis-AB-Testing-Regression/
├── Marketing-Campaign-Analysis-ABTesting-Regression26.ipynb
├── marketing_campaign_2026.csv
├── requirements.txt
└── README.md
```

## Run locally
```bash
pip install -r requirements.txt
jupyter notebook
```
Open the notebook from the repository root and run its cells in order. The original notebook references `warnings` without importing it; add `import warnings` before the filter call if running the original version.

## Limitations
The original notebook contains inconsistent narrative figures (including the dataset year and R²); this README uses the CSV dates and recorded numerical outputs. Historical observations may be affected by confounding and temporal dependence. CPA and ROI comparisons, randomized experiments and holdout validation are recommended extensions rather than completed analyses.
