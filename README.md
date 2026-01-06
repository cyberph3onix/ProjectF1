# 🏎️ ProjectF1 — F1 Race Outcome Prediction

**ProjectF1** is a data-driven machine learning pipeline built to predict Formula 1 race results. By analyzing historical qualifying performance, car telemetry, and track conditions, the model attempts to forecast the final race classification before the lights go out.

---

## 📊 Data Source

The project leverages high-fidelity racing data from the **2019–2024** seasons:
* **API:** [FastF1](https://github.com/theOehrly/FastF1) (Wrapper for Ergast and official F1 Live Timing).
* **Scope:** Historical race results, qualifying lap times, and session telemetry.
* **Format:** Processed into structured CSV datasets partitioned by Grand Prix.

---

## ⚙️ Tech Stack

* **Language:** Python
* **Data Analysis:** Pandas, NumPy
* **Machine Learning:** Scikit-learn
* **Data Retrieval:** FastF1
* **Environment:** Jupyter Notebook

---

## 🧠 Approach

### 1. Data Collection & Cleaning
Extracted session data for every GP since 2019. This includes filtering for DNFs (Did Not Finish), technical failures, and grid penalties that shift the starting order.

### 2. Feature Engineering
Focused on **pre-race features** available before the Sunday start:
* **Grid Position:** The driver's starting slot.
* **Qualifying Delta:** The time gap between the driver and the Pole position.
* **Constructor Performance:** Historical team strength at specific track types.
* **Tire Compounds:** Selected sets available for the race.

### 3. Modeling
Trained regression-based models (such as Random Forest and Gradient Boosting) to predict the numerical finishing order, which is then ranked to produce the final predicted leaderboard.

### 4. Evaluation
Performance is measured using:
* **MAE (Mean Absolute Error):** Average displacement from the actual finishing position.
* **Top 3 Accuracy:** How often the model correctly identifies podium finishers.

---

## 📁 Project Structure

```text
ProjectF1/
├── data/
│   ├── raw/                # Unprocessed CSVs from FastF1
│   └── processed/          # Cleaned features ready for ML
├── notebooks/
│   ├── 01_extraction.ipynb # Data scraping scripts
│   ├── 02_eda.ipynb        # Exploratory data analysis
│   └── 03_modeling.ipynb   # Training and evaluation
├── src/
│   ├── config.py           # API keys and constants
│   └── processing_utils.py # Helper functions for data cleaning
├── requirements.txt        # Python dependencies
└── README.md
