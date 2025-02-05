# Text Simplification Evaluation Framework
This repository contains a  framework for evaluating text simplification systems using multiple evaluation metrics, from traditional approaches like BLEU to modern LLM-based assessment methods.

## Overview
The framework implements and compares various evaluation metrics for text simplification:

- N-gram metrics (BLEU, SARI)
- Embedding-based metrics (BERTScore)
- Learning-based metrics (BLEURT)
- LLM-based evaluation (G-Eval)

## Requirements
```bash
$ pip install -r requirements.txt
```

## Setup

1. Clone the repository
2. Install dependencies
3. Download BLEURT checkpoint:

```bash
$ wget https://storage.googleapis.com/bleurt-oss-21/BLEURT-20.zip
$ unzip BLEURT-20.zip
```
4. Set up your OpenAI API key for G-Eval:
```python
os.environ["OPENAI_API_KEY"] = "your-key-here"
```

## Usage
The framework consists of two main notebooks that work with text from the OneStopEnglish corpus:

1. Data Generation (simplification_alteration_generation.ipynb)

  - Uses sentence_pairs.xlsx containing 21 sentence pairs from the corpus
  - Takes the first 20 pairs for generation (last pair serves as an example)
  - For each sentence, generates controlled alterations:
    - Fact reversal
    - Information omission
    - Unsupported information addition
    - Subject/object reversal
    - Partial meaning preservation

2. Metric Evaluation (metrics.ipynb)
  - Takes the generated alterations as input
  - Processes and evaluates all versions of each sentence
  - Outputs results to 'final_evaluation_results.xlsx'

Results are saved to 'final_evaluation_results.xlsx' with scores for each metric across different types of simplifications.