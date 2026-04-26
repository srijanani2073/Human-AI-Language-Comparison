# Human-AI Language Comparison in Education using NLP

A research project comparing bias patterns in human-authored NCERT textbook passages and AI-generated paraphrases using Natural Language Processing.



## Overview

This project investigates whether large language models (LLMs) **reproduce, reduce, or amplify** social biases found in Indian educational materials. We built a hybrid dataset by pairing original NCERT textbook excerpts (Grades 6–12) with AI-generated paraphrases and counterfactual variants, then evaluated them using both automated NLP metrics and human annotation.

This work was submitted as part of the **Research Methodology** course at Amrita Vishwa Vidyapeetham, Coimbatore.



## Repository Contents

```
├── Dataset.xlsx                      # The annotated parallel dataset (human + AI passages)
├── Dataset_Description.docx          # Detailed description of dataset columns, structure, and usage
├── lang_comp.ipynb                   # Jupyter notebook with full analysis and NLP pipeline
└── Paper.pdf                         # Final research paper submitted for the course
```



## Dataset

The dataset (`Dataset.xlsx`) was created entirely by us for this research project. It is a **parallel corpus** pairing original NCERT textbook passages with AI-generated variants.

### Columns

| Column | Description |
|---|---|
| `id` | Unique passage identifier |
| `class` | Grade level (6–12) |
| `subject` | Subject (History, Civics, Geography, Science, etc.) |
| `chapter` | Chapter name/number |
| `passage_no` | Passage number within the chapter |
| `text` | Original human-authored NCERT excerpt |
| `generated_text` | AI-generated paraphrase or counterfactual variant |

### Dataset Stats

- **Sources:** NCERT textbooks, Grades 6–12 (Social Science, Science, Language subjects)
- **Passage length:** 50–300 words per entry
- **AI generation methods:** Neutral paraphrasing, counterfactual swaps (gender, communal, socioeconomic), prompt variations
- **Bias annotation categories:** Gender, Communal/Religious identity, Race/Ethnicity, Socioeconomic class
- **Annotation scale:** None / Subtle / Explicit



## Methodology

The analysis pipeline (implemented in `lang_comp.ipynb`) includes:

1. **Data Preprocessing** — Text extraction, cleaning, and normalization
2. **AI Text Generation** — Neutral paraphrases and counterfactual variants using LLMs (GPT family, LLaMA, Mistral)
3. **Automated Bias Detection**
   - Embedding-based association tests (WEAT/CEAT)
   - Pronoun and role frequency analysis
   - Sentiment polarity comparison
   - Lexical diversity (Type-Token Ratio)
4. **Human Annotation** — Bias labeling with inter-annotator agreement (Fleiss' κ)
5. **Comparative Analysis** — Human vs. AI bias pattern comparison



## Key Results

- **WEAT effect size** for gender–profession bias: **1.12** (human) vs. **0.57** (AI), showing LLMs partially mitigate explicit bias
- **Pronoun distribution** in human corpus: 67% masculine, 28% feminine → improved to 55% / 38% in AI corpus
- **Explicit bias** detected in 9% of human passages vs. 4% of AI paraphrases
- **Inter-annotator agreement:** Fleiss' κ = 0.81 (strong)
- **Bias index by subject:** History (0.108) > Civics (0.090) > Geography (0.061)
- LLMs demonstrate *semantic smoothing* — reducing overt bias while retaining subtle structural stereotypes



## Running the Notebook

### Prerequisites

```bash
pip install pandas numpy matplotlib seaborn scikit-learn transformers openpyxl
```

### Steps

1. Clone this repository
2. Open `lang_comp.ipynb` in Jupyter Notebook or JupyterLab
3. Ensure `Dataset.xlsx` is in the same directory
4. Run cells sequentially



## Paper

The full research paper is available in `Paper.pdf`. It covers:

- Literature review on gender/social bias in educational materials and AI
- Full dataset description and construction methodology
- Algorithmic framework for bias evaluation
- Results, inferences, limitations, and future directions



## Authors

**Sri Janani S** — M.Tech CSE, Amrita Vishwa Vidyapeetham

**Swarna Dharshini S** — M.Tech CSE, Amrita Vishwa Vidyapeetham



## Disclaimer

This dataset was constructed for academic research purposes only. NCERT textbook content is sourced from publicly available materials. AI-generated paraphrases were produced using publicly accessible LLM APIs for research use.
