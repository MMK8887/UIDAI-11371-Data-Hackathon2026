# UIDAI-Data-Hackathon2026
# 🆔 Aadhaar Trend Intelligence Copilot (ATIC)
**UIDAI–NIC Online Hackathon 2026**

ATIC is a **read-only decision-support analytics dashboard** that identifies **patterns, trends, and anomalies** in Aadhaar enrolment and update activity using a **District Stress Index (DSI)** and explains results using a **Gemini-powered natural language layer**.

---

## 📌 Problem Statement

UIDAI has released anonymised Aadhaar enrolment and update datasets to enable data-driven insights that support **informed administrative decision-making**.

The challenge addressed by this project is to:
- Detect **abnormal enrolment or update behaviour**
- Identify **district-level operational stress**
- Translate complex analytics into **clear, policy-ready insights**

---

## 💡 Solution Overview

ATIC transforms **pre-computed Aadhaar analytics** into an interactive intelligence copilot that allows stakeholders to:

- View **top stressed districts**
- Observe **temporal stress trends**
- Understand **stress-level distributions**
- Ask **natural-language questions** and receive **data-grounded explanations**

> ⚠️ The application is strictly **read-only**.  
> All analytics are **computed offline** and loaded from a single output file.

---

## 📊 Key Features

- District Stress Index (DSI) visualisation  
- Stress classification: Low / Moderate / High / Extreme  
- Monthly trend analysis  
- Policy-oriented recommended actions  
- Gemini-based explanation layer (no recomputation)  
- Fully reproducible and auditable outputs  

---

## 🧠 Analytical Methodology (High Level)

1. **Data Cleaning & Aggregation**
   - Raw UIDAI enrolment, demographic, and biometric datasets
   - Aggregation at District × Month level

2. **Feature Engineering**
   - Normalised update rates
   - Cross-dataset ratios

3. **Anomaly Detection**
   - Statistical Z-score detection
   - Isolation Forest (ML-based)

4. **District Stress Index (DSI)**
   - Composite, interpretable stress metric

5. **Insight Generation**
   - Tables, charts, and natural-language explanations

---

## 🖥️ Application Architecture

Pre-computed Analytics (CSV)
↓
Streamlit Dashboard
↓
Tables • Charts • Filters
↓
Gemini Explanation Layer

yaml
Copy code

---

## 📁 Repository Structure

aadhaar-atic/
│
├── app.py # Streamlit application
├── district_stress_index.csv # Final analytical output (single source of truth)
├── requirements.txt # Dependencies
├── README.md # Project documentation

yaml
Copy code

---

## ▶️ How to Run Locally

### Install dependencies
```bash
pip install -r requirements.txt
Run the Streamlit app
bash
Copy code
streamlit run app.py
🔐 Gemini API Usage
Gemini is used only for explanation, not computation

All numerical values are pre-computed

The model receives compact, validated summaries

No analytics are generated or modified by the LLM

⚠️ The API key is embedded because the repository is private.
Do not make the repository public without removing the key.

📦 Dependencies
nginx
Copy code
streamlit
pandas
numpy
matplotlib
google-generativeai
👥 Team Members
Manish Kumar (Team Lead)

Member 2

Member 3

📈 Impact & Applicability
Enables early identification of district-level Aadhaar stress

Supports targeted administrative intervention

Converts technical analytics into decision-ready insights

Designed for scalability and future integration

📝 Notes
This repository contains only final outputs and visualisation logic

Data preprocessing and model training are performed offline

Shortlisted teams can submit notebooks separately if requested

✅ Hackathon Compliance Checklist
Uses UIDAI-provided anonymised datasets

Clear analytical methodology

Meaningful insights and visualisations

Reproducible and auditable outputs

Strong administrative relevance
