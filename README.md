# 🛒 The Dark Pattern Tax
### Exposing Manufactured Discounts on Flipkart

![Python](https://img.shields.io/badge/Python-3.10-blue)
![Pandas](https://img.shields.io/badge/Pandas-2.0-green)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.7-orange)
![Dataset](https://img.shields.io/badge/Dataset-Flipkart%2020K%20Products-red)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

---

## 📌 Overview

Indian e-commerce platforms display large MRP prices alongside heavily 
slashed selling prices — training consumers to evaluate value through 
the discount percentage rather than the actual price.

But MRP in India is **self-declared by sellers** with no enforcement 
mechanism. This creates a systemic opportunity: inflate the MRP, apply 
a large discount, sell at the original intended price — while the consumer 
feels they won.

**This project investigates whether Flipkart discounts are genuine price 
reductions or systematically manufactured through MRP inflation.**

---

## ❓ Research Question

> *Are Flipkart discounts genuine reductions from real market prices —
> or are they manufactured through artificial inflation of MRP?*

---

## 📊 Dataset

| Property | Detail |
|---|---|
| **Source** | PromptCloud via Kaggle |
| **Link** | [Flipkart Products Dataset](https://www.kaggle.com/datasets/PromptCloudHQ/flipkart-products) |
| **Size** | 19,922 products |
| **Key Columns** | `retail_price`, `discounted_price`, `product_rating`, `product_category_tree` |
| **Categories** | 10 major categories analysed |

---

## 🔬 Methodology

Four independent analyses were conducted, each targeting a different 
dimension of pricing manipulation:

| Analysis | What It Tests |
|---|---|
| **Discount Engineering Test** | Round-number concentration vs statistical expectation |
| **MRP Inflation Index** | How much MRP exceeds selling price per category |
| **Phantom Savings Quantification** | Rupee value of savings that were never real |
| **Quality Trap Analysis** | Relationship between discount size and product quality |

All analyses were built using **pandas** for computation and 
**matplotlib** for visualisation. Matplotlib plots only pre-computed 
pandas outputs — no calculations inside chart cells.

A **Consumer Harm Score (0–100)** was constructed as a weighted 
composite index:
- MRP Inflation Ratio → 40% weight
- Round Number Concentration → 30% weight  
- Phantom Savings % → 30% weight

---

## 🔍 Key Findings

| # | Finding | Result | Signal |
|---|---|---|---|
| 1 | Round-number discount concentration | **15.3%** vs 10% expected | 🔴 1.53x overrepresentation |
| 2 | Avg MRP inflation across platform | **2.3x** selling price | 🔴 MRP is more than double |
| 3 | Phantom savings per product | **₹857 avg** | 🔴 Majority of discount was never real |
| 4 | Total phantom savings (20K products) | **₹1.51 crore** | 🔴 Manufactured consumer perception |
| 5 | Scaled platform estimate | **~₹8,570 crore annually** | 🔴 Across full catalogue |
| 6 | Danger zone products | **227 products** | 🟠 High discount + low quality |
| 7 | Discount-quality correlation | **r = 0.016** | 🟠 Zero predictive power |
| 8 | Highest harm category | **Footwear (66.0)** | 🔴 Tops Consumer Harm Index |

---

## 📈 Charts

### Chart 1 — The Round Number Spike
Discount percentages cluster at round numbers (20%, 30%, 40%, 50%) 
at 1.53x the rate expected under random pricing — a statistical 
fingerprint of engineered discounts.

### Chart 2 — MRP Inflation Index
Category-wise inflation ratios show MRP is set at 2x–2.5x the actual 
selling price across most categories. Mobiles & Accessories (2.51x) 
and Automotive (2.50x) lead at scale.

### Chart 3 — Phantom Savings
On average ₹857 of every displayed discount per product was never 
real. Automotive shows the highest phantom ratio at 84% — 84 paise 
of every ₹1 discount shown was manufactured.

### Chart 4 — The Quality Trap
Correlation between discount % and product rating: r = 0.016 — 
effectively zero. Discount size carries no predictive power over 
product quality. 30% of heavily discounted products fall in the 
danger zone (high discount, low rating).

### Chart 5 — Consumer Harm Score
A weighted composite index ranking categories by systematic deception 
potential. Footwear (66.0), Clothing (65.4) and Mobiles & Accessories 
(59.9) represent the highest consumer risk.

---

## 💡 Recommendations

**For Consumers:**
Always verify price history on Smartprix or PriceSpy before purchasing 
during sale events. Discount percentage is an unreliable signal for 
both value and quality.

**For Flipkart:**
84% phantom savings in Automotive and 66.7% confirmed MRP inflation 
in Clothing represent significant reputational risk. Manufactured 
discounts erode platform trust and long-term GMV — especially during 
high-stakes events like Big Billion Days.

**For Regulators (CCPA):**
The Consumer Harm Score provides a category-level framework for 
prioritising enforcement. Footwear, Clothing, and Mobiles & Accessories 
warrant immediate scrutiny.

---

## ⚠️ Limitations

- Dataset covers ~20,000 products — a sample of Flipkart's full catalogue
- Ratings available for only 9.2% of products — quality trap analysis 
  is directional, not conclusive
- Phantom savings assumes 15% fair margin — actual margins vary by category
- Scaled ₹8,570 crore estimate is illustrative, not audited

---

## 🚀 What I Would Do With More Data

- Track price history over 90 days to directly measure pre-sale MRP inflation
- Include seller-level analysis to identify repeat offenders
- Expand to Amazon India for cross-platform comparison
- Build a real-time consumer alert tool flagging suspected dark pattern products

---

## 🛠️ Tools & Libraries

```python
pandas      # Data cleaning, feature engineering, analysis
matplotlib  # Visualisation — plots only pre-computed pandas outputs
numpy       # Statistical calculations
```

---

## 📁 Project Structure
