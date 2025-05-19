# missing-data-best-practices
Best-practice notebooks for handling missing values—from MCAR testing to model-ready datasets.

# Handling Missing Values: A Comprehensive Guide

## Why this notebook?

Missing data can  
* **Bias your insights** – misleading parameter estimates and conclusions  
* **Reduce statistical power** – fewer usable observations means wider confidence intervals  
* **Break ML pipelines** – many algorithms fail when they see `NaN`s  

This hands-on notebook shows you how to **detect, diagnose, visualise, and impute** missing values **responsibly** so you can keep your analysis honest and your models robust.

---

## Taxonomy of Missingness

| Abbrev. | Full Name | Intuition (casual definition) | Typical Analytical Consequence |
|---------|-----------|------------------------------|--------------------------------|
| **MCAR** | Missing Completely at Random | The fact a value is missing is unrelated to anything – seen or unseen | List-wise deletion remains unbiased (but costs sample size) |
| **MAR** | Missing at Random | Missingness depends only on other observed variables (e.g., low-income fields absent mostly among younger respondents) | Statistical imputation is usually valid and efficient |
| **MNAR**<br>(a.k.a. **NMAR**) | Missing Not at Random | Missingness depends on the value itself (e.g., people with *very* high incomes omit the field) | Must model the missing-data mechanism or use specialised techniques (e.g., selection models) |

> **Rule of thumb:** if you can build a decent classifier that predicts `is_NA` from the other columns, consider the pattern **MAR** rather than MCAR.

---


## Why do values go missing?

Common root causes to watch for:

* **Data-entry errors** – typos, OCR failures, manual form mistakes  
* **Sensor or logging failures** – IoT outages, packet loss, corrupt log files  
* **Survey design quirks** – skip logic, privacy opt-outs, conditional questions  
* **Time-based gaps** – product not launched yet, customer not yet active, late-arriving data  
* **Domain/business rules** – suppressed divisions by zero, calculated fields unavailable at ingest time  

> **Checklist tip:** Start a running log for your project. Each time you discover a new reason for missingness, record it along with affected variables, dates, and remediation steps. Clear provenance saves headaches later.

---

In the sections that follow, we will:

1. **Audit** missingness with summary metrics and visual diagnostics.  
2. **Diagnose** the mechanism (MCAR / MAR / MNAR) with statistical tests and predictive models.  
3. **Compare** common remedies – from simple mean/median fills to MICE, K-NN, and model-based imputations.  
4. **Evaluate** the impact of each strategy on downstream modelling performance.

Let’s dive in!

📖 Medium Article:

---
Max Wienandts
- LinkedIn: https://www.linkedin.com/in/max-wienandts/
- Medium: https://medium.com/@maxwienandts
- GitHub: https://github.com/MaxWienandts
- Buy me a coffee: https://www.paypal.com/donate/?hosted_button_id=2F444HZGJBNX6
