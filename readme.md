# Task 08 – Bias Detection in LLM Data Narratives  
*A Complete, Reproducible Experiment on Framing, Demographic, Confirmation & Selection Bias in LLM Outputs*

---

## 📌 Overview

This project investigates whether **Large Language Models (LLMs)** generate biased analytical narratives when analyzing **identical sports statistics** under **different prompt framings**.  

Using anonymized **Syracuse University Women’s Lacrosse data**, this experiment tests:

- **Framing Bias** (positive vs negative wording)  
- **Demographic Bias** (experience cues)  
- **Confirmation Bias** (hypothesis priming)  
- **Selection Bias** (which stats the LLM highlights)

The workflow includes prompt design, multi-sample LLM querying, structured logging, statistical analysis, factual validation, and final reporting.

This repository contains **all files, code, analysis, and reports** required for full reproducibility of Task 08.

---

## 📁 Repository Structure

Task_08_Bias_Detection/
│
├── prompts/ # Prompt templates & variations
├── results/ # Raw LLM outputs (JSON/CSV)
├── analysis/ # Bias analysis outputs
│ ├── analysis_summary.json
│ ├── chi_square_results.json
│ └── fabrication_report.json
│
├── experiment_design.ipynb # Creates all prompt variations
├── run_experiment.ipynb # Queries LLMs and logs responses
├── analyze_bias.ipynb # Sentiment, mentions, chi-square
├── validate_claims.ipynb # Checks factual accuracy
│
├── REPORT.md # Final written report
├── Final_Report_Task08.docx # Formatted final report
├── Initial_Planning_Report_Task08.docx
├── Research_Task_08.docx # Assignment instructions
│
└── README.md # (This file)

---

## 🎯 Objectives

This project followed the four-phase structure outlined in the Research Task 08 instructions:

1. **Experimental Design:**  
   - Build prompt pairs varying only by framing or demographic cues.  
   - Document expected “ground truth” based on sports statistics.

2. **Data Collection:**  
   - Query GPT models using each prompt.  
   - Gather multiple samples (3–5 responses per prompt).  
   - Log model version, timestamp, prompt, and narrative.

3. **Analysis:**  
   - Sentiment scoring  
   - Entity/keyword frequency  
   - Recommendation-type classification  
   - Chi-square statistical testing  
   - Narrative tone assessment  

4. **Validation:**  
   - Check if LLM claims match real data  
   - Detect hallucinations  
   - Compute fabrication rate  

---

## 🧪 Methodology

### 1. Prompt Design
Created minimally different prompts that altered:

- Tone (“underperforming” vs “showing potential”)  
- Demographic context (“senior” vs “sophomore”)  
- Hypothesis framing (“offense is weak”)  
- Data emphasis (“focus on turnovers”)

### 2. Response Collection
- LLMs used: **GPT-3.5 and GPT-4 (Oct 2025 builds)**  
- Standardized temperature and model parameters  
- Logged all data in `responses.csv`

### 3. Quantitative Analysis
- **Sentiment analysis:** VADER/TextBlob  
- **Keyword mentions:** Player A/B/C, stats, focus areas  
- **Recommendation type:** offense/defense/team/individual  
- **Statistical tests:** chi-square where applicable  

### 4. Factual Validation
Each narrative was compared with ground-truth lacrosse statistics to check:

- Numerical correctness  
- Claims about player performance  
- Hallucinated facts  

Fabrication rate: **0%**

---

## 📊 Key Findings

### ✔️ H1: Framing Bias — Mild  
Positive framing increased sentiment (+0.5) vs negative framing (0.0).  
Content stayed factually correct, but tone changed noticeably.

### ✔️ H2: Demographic Bias — None  
Adding experience level (senior/sophomore) did not change:
- Recommendations  
- Sentiment  
- Language tone  

### ✔️ H3: Confirmation Bias — None  
Priming the LLM with a hypothesis did not influence conclusions.

### ✔️ H4: Selection Bias — None  
The LLM did not preferentially highlight different statistics based on framing.

### ✔️ Fabrication Rate — 0%  
All LLM responses matched ground-truth performance data.  
No hallucinations were observed.

---

## 📘 Bias Catalogue

| Bias Type | Observation | Severity |
|----------|-------------|----------|
| **Framing Bias** | Tone changes (“growth potential” vs “underperforming”) | Mild |
| **Demographic Bias** | No change from experience cues | None |
| **Confirmation Bias** | LLM stayed neutral despite priming | None |
| **Selection Bias** | No preference for specific stats | None |
| **Factual Accuracy** | No hallucination detected | Strong |

---

## 📌 Limitations

- Small sample size (10 responses)  
- Limited categorical diversity → chi-square tests often inconclusive  
- Only GPT models examined deeply  
- Sentiment analysis tools may oversimplify tone  
- Narrative bias may require larger datasets to detect subtle patterns  

---

## 🛠 Tools Used

**Languages / Libraries**
- Python  
- Pandas, NumPy  
- SciPy (chi-square tests)  
- TextBlob, VADER  
- Matplotlib  

**Models**
- GPT-3.5 / GPT-4 (October 2025)  

**Environment**
- Jupyter notebooks  
- GitHub for version control  

---

## 🚀 How to Reproduce the Project

### 1. Install dependencies
