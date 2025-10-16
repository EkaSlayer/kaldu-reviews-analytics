# Kaldu Reviews Analytics

**Project Title**: Kaldu Reviews Analytics — Mining Public/Non-confidential Feedback for Actionable Insights

## Project Overview
This project analyzes public (or non-confidential) customer reviews to extract **sentiment**, **frequent topics**, and **operational signals** for a Kaldu-related business (e.g., F&B). We combine **EDA**, **lexicon-based sentiment (VADER or fallback)**, and **unsupervised topic cues** (KMeans on n-grams) to produce clear recommendations.

## Raw Dataset
- Local copy: [sandbox:/mnt/data/kaldu-cleaning.xlsx](sandbox:/mnt/data/kaldu-cleaning.xlsx)
- Original sheets detected: ['Recovered_Sheet1', 'Recovered_Sheet1 (2)']

## Analytical Results (TL;DR)
- Total reviews: **255**
- Owner reply rate: **26%**
- Sentiment counts: {'positive': 8, 'neutral': 245, 'negative': 2}
- See `/outputs/insights.json` and `/outputs/charts/` for details.

## Insight & Findings
1. **Sentiment mix** skews across positive/neutral/negative (see chart). Prioritize converting neutrals to promoters (reduce friction points highlighted by negative keywords).
2. **Top terms** reveal recurring themes: enak, makanan, pelayanan, ga, yg, tempatnya, makanannya, makan. These likely represent product attributes (e.g., rasa/price/service/speed).
3. **Topic cues (unsupervised)** group reviews into **5** clusters by language patterns, useful for routing improvements (menu, service speed, cleanliness, etc.).
4. **Owner engagement**: Reply rate ≈ **26%**. Timely, template-based responses can improve perceived care and reduce churn.

## Analysis Process
1. **Load & clean**: drop duplicates; parse timestamps; fill missing fields.
2. **Text prep**: lowercasing, punctuation/digit removal, basic stopwords (ID & EN).
3. **Sentiment**: VADER (if available), otherwise a small ID/EN lexicon fallback; thresholds: ±0.2 for label.
4. **N-grams**: CountVectorizer (1–2 grams, min_df=3, max_df=0.9).
5. **Topics (unsupervised)**: KMeans (k=3 or 5, depending on rows), top terms per cluster.
6. **KPIs**: reviews per month, sentiment distribution, top terms; owner reply rate.

## Conclusion & Recommendations
- **Standardize responses**: Raise **owner reply rate** to ≥80% with polite, helpful templates; add a path to resolution (WhatsApp/DM).
- **Targeted fixes**: Use **negative terms** and **topic cues** as a punch list—prioritize hygiene, speed, and taste consistency.
- **Promoter flywheel**: Encourage **photo/review prompts** post-purchase, add small perks for detailed feedback; leverage **UGC**.
- **Track monthly**: Maintain this notebook, export charts, and monitor trend shifts after each operational change.

## AI Support Explanation
- **NLP/Sentiment**: VADER (or lexicon fallback) classifies polarity per review (AI-driven rule-based).  
- **Unsupervised learning**: **KMeans** on n-gram TF counts to derive topic cues.  
- **LLM support**: This README and slide narrative were drafted/refined using an LLM to articulate findings and recommendations.

## How to Run (Colab/GitHub)
1. Upload this repo to GitHub.
2. Open `notebooks/kaldu_analysis.ipynb` in **Google Colab**; ensure `/data/kaldu-cleaning.xlsx` is present.
3. Run all cells to regenerate charts in `/outputs/charts/` and insights in `/outputs/insights.json`.

---
**Author**: Eka Hilal Hamdi
