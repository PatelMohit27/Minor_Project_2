<img width="955" height="937" alt="Screenshot 2026-07-01 182200" src="https://github.com/user-attachments/assets/a0b4f132-3c2e-44fc-b27b-fd334fc206aa" /># Minor_Project_2

# 💸 SpendDNA — Your Wallet's Year-End Story

> *"Spotify Wrapped for your money."*

A Python-based transaction analytics tool that decodes 6 months of UPI/bank statement data into a clean, formatted financial report — built with only Pandas and NumPy, zero ML, zero fintech APIs.

---

## 📸 Output Preview

![SpendDNA Report Part 1](screenshot1.png)<img width="955" height="937" alt="Screenshot 2026-07-01 182200" src="https://github.com/user-attachments/assets/7e3cee28-9cd9-4ae6-be92-835ed2a4365b" />


![SpendDNA Report Part 2](screenshot2.png)<img width="888" height="856" alt="Screenshot 2026-07-01 182222" src="https://github.com/user-attachments/assets/7e91f2cd-70b3-42ca-870a-523eb7e45cc0" />

![SpendDNA Report Part 3](screenshot3.png)!<img width="933" height="888" alt="Screenshot 2026-07-01 182244" src="https://github.com/user-attachments/assets/e9668dde-2e7e-447e-902e-19b618826e3b" />




---

## 🎯 What This Project Does

SpendDNA takes a raw, messy bank statement CSV and produces:

- **Vendor extraction** — maps 280+ messy UPI descriptions to 37 canonical vendor names
- **Category tagging** — classifies every transaction into 12 spending categories
- **Spending overview** — total credits, debits, savings rate, top vendors
- **Monthly trends** — category-wise spend across Jan–Jun 2024
- **Time-of-day patterns** — when does Rahul actually spend? (spoiler: late nights)
- **Anomaly detection** — flags 33 unusually large transactions using z-score
- **Spending archetypes** — assigns personality labels based on spending behaviour
- **Formatted ASCII report** — screenshot-ready console output

---

## 📊 Key Findings (Rahul's Data)

| Metric | Value |
|--------|-------|
| Total Credits | Rs. 5,09,774 |
| Total Debits | Rs. 16,78,901 |
| Savings Rate | -229.3% (BURNING SAVINGS) |
| Top Category | E-commerce (28.4%) |
| Anomalies Found | 33 transactions |
| Unique Vendors | 37 |

**Spending Archetypes Detected:**
- 🛒 THE SHOPAHOLIC (28.4% on e-commerce)
- 📈 THE INVESTOR (17.4% on SIPs)
- 📺 THE SUBSCRIPTION LOVER (4 active subs)
- 💸 THE YOLO SPENDER (savings rate -229.3%)

---

## 🗂️ Project Structure

```
SpendDNA/
│
├── SpendDNA_Patel_Mohitkumar_Dipakkumar.ipynb   # Main notebook
├── rahul_transactions.csv                         # Synthetic dataset (1,328 rows)
└── README.md                                      # This file
```

---

## 🚀 How to Run

**Option 1 — Google Colab (Recommended)**
1. Open the `.ipynb` file in Google Colab
2. Upload `rahul_transactions.csv` to the Colab session files
3. Click `Runtime > Run All`
4. View the formatted report in the final output cell

**Option 2 — Jupyter Notebook (Local)**
```bash
# Install dependencies
pip install pandas numpy

# Launch notebook
jupyter notebook SpendDNA_Patel_Mohitkumar_Dipakkumar.ipynb
```

> Make sure `rahul_transactions.csv` is in the same folder as the notebook.

---

## 🧠 Features Built

| Feature | Description |
|---------|-------------|
| F1 — Transaction Parser | Handles 4 date formats, 3 amount formats, standardises Type field, drops 18 duplicates |
| F2 — Vendor Extractor | Maps 280+ messy descriptions → 37 canonical vendors (0 uncategorised) |
| F3 — Category Tagger | Tags every transaction into 12 categories using vendor→category dictionary |
| F4 — Spending Overview | Executive summary with totals, top categories, top vendors |
| F5 — Monthly Trends | Pivot table showing category spend across 6 months |
| F6 — Time-of-Day | Peak hours per category + weekend vs weekday analysis |
| F7 — Anomaly Detection | Z-score formula (hand-built) flags 33 unusual transactions |
| F8 — Archetype Detection | 10 archetype rules, each as a separate function |

---

## 🔧 Tech Stack

### ✅ Allowed
- Python fundamentals (loops, dicts, functions, f-strings)
- `pandas` — read_csv, groupby, pivot_table, .dt, .str, .map
- `numpy` — mean, std (for z-score)
- `datetime` — strptime for custom date parsing

### ❌ Not Used (by design)
- `matplotlib` / `seaborn` / `plotly` — all visualisation is ASCII-based
- `scikit-learn` / `scipy` — z-score written by hand
- `re` (regex) — all matching via `.str.contains()` and `in` operator
- `collections.Counter` — counters built with plain dicts
- `pandas-profiling` / `sweetviz` — analysis built from scratch

> Constraint discipline is the point. Anyone can run pandas-profiling. Few can build the analysis themselves.

---

## 📁 Dataset

- **File:** `rahul_transactions.csv`
- **Rows:** 1,328 (including 18 duplicates)
- **Period:** Jan 2024 – Jun 2024
- **Persona:** Rahul Sharma, 24, Software Engineer, Bengaluru
- **Columns:** Date, Time, Description, Type, Amount, Balance, Mode, Ref

The dataset is **synthetic** — generated to replicate real Indian UPI transaction messiness including mixed date formats, currency symbols, UPI prefixes, parent company names, and injected anomalies.

---

## 🏗️ The Hard Parts

**Vendor Extraction** was the toughest feature. The same vendor appears as:
```
UPI-SWIGGY-7959@HDFCBANK  →  Swiggy
BHIM SWIGGY               →  Swiggy
POS SWIGGY BANGALORE      →  Swiggy
Swiggy*Order              →  Swiggy
BUNDL TECH P L            →  Swiggy  ← parent company!
BUNDL TECH-INSTAMART      →  Swiggy Instamart
```

Built a keyword dictionary with 40+ vendor entries, each with multiple pattern variants, applied in priority order so specific vendors match before generic P2P/ATM fallbacks.

---

## 📝 AI Assistance Disclosure

Some cells in this notebook were built with AI assistance for syntax help and debugging. All vendor dictionaries, category mappings, and data-specific insights were written based on actual output from running the code on `rahul_transactions.csv`.

As required by the project brief — all AI-assisted cells are marked with:
```python
# AI-assisted: <description>
```

---

## 👤 Author

**Patel Mohitkumar Dipakkumar**


---

*
