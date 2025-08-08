# 🧬 MOFA+ Multi-Omics Integration for Biomarker Discovery in Stomach Adenocarcinoma

**Author:** Nadeen Ali  
**Course:** Bioinformatics – Spring 2024/2025  
**Instructor:** Dr. Rami Al-Ouran  

---

## 📌 Overview
This project applies **MOFA+** (Multi-Omics Factor Analysis) to integrate **RNA-seq** and **mutation data** from the TCGA-STAD cohort (stomach adenocarcinoma) to identify latent biological factors and potential biomarkers linked to tumor progression and immune response.

The goal is to uncover **hidden patterns across multiple omics layers** that may reveal biological processes relevant to stomach cancer.

---

## 📊 Dataset
- **Source:** [LinkedOmics – TCGA-STAD](https://linkedomics.org/data_download/TCGA-STAD/)
- **Data types:**
  - **RNA-seq** (gene expression, Gaussian likelihood)
  - **Mutation data** (binary mutation status, Bernoulli likelihood)
  - **Clinical data** (basic patient information – used for high-level analysis, not integrated in MOFA)
- **Samples:** 205 patients present in all datasets after preprocessing

---

## ⚙️ Methodology
### 1. **Preprocessing**
- Removed low-quality features:
  - RNA-seq: kept genes expressed in ≥20% of samples
  - Mutation: kept genes mutated in ≥5% of samples
- Matched patients across datasets
- Outlier detection via **PCA**, **t-SNE**, and **UMAP** (no outliers removed)
- Mutation view found to be weaker compared to RNA-seq

### 2. **MOFA+ Model Creation**
- Views:
  - View 0 → RNA-seq
  - View 1 → Mutation data
- 10 latent factors learned
- Saved model in `.hdf5` format for downstream analysis

### 3. **Downstream Analysis**
- **Variance explained** identified **Factors 1–4** as most informative
- Created mapping from feature IDs to gene names for interpretation
- Selected **top 10 genes** per factor
- Performed **GO enrichment analysis** for Biological Processes, Cellular Components, and Molecular Functions

---

## 🔍 Key Findings
### **Factor 1** – Muscle & Ion Transport
- Genes related to muscle contraction, heart/stomach motility, and ion balance
- Suggests tumor impacts tissue dynamics

### **Factor 2** – Protein Transport & Immune Suppression
- Altered protein trafficking pathways
- Tumor may suppress immune signals

### **Factor 3** – Stress Response & Immune Interaction
- Genes active in unfolded protein response and immune regulation
- Suggests tumor adaptation to harsh microenvironments

### **Factor 4** – B Cell Activation & Inflammation
- Strong immune-related activity
- Possible role in inflammation and tumor immune context

---

## 🧪 Potential Improvements
- Add more omics layers (e.g., proteomics, methylation)
- Integrate clinical data as a third MOFA+ view
- Apply clustering/classification to latent factors to detect patient subtypes

---
