# 📈 Lending Portfolio Risk Audit: Stress-Testing Traditional Credit Models

## 🎯 Project Goal

This analysis was conducted to **stress-test the predictive power of traditional credit risk models (FICO Score and Loan Grade)** against a large public lending portfolio (LendingClub). The primary objective was to identify and quantify systemic risk classification failures that present a direct opportunity for an **AI-driven lending platform (Upstart)** to drive partner profitability and minimize unexpected losses.

---

## 💼 Business Context & Problem Statement

Traditional lending relies heavily on historical metrics like FICO. While effective for most consumer segments, AI-driven platforms like Upstart hypothesize that FICO is inefficient. This project proves the inverse: it identifies **"hidden subprime"**—borrowers with seemingly safe FICO scores who are actually high risk.

**Challenge:** If a bank partners with Upstart, they need to know *where* their current risk model is leaking money.

---

## 🔑 Key Findings & Strategic Recommendation

The analysis found that while high-FICO borrowers ($\ge 750$) are generally safe, the risk model exhibits a **highly concentrated anomaly** when evaluating a specific purpose-driven loan:

### 1. Debunking the Volume Trap

* The raw volume analysis showed **Debt Consolidation** had the highest *number* of defaults among Prime borrowers (FICO $\ge$ 750).
* However, the **normalized default rate** proved Debt Consolidation is relatively safe (4.2% default rate), confirming it was a simple volume issue.

### 2. Identifying the Hidden Risk

* The true operational failure is concentrated in the **Small Business loan** category.
* For borrowers with **Prime FICO scores ($\ge$ 750)**, Small Business loans default at a rate of **10.6%**. This is more than **double the average risk** for this demographic.
* **Strategic Conclusion:** The traditional FICO model fails to capture the fundamental risk of entrepreneurship, even for 'Prime' borrowers. This segment represents a significant blind spot and a prime target for a next-generation AI risk model.



### 3. Recommendation for Upstart

**Actionable Insight:** Upstart's AI should focus on building proprietary models that incorporate non-FICO metrics to accurately price the risk of Small Business loans, thereby correcting the model failure and mitigating significant partner losses in this high-risk segment.

---

## 📊 Visualization Highlights

### A. FICO vs. Interest Rate (The Strategic Opportunity)
This scatter plot visualizes the traditional bank pricing model (FICO drives rate) and highlights **all defaulted loans (red dots)**, proving that defaults occur across the entire spectrum, including the low-rate, high-FICO segment (the anomaly).


<img width="988" height="678" alt="image" src="https://github.com/user-attachments/assets/a055a44e-5a7d-4389-bfa5-7e0be5ef3ac1" />


### B. Loan Grade Risk (Baseline Check)
The overall default rate increases linearly with the loan grade (A is safest, G is riskiest), confirming the bank's general model works.



### C. Risk vs. Volume Side-by-Side (Judgment Check)
This dual chart compares default risk and loan volume for a risky category (Educational loans), demonstrating the need to **check sample size** and avoid misleading trends from low-volume data.



---

## ⚙️ Methodology and Technical Stack

* **Data Source:** **LendingClub Loan Data** (2007-2018) from **Kaggle**.
    * [Link to Dataset](https://www.kaggle.com/datasets/wordsforthewise/lending-club)
* **Methodology:** Comparative Risk Analysis, Statistical Filtering, Normalization (calculating the mean of a binary target variable `is_default` to derive the percentage rate).
* **Language:** Python
* **Libraries:** **Pandas** (Data cleaning, filtering, SQL-style merge, aggregation), **Seaborn/Matplotlib** (Visualization, data sampling).
