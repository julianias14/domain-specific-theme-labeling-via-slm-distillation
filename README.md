# Efficient Customer Support AI: Distilling LLMs into Small Language Models

> Break Through Tech AI Studio | Industry Partner: Automation Anywhere

---

### 👥 **Team Members**

| Name             | GitHub Handle |
|------------------|---------------|
| Juliania Shyprykevych    | @julianias14 |
| Van Do   | @vantastics     |
| Ancheng Li     | @Ancheng-git  |
| Naavya Jain      | @naavyaj-29       |
| Kelly Huang       | @kelly-huang06    |
| Aashish Khosla       | @AashishKhosla    |
| Wiesmes Antwi       | @wiesmes    |

---

## 🎯 **Project Highlights**

**Example:**

- Fine-tuned Phi-3.5-mini (3.8B parameters) using 4-bit QLoRA on a Google Colab T4 GPU.
- Tested SmolLM2 360M and 1.7B models across four hyperparameter experiments.
- Improved Phi-3.5-mini's reported held-out LLM-judge composite score from 3.81 to 3.96 in a later, 1,000-example configuration; other reported response-quality metrics improved as well.
- Consolidated 2,200 evaluation records across SmolLM2 and Phi-3.5-mini baseline and fine-tuned outputs into a common reporting workflow.
- Identified a key trade-off: increases in semantic similarity do not always translate into better LLM-judge scores.
These findings are preliminary and are not evidence yet that an SLM matches a frontier LLM in quality, cost, or latency.

---

## 👩🏽‍💻 **Setup and Installation**

The project uses Python, Hugging Face tooling, and Google Colab for GPU-based experiments. The following steps provide a dataset-access smoke test, not a guaranteed reproduction of the model-training experiments.
1. Clone this repository using its GitHub Code menu, then open the cloned directory.* How to install dependencies
2. Create and activate a Python virtual environment (macOS/Linux):
```
python3 -m venv .venv
source .venv/bin/activate
```
3. Install the packages needed for the dataset smoke test:
```
python -m pip install --upgrade pip
python -m pip install datasets pandas
```
* How to run the notebook or scripts

---

## 🏗️ **Project Overview**

Large language models (LLMs) can help enterprises understand customer-support requests and generate relevant responses, but deploying a frontier model for every request may introduce substantial inference costs and latency. This project investigates whether smaller language models (SLMs) can learn from LLM-generated examples and deliver useful customer-support outputs with a more efficient deployment footprint.

In collaboration with Automation Anywhere, the team is exploring knowledge distillation and parameter-efficient fine-tuning (PEFT), including LoRA and QLoRA. The experimental work covers customer-support request understanding and response generation, using semantic similarity, automated response-quality judgments, and text-overlap measures to evaluate model behavior. The broader challenge also calls for intent/theme-labeling accuracy, inference latency, and cost-per-inference comparisons with a frontier LLM.

Project status (November 2026): Multiple SmolLM2 and Phi-3.5-mini fine-tuning experiments have been completed. Evaluation results are being standardized; a consistent cross-model benchmark and cost comparison have not yet been finalized.

---

## 🧠 **Model Development**

Approach
1. Prepare customer-support instructions and corresponding reference/teacher outputs for experimentation.
2. Establish baseline outputs from the selected pretrained SLM.
3. Adapt the SLM with LoRA/QLoRA and compare hyperparameter settings.
4. Evaluate baseline and fine-tuned generations using the same scoring framework where possible.
5. Consolidate experiment outputs to investigate quality, latency, and eventual cost trade-offs.


---

## 📈 **Results & Key Findings**

| Metric | Baseline | Fine-tuned | Direction |
|------------------|---------------|----------------------|------------|
| Test LLM-judge composite    | 3.86 | 3.67 | Decreased |
| Validation LLM-judge composite | 4.06 | 4.11 | Increased |
| Test cosine similarity | 0.770  | 0.817 | Increased |
| Test multi-reference cosine similarity | 0.825 | 0.862 | Increased |

---

## 🚀 **Next Steps**

1. Validate reconstructed prompts, dataset splits, and reference outputs; finalize the common 17-column evaluation format.
2. Compute BERTScore from saved predictions and references, and resolve missing relevance and batch-size fields where reliable source records exist.
3. Evaluate selected baseline and fine-tuned configurations on the same held-out examples, with the same judge rubric, prompts, and scoring settings.
4. Report separate results for intent/theme-labeling quality and response-generation quality where both tasks are evaluated.
5. Benchmark per-request latency, token usage, and estimated cost under clearly stated, comparable hardware and pricing assumptions.
6. Analyze response specificity and whether additional epochs or higher adapter rank lead to diminishing returns.
7. If feasible, build a live side-by-side customer-support input demo comparing a frontier LLM and the selected SLM.
8. Document limitations, data provenance, and potential research-paper findings.

---

## 🙏 **Acknowledgements**

Thank you to Automation Anywhere, Break Through Tech AI Studio, and the project's Challenge Advisor, AI Studio Coach, and collaborators for their guidance and support.
