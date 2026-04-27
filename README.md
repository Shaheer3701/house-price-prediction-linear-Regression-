# 🏠 Pakistan House Price Prediction

A complete end-to-end Machine Learning project to predict house prices across Pakistan's 5 major cities using real Zameen.com data and Linear Regression.

---

## 📌 Project Overview

This project covers the full Data Science pipeline:
- Data Cleaning & Preprocessing
- Exploratory Data Analysis (EDA)
- Feature Engineering
- Model Building & Evaluation

**Model Performance: R² Score = 0.82** (explains 82% of house price variation)

---

## 📂 Project Structure

```
House_Price_Prediction/
├── Data/
│   ├── raw/          ← original dataset (not tracked by git)
│   └── cleaned/      ← cleaned dataset (not tracked by git)
├── notebooks/
│   └── house_price.ipynb
├── visuals/
│   └── *.png
└── README.md
```

---

## 📊 Dataset

- **Source:** Kaggle — Zameen.com Pakistan Property Data
- **Raw Data:** 191,000+ property listings
- **Final Clean Data:** 126,000+ properties after cleaning
- **Cities:** Karachi, Lahore, Islamabad, Rawalpindi, Faisalabad

---

## 🔧 Data Cleaning

Key cleaning steps performed:

- Removed 64,000+ rent listings — keeping only sale properties
- Replaced zero values in baths/bedrooms using property type median
- Converted mixed area units (Kanal/Marla) to standard Marla
- Removed properties with invalid prices (below 1M or above 500M)
- Dropped irrelevant columns: agent, agency, page_url, purpose, province

**Started with 191k rows → Ended with 126k clean rows**

---

## 📈 Exploratory Data Analysis

### Price Distribution — Before & After Log Transformation

![Price Before](visuals/Price%20distribtion%20before%20log%20transformation.png)
![Price After](visuals/price%20distribtion%20after%20log%20transformation.png)


> Price data was heavily right skewed. Log transformation converted it to a normal distribution — essential for Linear Regression.

---

### Price by City

![Cities Before](visuals/Boxplot%20By%20cities%20before%20log%20transformation.png)
![Cities After](visuals/Boxplot%20By%20cities%20after%20log%20transformation.png)


> Islamabad has the highest price variation. Faisalabad is the most affordable major city.

---

### Price by Property Type

![Property Before](visuals/Boxplot%20By%20Property%20Type%20before%20log%20transformation.png)
![Property After](visuals/Boxplot%20By%20Property%20Type%20after%20log%20transformation.png)


> Farm Houses have the highest price variation. Rooms and Lower Portions are most affordable.

---

### Correlation Heatmap

![Correlation](visuals/Correlation%20Heatmap%20before%20Log%20Transformation.png)
![Correlation After Feature Engineering](visuals/Correlation%20Heatmap%20after%20feature%20engineering.png)


> Area_marla is the strongest predictor of price (0.8 correlation). Baths and bedrooms are highly correlated with each other (0.68) — multicollinearity noted.

---

## ⚙️ Feature Engineering

| Feature | Transformation | Reason |
|---|---|---|
| price | Log transformation | Heavy right skew |
| area_marla | Log transformation | Heavy right skew |
| city | One Hot Encoding | 5 categories |
| property_type | One Hot Encoding | 6 categories |
| location | Target Encoding | 1459 unique values |

---

## 🤖 Model Building

- **Algorithm:** Linear Regression (scikit-learn)
- **Train/Test Split:** 80% / 20%
- **Target Variable:** log(price)

---

## 📉 Model Evaluation

| Metric | Value |
|---|---|
| Train R² | 0.819 |
| Test R² | 0.823 |
| RMSE (log scale) | 0.40 |

### Residual Plot

![Residual](visuals/Residual%20Plot.png)

> Model performs well for mid-range properties. Struggles with luxury properties above 50M — visible heteroscedasticity at high predicted values.

**No overfitting detected** — train and test scores are nearly equal.

---

## 🔑 Key Findings

- Area_marla is the strongest numerical predictor of price
- Location is the most critical feature overall — same area size can have 10x price difference by location
- Islamabad has highest price variation across all cities
- Faisalabad is the most affordable major city
- 64k rent listings were mixed with sale listings — a major data quality issue

---

## 🚀 Future Improvements

- Try **Random Forest** or **XGBoost** for non-linear patterns
- Add distance-based features (distance from city center, schools)
- Collect more luxury property data to improve high-price predictions
- Deploy as a **web app** where users input property details and get instant price estimates

---

## 🛠️ Tech Stack

- Python
- Pandas, NumPy
- Matplotlib, Seaborn
- Scikit-learn

---

## 👤 Author

**Shaheer Khan**  
Aspiring Data Scientist | Pakistan  
GitHub: [@Shaheer3701](https://github.com/Shaheer3701)
