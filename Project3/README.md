# Project 3: Prompt Engineering with Large Language Models

**Course:** DSC 670 – Advanced Uses of Generative AI

## Overview
This project has two parts. Each one tests LLM prompting techniques with measurable checks instead of judging outputs by eye.

### Part A: Policy-grounded customer support assistant (Milestone 2)
Before building a customer support reply generator, I ran five experiments to find out where an LLM succeeds and where it fails at the task. The model was Claude, through the Anthropic API, at temperature 0.2. The store and its support policy, *Harbor & Pine Outfitters*, are made up for the experiments.

| # | Experiment | Question |
|---|---|---|
| 1 | Zero-shot baseline | How well does a general model do with minimal instructions? |
| 2 | Policy-grounded prompt | Does putting the policy in the prompt fix factual accuracy? |
| 3 | Few-shot house style | Can two examples make replies consistent? |
| 4 | Structured JSON triage | Can the model classify intent, sentiment and escalation *and* draft a reply? |
| 5 | Adversarial cases | Does it resist prompt injection, chargeback pressure, pasted card numbers and safety incidents? |

**Key findings**
- The baseline already sounded professional, but it invented a 30-day return window. The real policy is 45 days. It also promised actions it couldn't take.
- Grounding the model in the policy fixed accuracy more than any other change. Policy facts should come from retrieval, not fine-tuning.
- Few-shot examples brought replies under 120 words and in the house style, at the cost of extra tokens on every call.
- Triage produced valid JSON on all 8 test messages and identified the primary intent and language correctly on all 8. That included sarcasm, a message in Spanish, and messages with more than one request.
- The model handled all 4 adversarial cases safely. The remaining gaps were in the policy itself, such as having no rule for "customer sent a card number."

### Part B: Extraction, math and chain of thought (Week 4)
- **Problem 1:** extracted shoe orders from customer emails into a fixed JSON schema, with prices, subtotals and a grand total. I compared zero-shot and one-shot prompting with `gpt-4o-mini`. Python recalculates every total to check the model's arithmetic.
- **Problem 2:** recreated a few-shot chain-of-thought prompt ("when I was 6 my sister was half my age…") with the OpenAI API. The model answered **67**, which is correct, and kept the 3-year age gap in its reasoning.

## Files
- `Milestone2_Prompt_Experiments.ipynb`: Part A experiments (Anthropic API)
- `Milestone2_Anish_Samuel.docx`: Part A written report
- `DSC670_Week4_AnishSamuel.ipynb`: Part B submitted notebook
- `Week4_Prompt_Engineering.ipynb`: longer working version of Part B, with validation helpers, a controlled zero-shot vs. one-shot comparison and a self-consistency check
- `DSC670_AnishSamuel_Week4.docx`: Part B written report

## Tools
Python, Anthropic API (Claude), OpenAI API (`gpt-4o-mini`), pandas, JSON schema prompting, few-shot and chain-of-thought prompting

## How to run
API keys are read from environment variables and are never saved in the notebooks.
```bash
pip install anthropic openai pandas
export ANTHROPIC_API_KEY=...   # Part A
export OPENAI_API_KEY=...      # Part B
jupyter notebook
```
API calls are billed, and LLM outputs can change slightly from one run to the next.
