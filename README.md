# Bumble User Profiling & Strategic Analysis

## 📌 Project Overview
Bumble is a market leader in the dating app space. However, maintaining a competitive edge requires a deep understanding of user intent and marketplace health. 

This project goes beyond basic exploratory analysis. It simulates a **Strategic User Data Analysis** aimed at improving matchmaking algorithms and increasing user retention. By moving from raw noisy data to actionable business intelligence, we identify distinct user personas and evaluate the "liquidity" (supply/demand balance) of the dating marketplace.

## 🎯 Objectives
1.  **Data Sanitization:** Cleaning notoriously noisy dating data (handling missing income/height data, removing outliers).
2.  **Behavioral Feature Engineering:** Creating signals for **User Intent** (`profile_completeness`) and **Recency**.
3.  **Marketplace Liquidity:** Analyzing gender imbalances across different geographies.
4.  **User Segmentation:** Using **K-Means Clustering** to group users into actionable personas (e.g., *Power Users* vs. *Casual Browsers*).
5.  **Strategic Recommendations:** Proposing product and marketing interventions based on data.

## 🛠️ Tech Stack
* **Language:** Python 3.x
* **Data Manipulation:** Pandas, NumPy
* **Visualization:** Matplotlib, Seaborn
* **Machine Learning:** Scikit-learn (StandardScaler, K-Means)

## 📊 Key Analysis Phases

### Phase 1: Data Wrangling & Cleaning
* **Missing Data Strategy:** Imputed sensitive fields like `income` using grouped medians (by Age/Gender) to preserve distribution shapes. Imputed `religion` and `sign` with "Prefers not to say" to capture behavioral signaling.
* **Outlier Removal:** Applied IQR-based capping (Winsorization) to `income` to prevent skewing the clustering model, while removing unrealistic age/height entries.

### Phase 2: Feature Engineering
We derived metrics to proxy user behavior:
* **`intent_level`:** Categorized users into High/Medium/Low intent based on `profile_completeness` (effort invested in bio/prompts).
* **`recency_bucket`:** Segmented users into Very Active (<=7 days) to Churned (>90 days).
* **`marketplace_health`:** Calculated Male:Female ratios per location to identify liquidity risks.

### Phase 3: Exploratory Analysis (EDA)
* **Demographics:** Visualized age and income distributions.
* **Psychographics:** Analyzed correlations between lifestyle habits (drinking, diet) and user engagement.
* **Geography:** Identified top cities with the highest user density and gender imbalances.

### Phase 4: User Segmentation (K-Means)
We standardized features (`age`, `income`, `profile_completeness`) and applied K-Means clustering to identify three core personas:

| Persona | Characteristics | Strategic Action |
| :--- | :--- | :--- |
| **🌟 Power Users** | High income, very active, high intent. | **Upsell:** Target with Premium/Spotlight features. |
| **👀 Casual Browsers** | Low completeness, dormant, younger. | **Re-engagement:** Gamified prompts to complete profiles. |
| **💡 Value Seekers** | Medium income, active, medium intent. | **Retention:** Optimize free-to-paid funnel. |

## 💡 Strategic Recommendations
Based on the analysis, the following actions are recommended for the product team:

1.  **Fix Liquidity Imbalances:** Launch geo-targeted acquisition campaigns in cities where the Male:Female ratio exceeds 1.5:1 to prevent male churn.
2.  **Gamify Profile Completion:** Users with <50% completeness should be prompted with "AI-suggested bios" to reduce friction and move them from *Casual* to *Value Seeker*.
3.  **Churn Prediction:** Integrate `days_since_last_online` and `intent_level` into a predictive churn model to trigger notifications before a user becomes "Dormant."

## 🚀 How to Run
1.  Clone the repository:
    ```bash
    git clone [https://github.com/yourusername/bumble-user-segmentation.git](https://github.com/yourusername/bumble-user-segmentation.git)
    ```
2.  Install dependencies:
    ```bash
    pip install pandas numpy matplotlib seaborn scikit-learn
    ```
3.  Run the notebook:
    ```bash
    jupyter notebook Analysis.ipynb
    ```

## 👤 Author
**Ansh Jain** [LinkedIn](https://linkedin.com/in/anshjain1409) | [Portfolio](https://nextleap.app/portfolio/ansh-jain-1rym)

---
*Disclaimer: This analysis is based on a public dataset for educational purposes.*
