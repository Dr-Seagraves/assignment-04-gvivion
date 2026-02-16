# Assignment 04 Interpretation Memo

**Student Name:** [Your Name]
**Date:** [Submission Date]
**Assignment:** REIT Annual Returns and Predictors (Simple Linear Regression)

---

## 1. Regression Overview

You estimated **three** simple OLS regressions of REIT *annual* returns on different predictors:

| Model | Y Variable | X Variable | Interpretation Focus |
|-------|------------|------------|----------------------|
| 1 | ret (annual) | div12m_me | Dividend yield |
| 2 | ret (annual) | prime_rate | Interest rate sensitivity |
| 3 | ret (annual) | ffo_at_reit | FFO to assets (fundamental performance) |

For each model, summarize the key results in the sections below.

---

## 2. Coefficient Comparison (All Three Regressions)

**Model 1: ret ~ div12m_me**
- Intercept (β₀): 0.1082 (SE: 0.006, p-value: 0.000)
- Slope (β₁): -0.0687 (SE: 0.032, p-value: 0.035)
- R²: 0.002 | N: 2527

**Model 2: ret ~ prime_rate**
- Intercept (β₀): 0.1998 (SE: 0.016, p-value: 0.000)
- Slope (β₁): -0.0194 (SE: 0.003, p-value: 0.000)
- R²: 0.016 | N: 2527

**Model 3: ret ~ ffo_at_reit**
- Intercept (β₀): 0.0973 (SE: 0.009, p-value: 0.000)
- Slope (β₁): 0.5770 (SE: 0.567, p-value: 0.309)
- R²: 0.000 | N: 2518

*Note: Model 3 may have fewer observations if ffo_at_reit has missing values; statsmodels drops those rows.*

---

## 3. Slope Interpretation (Economic Units)

**Dividend Yield (div12m_me):**
- A 1 percentage point increase in dividend yield (12-month dividends / market equity) is associated with a -0.000687 change in annual return.
- Higher dividend yield is associated with slightly lower returns, which could reflect that high yields often coincide with lower prices or higher perceived risk.

**Prime Loan Rate (prime_rate):**
- A 1 percentage point increase in the year-end prime rate is associated with a -0.000194 change in annual return.
- The evidence suggests REIT returns are negatively sensitive to interest rates; higher rates are linked to lower returns.

**FFO to Assets (ffo_at_reit):**
- A 1 unit increase in FFO/Assets (fundamental performance) is associated with a 0.5770 change in annual return.
- The point estimate is positive, but the evidence is weak, so we cannot conclude more profitable REITs earn higher returns in this sample.

---

## 4. Statistical Significance

For each slope, at the 5% significance level:
- **div12m_me:** Significant — The negative slope is statistically different from zero at the 5% level.
- **prime_rate:** Significant — The negative slope is highly statistically significant.
- **ffo_at_reit:** Not significant — The slope is not statistically different from zero at the 5% level.

**Which predictor has the strongest statistical evidence of a relationship with annual returns?** prime_rate

---

## 5. Model Fit (R-squared)

Compare R² across the three models:
- prime_rate explains the most variation (R² = 0.016), but R² values are low overall, suggesting most variation in REIT annual returns is driven by other factors not captured by these single predictors.

---

## 6. Omitted Variables

By using only one predictor at a time, we might be omitting:
- Leverage or debt ratio: Higher leverage can amplify returns and risk, affecting annual performance.
- Property sector or REIT type: Sector composition (e.g., office vs. industrial) can drive systematic return differences.
- Market conditions (e.g., equity market return or GDP growth): Broad economic shocks influence REIT returns beyond the single predictor.

**Potential bias:** If omitted variables move with the predictor (e.g., higher rates coincide with weaker macro conditions), the slope can be biased, possibly overstating the negative effect of rates or dividend yields on returns.

---

## 7. Summary and Next Steps

**Key Takeaway:**
The strongest evidence of a relationship is for `prime_rate`, which is negative and statistically significant, consistent with higher borrowing costs pressuring REIT returns. Dividend yield also shows a small but significant negative association, while FFO/Assets has a positive but statistically weak slope. Overall, the single-predictor models explain little of the variation in annual returns.

**What we would do next:**
- Extend to multiple regression (include two or more predictors)
- Test for heteroskedasticity and other OLS assumption violations
- Examine whether relationships vary by time period or REIT sector

---

## Reproducibility Checklist
- [x] Script runs end-to-end without errors
- [x] Regression output saved to `Results/regression_div12m_me.txt`, `regression_prime_rate.txt`, `regression_ffo_at_reit.txt`
- [x] Scatter plots saved to `Results/scatter_div12m_me.png`, `scatter_prime_rate.png`, `scatter_ffo_at_reit.png`
- [x] Report accurately reflects regression results
- [x] All interpretations are in economic units (not just statistical jargon)
