
---

# 🏙️ Airbnb NYC Data Analysis — Exploratory Data Analysis (EDA)

This project performs a complete **Exploratory Data Analysis (EDA)** on the Airbnb New York City dataset.
It includes **data cleaning, preprocessing, visualization, outlier removal, feature engineering, and insights**.

---

## 📌 **Project Overview**

This EDA aims to understand:

* Price patterns across neighborhoods
* Relationship between room types and pricing
* Geographic distribution of listings
* Host activity and availability
* Review behavior
* Outliers in price, reviews, location
* Data quality (missing values, incorrect types, encoding issues)

The final cleaned dataset is ready for **modeling**, **dashboarding**, or **further analysis**.

---

## 📁 **Dataset Information**

The dataset contains **22 columns**, including:

* Listing information (`id`, `name`, `neighbourhood`, `room_type`)
* Host information (`host_id`, `host_name`)
* Location (`latitude`, `longitude`)
* Pricing and availability (`price`, `minimum_nights`, `availability_365`)
* Reviews (`number_of_reviews`, `reviews_per_month`)
* Extra details (`bedrooms`, `beds`, `baths`, `license`, `rating`)

---

## 🧼 **Data Cleaning Steps**

### ✔ Handled Missing Values

* Removed rows with missing critical fields (`neighbourhood`, `latitude`, `longitude`, `room_type`, `price`)
* Filled missing values in:

  * `reviews_per_month` → **0**
  * `bedrooms`, `baths` → **median**
  * `rating` → **median**
  * `license` → **"No License"**

### ✔ Fixed Data Types

* Converted IDs to **string** (because float created scientific notation like `9.71E+17`)
* Converted `last_review` to datetime
* Cleaned numeric fields using `to_numeric(errors="coerce")`

### ✔ Fixed Text Encoding Issues

The `name` column contained characters like:

```
Â· â˜…
```

These were fixed using:

* UTF-8 decoding
* Custom replacements

---

## ⚠️ Outlier Detection & Removal

### ✔ Price

* Extreme values like `10000` and `100000` removed
* Kept listings with `price < 1500`

### ✔ Coordinates

* Removed invalid latitude/longitude outside NYC’s range
  (`40–41` and `-74.3 to -73.6`)

---

## 📊 **Visualizations Included**

* Boxplots (price, geographic outliers)
* Histograms (price, reviews, availability)
* Scatterplots (reviews vs price)
* Bar charts (average price by neighborhood & room type)
* Heatmaps (correlation matrix)
* Geographical scatterplot of NYC using lat & long

---

## 🗂️ **Project Files**

| File                   | Description                              |
| ---------------------- | ---------------------------------------- |
| `airbnb_eda.ipynb`     | Full Jupyter Notebook with complete EDA  |
| `datasets.csv`         | Raw dataset                              |
| `datasets_cleaned.csv` | Fully cleaned dataset ready for modeling |
| `README.md`            | Project documentation                    |

---

## 🚀 **How to Run the Notebook**

1. Install dependencies:

```bash
pip install pandas numpy seaborn matplotlib jupyter
```

2. Launch the notebook:

```bash
jupyter notebook airbnb_eda.ipynb
```

---

## 🌟 **Key Insights**

* Manhattan is the most expensive neighbourhood
* Brooklyn is second-highest in price
* Shared rooms are cheapest across all boroughs
* Number of reviews and reviews per month are strongly correlated
* Price has **no strong correlation** with reviews, availability, or minimum nights
* Geographic mapping clearly separates the 5 borough clusters

---

## 📈 Next Steps (Optional)

You can extend this project by:

* Building a **Price Prediction Model**
* Creating **Dashboards** using Streamlit or PowerBI
* Adding **Sentiment Analysis** on the “name” field
* Detecting fraudulent listings

---
