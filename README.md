# Task-1-Researcher-Profile-Mining-and-Analysis

# 🧑‍🔬 Task 1: Researcher Profile Mining and Analysis

This repository contains the implementation for **Researcher Profile Mining and Analysis**, a case study developed to analyze the research profiles of assigned researchers by mining their **Google Scholar** data. The primary objective is to extract recent publications, identify core research themes using **NLP techniques**, compute research diversity, and present results in structured **Excel files**.

---

## 🎯 Objectives

- **Fetch Publications**: Collect the 20 most recent publication titles and abstracts for each assigned researcher from Google Scholar.
- **Build Profiles**: Use NLP techniques (TF-IDF, BERT-based NER) to extract core research themes.
- **Analyze Diversity**: Compute semantic similarity between abstracts to determine research diversity.
- **Generate Outputs**: Produce Excel summaries, diversity reports, and optional Word Clouds.

---

## 📂 Dataset

- Input: `Assigned_People_to_Students.xlsx` — Contains a list of 20 assigned researchers:

- Output: 20 publications per researcher fetched from Google Scholar using SerpAPI or manually curated.

---

## ⚙️ Methodology

### ✅ Step 1: Data Collection

- **Tool**: SerpAPI
- **Output**: Individual Excel files (e.g., `Chen_Jia.xlsx`) with:
  - `S.No`
  - `Researcher Name`
  - `Title of the Paper`
  - `Abstract`

---

### ✅ Step 2: Research Theme Extraction

- **Approach**:
  - Merge abstracts into a single corpus.
  - Apply **TF-IDF** (via `scikit-learn`) to extract high-frequency keywords.
  - Use **BERT-based NER** (`dslim/bert-base-NER`) to identify research-related named entities.

- **Optional**: Generate Word Clouds using the `wordcloud` library.

---

### ✅ Step 3: Diversity Analysis

- **Tool**: `sentence-transformers` (`all-MiniLM-L6-v2`)
- **Metric**: Pairwise cosine similarity among abstracts

| Similarity Score Range | Diversity Level |
|------------------------|-----------------|
| `< 0.4`                | High Diversity  |
| `0.4 - 0.7`            | Medium Diversity|
| `≥ 0.7`                | Low Diversity   |

---

### ✅ Step 4: Output Compilation

- **Excel File**: `Researcher_Analysis.xlsx`
  - `Author_Profiles` sheet: Researcher names and top research themes
  - `Author_Diversity` sheet: Researcher names, similarity scores, and diversity levels


---

## 🔧 Setup Instructions

### 📌 Prerequisites

- Python 3.8+
- SerpAPI key (get from [SerpAPI](https://serpapi.com))
- Git

### 📥 Installation

```bash
# Clone the repository
git clone https://github.com/FenilVadher/Task-1-Researcher-Profile-Mining-and-Analysis.git
cd Task-1-Researcher-Profile-Mining-and-Analysis

# Install required packages
pip install pandas requests nltk scikit-learn transformers sentence-transformers wordcloud matplotlib openpyxl

# Download NLTK resources
python
>>> import nltk
>>> nltk.download('punkt')
>>> nltk.download('stopwords')

