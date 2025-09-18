# FineTuning-BioSummary

DPO fine-tuning project for OpenAI 4.1-nano using human preference data (evals) from Agent-BioSummary.

## Overview

This project fine-tunes an OpenAI 4.1-nano model using Direct Preference Optimization (DPO) based on human preference data collected from the Agent-BioSummary project. The model learns to generate better scientific summaries by understanding human preferences between different summary styles.

## Project Structure

```
FineTuning-BioSummary/
├── simple_etl_pipeline.ipynb    # ETL pipeline to prepare training data
├── openai_dpo_finetuning.ipynb  # DPO fine-tuning notebook
├── requirements.txt             # Python dependencies
├── TrainingData/               # Generated training data files
└── README.md                   # This file
```

## Setup

1. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

2. **Environment setup:**
   - Create `.env.local` file with your API credentials:
     ```
     OPENAI_API_KEY=your_openai_api_key
     SUPABASE_URL=your_supabase_url
     SUPABASE_KEY=your_supabase_key
     ```

## Usage

### 1. Prepare Training Data
Run `simple_etl_pipeline.ipynb` to:
- Extract preference data from Supabase
- Transform HTML summaries to text
- Apply preference logic (A vs B preferences)
- Save formatted data to `TrainingData/` directory

### 2. Fine-tune Model
Run `openai_dpo_finetuning.ipynb` to:
- Format data for OpenAI DPO training
- Upload training file to OpenAI
- Start DPO fine-tuning job
- Monitor training progress with enhanced metrics

## DPO Training Metrics

The enhanced monitoring provides:
- **Training Loss**: DPO-specific training loss values
- **Preference Accuracy**: How well the model learns preferences
- **Cost Estimation**: Real-time cost calculation
- **Validation Loss**: Performance on validation data
- **Learning Rate**: DPO learning rate (usually Auto)
- **Training Duration**: Actual training time

## Data Source

Training data comes from the `feedback_comparisons` table in Supabase, containing:
- Human preferences between summary versions (A vs B)
- Article content for context
- HTML-formatted summaries converted to plain text

## Model Output

The fine-tuned model will generate scientific summaries that:
- Use simple, clear language for college sophomores
- Explain complex terms when they appear
- Focus on main findings and their importance
- Are engaging and interesting
- Are concise (2-3 paragraphs)
- Are suitable for email newsletters

## Repository

- **GitHub**: https://github.com/ashtekar/FineTuning-BioSummary
- **Privacy**: Private repository (contains API keys and training data)
