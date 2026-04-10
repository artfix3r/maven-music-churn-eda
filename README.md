# Maven Music – Customer Churn EDA & Feature Engineering

An end-to-end Exploratory Data Analysis (EDA) project on Maven Music customer data,
aimed at building a supervised machine learning model to predict subscription cancellations.

---

## 📌 Project Objective

Predict which customers are most likely to cancel their subscription using the past
three months of customer and listening history data.

---

## 📂 Dataset

| File | Description |
|------|-------------|
| `mavenmusiccustomers.csv` | Customer profiles: subscription plan, rate, discount, cancellation date |
| `mavenmusiclisteninghistory.xlsx` | Listening history (songs & podcasts), audio metadata, session logs |

**Tables used:**
- `customers` – 30 customers, 8 columns
- `listening_history` – 505 rows of audio play records
- `audio` – 17 audio tracks/podcasts with genre & popularity
- `sessions` – 90 session login timestamps

---

## 🛠️ Steps Performed

### 1. Scope the Project
- Defined a supervised learning approach to classify churned vs. active customers.

### 2. Gather Data
- Loaded CSV and multi-sheet Excel files into Pandas DataFrames.

### 3. Clean Data
- **Data Type Conversion:** Converted `Member Since`, `Cancellation Date` to datetime; `Subscription Rate` to float.
- **Missing Values:**
  - Filled missing `Subscription Plan` values as `"Basic Ads"` (all had rate = $2.99).
  - Encoded `Discount?` as binary (1 = Yes, 0 = No).
  - Kept `Cancellation Date` NaT as "still active."
- **Typos:** Fixed `99.99` subscription rate (should be `9.99`); standardized `"Pop Music"` → `"Pop"`.
- **Duplicates:** Confirmed no duplicate rows.

### 4. Exploratory Data Analysis
- Analyzed genre preferences per customer.
- Computed listening session counts.
- Calculated percentage of Pop, Hip-Hop, Country, Jazz, Comedy, and True Crime listens per customer.

### 5. Feature Engineering
Built a model-ready feature table with:
- `Cancelled` (target label)
- `Discount?`
- `Number of Sessions`
- Genre listening percentages (Pop, Hip-Hop, Country, Jazz, etc.)
- Total audio items listened to

---

## 🔧 Tools & Libraries

- Python 3.x
- `pandas` – data loading, cleaning, aggregation
- `numpy` – type conversions & conditional logic
- `openpyxl` – reading multi-sheet Excel files

---

## 🚀 How to Run

1. Clone this repository:
   ```bash
   git clone https://github.com/your-username/maven-music-churn-eda.git
   cd maven-music-churn-eda
   ```

2. Install dependencies:
   ```bash
   pip install pandas numpy openpyxl
   ```

3. Place the data files in the project root:
   - `mavenmusiccustomers.csv`
   - `mavenmusiclisteninghistory.xlsx`

4. Open and run the notebook:
   ```bash
   jupyter notebook ea.ipynb
   ```

---

## 📊 Key Findings

- **13 out of 30 customers** cancelled their subscription.
- Customers with only 1 session are more likely to have cancelled.
- Discount holders make up ~23% of the customer base.
- Subscription plans: Basic Ads ($2.99), Premium No Ads ($7.99–$9.99).

---

## 📁 Project Structure
