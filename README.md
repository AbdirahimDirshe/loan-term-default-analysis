# Project Title

Loan Term Length and Default Behavior in SBA 7(a) Loans

## 1. Research Question

This project investigates whether loan term length is associated with default behavior in SBA 7(a) loans. Specifically, it examines whether short-term loans (less than 60 months) have different default rates compared to long-term loans (60 months or more). Understanding this relationship helps clarify how loan structure relates to observed default outcomes in this dataset.

## 2. Hypothesis

Long-term loans are defined as loans with terms of 60 months or more, while short-term loans are defined as loans with terms shorter than 60 months.

Null Hypothesis (H₀):
There is no difference in default rates between long-term and short-term loans.

Alternative Hypothesis (H₁):
Short-term loans have higher default rates than long-term loans.

## 3. Data Description

Describe your data source(s):

Data source:
U.S. Small Business Administration (SBA) 7(a) loan data, provided as two CSV files:

foia-7a-fy2010-fy2019-asof-250930.csv

foia-7a-fy2020-present-asof-250930.csv

The datasets were combined into a single DataFrame.

Unit of analysis:
Each observation represents one SBA 7(a) loan.

Key variables used in this project:

LoanStatus – loan outcome category

Default – binary indicator (1 = CHGOFF, 0 = PIF)

TerminMonths – loan term length in months

LoanTermGroup – categorical variable:

Short: term < 60 months

Long: term ≥ 60 months

GrossApproval – approved loan amount

## 4. Methods

Permutation Test

Test statistic:
Difference in default rates between loan term groups:

Default Rate
𝐿
𝑜
𝑛
𝑔
−
Default Rate
𝑆
ℎ
𝑜
𝑟
𝑡
Default Rate
Long
	​

−Default Rate
Short
	​


Null simulation:
Loan term group labels were randomly permuted across loans while keeping default outcomes fixed.

Number of permutations:
5,000

p-value:
Computed as the proportion of simulated differences at least as extreme as the observed difference.

Bootstrap Analysis

Bootstrap resampling was used to estimate uncertainty for metrics where the Central Limit Theorem does not apply.

Bootstrap metrics:

Median loan term

Difference in median loan term between:

Defaulted loans (CHGOFF)

Non-defaulted loans (PIF)

Resampling details:

Sampling with replacement

5,000 bootstrap resamples

95% percentile confidence intervals

Why CLT does not apply:
The median is not a mean-based statistic, and loan terms are highly skewed with many extreme values. Therefore, the sampling distribution of the median is not guaranteed to be approximately normal, even with a large sample size.

## 5. Results

Exploratory Data Analysis (EDA)

Short-term loans are more numerous than long-term loans.

Default rates differ substantially between loan term groups.

Loan term distributions are skewed and contain many outliers.

Permutation Test Results

The observed difference in default rates (Long − Short) is strongly negative.

The permutation p-value is approximately 0, indicating that the observed difference is extremely unlikely under the null hypothesis.

This provides strong evidence against H₀.

Bootstrap Results

The 95% bootstrap confidence interval for the difference in median loan term (defaulted − non-defaulted) is:

[
−
24
,
 
−
24
]
 months
[−24, −24] months

The interval does not include zero.

## 6. Uncertainty Estimation

Number of resamples: 5,000

Bootstrap distributions:
Highly concentrated due to the large sample size and discrete loan term values.

Interpretation:
Defaulted loans have a median loan term approximately 24 months shorter than non-defaulted loans, with high confidence.

The bootstrap results are consistent with the permutation test and reinforce the conclusion that loan term length is meaningfully associated with default behavior.

## 7. Limitations

This analysis relies on observational data, so the results reflect associations rather than causal relationships between loan term length and default behavior.
The definition of default is based only on available finalized loan status categories (CHGOFF vs PIF), and other outcomes were excluded.
Additionally, other borrower or loan characteristics that may influence default behavior were not included in the analysis, which may lead to unobserved confounding.

## 8. References

U.S. Small Business Administration, SBA 7(a) Loan Data (FOIA):
https://data.sba.gov/dataset/7-a-504-foia.

---
