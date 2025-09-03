# 🏨 GTC ML Project 1 – Data Cleaning & Preprocessing

## 👨‍💻 Author
**Youssef Ali Manaa**

---

## 📌 Project Overview
This project is part of the **GTC Machine Learning Challenge**.  
The objective is to transform the raw **hotel bookings dataset** into a **clean, machine-learning-ready dataset** for predicting cancellations.

**Business Problem:**  
Last-minute booking cancellations negatively impact profitability.  
Our role is to prepare the data so that accurate ML models can later be trained.

---

## 🛠️ Workflow

### 🔹 Importing Libraries & Data
- Imported core libraries: `pandas`, `numpy`, `matplotlib`, `seaborn`, `missingno`, `sklearn`.
- Loaded dataset: `hotel_bookings.csv`.

---

### 🔹 Phase 1: Exploratory Data Analysis (EDA) & Data Quality Report
- Inspected the dataset with `.head()`, `.shape`, `.describe()`.
- Checked **missing values** with `missingno` matrix and bar plots.
- Found **outliers** in:
  - `adr` → 3,793 outliers
  - `lead_time` → 3,005 outliers
- Visualized:
  - Reservation status distribution.
  - Reservation status by hotel type.
  - **Top 10 countries by cancellations** (Portugal was the highest).
  - ADR trends over time for **cancelled vs. not cancelled bookings**.
- **Key Findings:**
  - 4 columns with missing values: `company`, `agent`, `country`, `children`.
  - City hotels had more bookings than resort hotels.
  - Higher ADR values are often linked to cancellations.
  - Portugal had the most cancellations.

---

### 🔹 Phase 2: Data Cleaning
- **Missing Values:**
  - `company` & `agent` → filled with `0`
  - `country` → filled with mode
  - `children` → filled with median
- **Duplicates:** Removed duplicate rows.
- **Outliers:** ADR values capped at 1000.
- **Data Types:** Converted `reservation_status_date` to datetime.
- Dataset became cleaner and consistent.

---

### 🔹 Phase 3: Feature Engineering & Preprocessing
- **New Features:**
  - `total_guests = adults + children + babies`
  - `total_nights = stays_in_weekend_nights + stays_in_week_nights`
  - `is_family = 1 if (children + babies > 0) else 0`
- **Feature Reduction:**
  - Dropped leakage columns: `reservation_status`, `reservation_status_date`.
  - Dropped redundant raw columns once aggregated.
- **Encoding:**
  - One-Hot Encoding for low-cardinality categorical variables: `hotel`, `deposit_type`, `customer_type`, `meal`, `distribution_channel`.
  - Frequency Encoding for high-cardinality variables (e.g., `country`).
- **Train-Test Split:**
  - Training set (80%), Test set (20%) using `train_test_split`.

---

## 📊 Tools & Libraries
- **Python**: `pandas`, `numpy`
- **Visualization**: `matplotlib`, `seaborn`, `missingno`
- **ML Preprocessing**: `scikit-learn`

---

## 📁 Repository Structure
