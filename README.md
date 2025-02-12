# Custom Named Entity Recognition (NER) for BeHealthy Medical Data

## 📌 Project Overview

This project is part of an **assignment for IIITB** and focuses on **Named Entity Recognition (NER) in healthcare** using **Conditional Random Fields (CRF)**. The goal is to **identify diseases (D) and treatments (T)** from medical text and create a structured **disease-treatment mapping**.

The project is based on a **real-world healthcare scenario** inspired by **BeHealthy**, a health-tech company that connects doctors with patients through online consultations, prescription management, and appointment scheduling. Automating **disease-treatment extraction** can improve medical record analysis and streamline healthcare services.

---

## 🏗 Project Workflow

### **1️⃣ Data Preprocessing**
- The dataset is in **tokenized format**, with each word appearing on a new line.
- Corresponding labels (`D`, `T`, or `O`) are provided separately.
- Sentences are **reconstructed** using empty lines as delimiters.
- Exploratory Data Analysis (EDA) includes **POS tagging** and **noun frequency analysis**.

### **2️⃣ Feature Engineering**
- **Baseline Features**: Word shape, suffixes, uppercase checks, digit detection.
- **Contextual Features**: Previous and next word properties.
- **Syntactic Features**: Part-of-Speech (POS) tags and dependency relations.
- **Custom Enhancements**: Inclusion of domain-specific medical terminology.

### **3️⃣ Model Training & Evaluation**
- **Conditional Random Fields (CRF)** is used for sequence labeling.
- Multiple models are tested:
  - **Model 1:** Baseline with word-level features.
  - **Model 2:** Added POS tags.
  - **Model 3:** Added POS + dependency parsing.
  - **Model 4:** Increased `max_iterations` for training.
- **Evaluation Metric:** Weighted F1-score.

### **4️⃣ Extracting Disease-Treatment Relationships**
- The trained CRF model is applied to test data.
- Identified **diseases** are mapped to their corresponding **treatments** in a structured dictionary.
- Example Query: `"What is the treatment for 'hereditary retinoblastoma'?"`

---

## 📊 Model Performance Comparison

<details>
  <summary>Click to expand Model Comparison</summary>

| Model | Features | Max Iterations | F1 Score |
|--------|----------------------|----------------|----------|
| **Model 1** | Baseline + Word Features | 100 | **0.9122** |
| **Model 2** | + POS Tagging | 100 | 0.9085 |
| **Model 3** | + POS & Dependency Tags | 100 | 0.9097 |
| **Model 4** | + Increased Iterations | **500** | 0.9107 |

**Key Observations:**
- **Model 1** (Baseline + word-level features) achieved the **highest F1-score (0.9122)**.
- Adding **POS and dependency features (Model 2 & 3)** did not significantly improve accuracy.
- **Increasing training iterations (Model 4)** slightly improved Model 3 but still performed worse than Model 1.
- **Feature selection matters more than additional syntactic features** for this task.

</details>

