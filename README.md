UIDAI-11371-Data-Hackathon2026
🆔 Aadhaar Trend Intelligence Copilot (ATIC)

UIDAI Data Hackathon 2026

Aadhaar Trend Intelligence Copilot (ATIC) is a read-only, analytics-driven governance intelligence system designed to uncover patterns, trends, and operational stress signals in Aadhaar enrolment and update activities across India.

The project introduces a statistically grounded District Stress Index (DSI) and operationalizes it through an interactive Streamlit dashboard, supported by an AI-assisted explanation layer for interpretability.

📌 Problem Statement

UIDAI has released anonymised Aadhaar enrolment, demographic update, and biometric update datasets to encourage data-driven insights that support informed administrative decision-making and system monitoring.

The core challenges addressed by this project are:

Identifying abnormal surges and drops in Aadhaar activity

Measuring district-level operational stress in a fair and comparable manner

Translating complex analytics into clear, interpretable, governance-ready insights

💡 Concept & Solution Overview

ATIC evaluates Aadhaar activity relative to each district’s own historical baseline, rather than relying on raw counts or national averages. This design choice ensures:

Scale-invariant comparisons across districts with very different population sizes

Robust anomaly detection under non-stationary and burst-driven behavior

Fair assessment of operational stress independent of absolute volume

All analytics are computed offline, stored as structured CSV outputs, and visualized through a read-only dashboard.
The application enables administrators and analysts to:

Identify high-stress districts

Explore temporal stress patterns

Compare stress distributions across states

Obtain natural-language explanations grounded strictly in computed metrics

⚠️ The application does not modify data or recompute analytics at runtime.

📊 Datasets Used

UIDAI provides three anonymised datasets:

Enrolment Dataset

New Aadhaar enrolments

Age groups: 0–5, 5–17, 18+

Demographic Update Dataset

Name, address, DOB, gender updates

Age groups: 5–17, 17+

Biometric Update Dataset

Fingerprint and iris updates

Age groups: 5–17, 17+

Each dataset spans multiple years and covers nearly the complete district-level administrative geography of India.
For analysis, all datasets are aggregated to District × Month resolution.

🧠 Analytical Methodology (Detailed)
1. Data Preprocessing & Canonical Standardization

Merging multi-sheet Excel datasets into unified tables

Normalizing inconsistent date formats and extracting Year-Month

Canonical standardization of states and districts using controlled mappings

Resolution of spelling variants and aliases

Removal of invalid, duplicate, and non-administrative geographic entries

This step ensures geographic consistency, reproducibility, and auditability.

2. Feature Engineering & Monthly Aggregation

For each State, District, Month, the following metrics are computed:

Total enrolments

Total demographic updates

Total biometric updates

A unified total activity measure is defined as:

Total Activity = Enrolments + Demographic Updates + Biometric Updates


This produces aligned district-level time series across all activity types.

3. Descriptive Statistical Analysis

Before constructing stress indicators, baseline behavior is established for each district through:

Mean monthly activity

Standard deviation of activity

Distributional inspection (skewness, heavy tails, zero inflation)

Key observations:

Activity distributions are highly right-skewed

Most districts exhibit burst-like, non-stationary behavior

Age-group activity moves in parallel within each dataset

These findings justify district-relative normalization instead of raw counts.

4. District-Relative Stress Signal (Z-Score)

Each district’s monthly activity is standardized relative to its own historical baseline:

𝑍
𝑑
,
𝑡
=
𝑋
𝑑
,
𝑡
−
𝜇
𝑑
𝜎
𝑑
Z
d,t
	​

=
σ
d
	​

X
d,t
	​

−μ
d
	​

	​


Where:

𝑋
𝑑
,
𝑡
X
d,t
	​

 is observed activity

𝜇
𝑑
μ
d
	​

 is the district mean

𝜎
𝑑
σ
d
	​

 is the district standard deviation

Interpretation:

Z ≈ 0 → normal behavior

Z ≥ 2 → statistically unusual

Z ≥ 3 → extreme deviation

This produces a district-relative stress signal over time.

5. Stress Component Construction

For each district, anomaly behavior is summarized using three orthogonal components:

Component	Captures	Governance Question
Anomaly Count	Frequency	How often does stress occur
Mean Severity	Typical intensity	How strong are deviations
Max Severity	Peak shock	How severe was the worst incident

These capture frequency, intensity, and tail risk.

6. District Stress Index (DSI)

Because components exist on different scales, min–max normalization is applied.
The final composite index is defined as:

DSI = 0.4 × Anomaly Count
    + 0.3 × Mean Severity
    + 0.3 × Max Severity


DSI ∈ [0, 1]

Stress classification:

Low

Moderate

High

This yields one interpretable, governance-ready metric per district.

🖥️ Streamlit Dashboard

The Streamlit application converts analytical outputs into an interactive decision-support interface featuring:

KPI summary strip

District prioritization table

Top stressed districts visualization

District-level activity and stress timelines

National activity trend

State and stress-level filters

The dashboard is read-only and operates solely on pre-computed analytics.

🔐 AI-Assisted Explanation Layer

Used strictly for interpretation, not computation

Receives validated metrics and summaries only

Explains stress levels and trends in natural language

Does not infer causality or modify results

⚠️ API key is embedded because the repository is private.

🖥️ Application Architecture
Offline Analytics
   ↓
CSV Outputs
   ↓
Streamlit Dashboard
   ↓
KPIs • Tables • Charts
   ↓
AI Explanation Layer

📁 Repository Structure
UIDAI-11371-Data-Hackathon2026/
│
├── app.py
├── district_stress_index.csv
├── district_time_series.csv
├── requirements.txt
├── README.md

▶️ How to Run Locally
pip install -r requirements.txt
streamlit run app.py

📦 Dependencies

streamlit

pandas

numpy

plotly

google-generativeai

👥 Team Members

Manish M Kumar – Team Lead

Vasukinatha Adiga

Deekshith Patkar

📈 Impact & Applicability

Enables early identification of district-level Aadhaar operational stress

Supports targeted monitoring and administrative prioritization

Bridges statistical rigor with governance usability

Designed for scalability and future predictive extensions

📝 Notes

Repository contains final analytics outputs and visualization logic only

Data preprocessing and modeling are executed offline

Detailed notebooks can be shared if requested

✅ Hackathon Compliance Checklist

UIDAI-provided anonymised datasets used

Transparent and reproducible methodology

Statistically grounded indicators

Clear administrative relevance

Final Remark

This repository represents a governance-grade analytics framework, not just a dashboard.
ATIC demonstrates how large-scale Aadhaar operational data can be transformed into actionable, interpretable intelligence for monitoring and decision support
