# Google Play Store Opportunity Analyzer

A market analysis of 9,744 apps across the Google Play Store, built to surface underserved categories and identify where new apps are most likely to succeed.

Tableau Public: [View Dashboard](https://public.tableau.com/app/profile/himaja.kavuri/viz/GooglePlayStoreAnalysis)

---

## Key findings

**Counterintuitive correlation**: Higher review counts correlate with *lower* average ratings. Top-performing categories average 4.3+ stars — well above the overall mean of 4.17 — suggesting that niche, lower-volume categories maintain higher quality signals.

**Opportunity Score ranking**: A composite Opportunity Score was engineered per category, weighting install volume, rating quality, and market saturation:

| Rank | Category | Opportunity Score |
|------|----------|-------------------|
| 1 | BEAUTY | 0.46 |
| 2 | COMICS | 0.44 |
| 3 | PARENTING | 0.41 |

These categories show high install potential relative to competition — strong signals for new entrants.

---

## Dashboards (12 views)

| Dashboard | What it shows |
|---|---|
| Opportunity Score Ranking | Composite score by category — top targets for new apps |
| Opportunity Map | Scatter of avg installs vs avg rating, sized by app count |
| Apps by Category | Distribution of apps across all categories |
| Average Rating by Category | Which categories earn the highest user ratings |
| Rating by Category | Rating spread and variance per category |
| Reviews vs Rating | Correlation analysis — the negative review-rating relationship |
| Top 10 Apps by Installs | Most-installed apps overall |
| Treemap of Installs by Category | Install volume by category, proportional area |
| Free vs Paid Rating | Rating comparison between free and paid apps |
| Free vs Paid by Category | Free/paid mix across categories |
| Paid App Price Distribution | Price spread for paid apps |
| Paid App% by Category | Share of paid apps per category |

---

## Dataset

Source: [Google Play Store Apps — Kaggle](https://www.kaggle.com/datasets/lava18/google-play-store-apps)

Fields: App, Category, Rating, Reviews, Size, Installs, Type (Free/Paid), Price, Content Rating, Genres, Last Updated, Android Version

9,744 apps after cleaning.

---

## Tech stack

- Tableau Desktop / Tableau Public
- Custom calculated fields for Opportunity Score
- Parameters for dynamic avg rating and installs benchmarks

---

## Author

Himaja Kavuri — MS Analytics, USC Viterbi School of Engineering  
Portfolio: [himajakavuri23.github.io](https://himajakavuri23.github.io)  
LinkedIn: [linkedin.com/in/himaja-kavuri](https://linkedin.com/in/himaja-kavuri)
