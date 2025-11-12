<!--
Source - https://stackoverflow.com/a/12118349
Posted by waldyr.ar, modified by community. See post 'Timeline' for change history
Retrieved 2025-11-12, License - CC BY-SA 4.0
-->

<p align="center">
<img width="200" height="200" alt="为RxSafeBench生成Logo" src="https://github.com/user-attachments/assets/1cf3d281-81ee-44d5-ae93-53d71ed82909" />
</p>

# RxSafeBench: Identifying Medication Safety Issues of Large Language Models in Simulated Consultation

[![arXiv](https://img.shields.io/badge/arXiv-1234.56789-b31b1b.svg)](https://arxiv.org/abs/2511.04328)

## News

- **[October 2025]:** 🎉 *RxSafeBench* has been accepted to **IEEE BIBM 2025 (Short Paper)**!  
- **[October 2025]:** Preprint available on [arXiv](https://arxiv.org/abs/2511.04328).  

---

## Overview


<img width="5594" height="2268" alt="pipeline_01" src="https://github.com/user-attachments/assets/e6c9fb63-3d4b-4d26-af7a-d4b61b7f5ae2" />

**RxSafeBench** is the first comprehensive benchmark designed to evaluate the **medication safety capabilities of Large Language Models (LLMs)** in realistic clinical consultation settings.  
While LLMs have shown impressive performance across various medical applications, their safety in medication recommendation remains largely underexplored due to the lack of real-world, privacy-safe datasets.
<img width="1974" height="660" alt="fig1" src="https://github.com/user-attachments/assets/5a82aa34-d948-4aaa-920a-fe2e4f3384ac" />

To address this gap, RxSafeBench introduces a framework that **simulates doctor–patient consultations** with embedded medication risks. It is built upon **RxRisk DB**, a curated medical safety database containing:
- **6,725 contraindications**  
- **28,781 drug interactions**  
- **14,906 indication–drug pairs**

<img width="2419" height="1058" alt="framework1_01" src="https://github.com/user-attachments/assets/386fcda8-7304-44ad-b239-9f6ec71ee654" />


After multi-stage expert filtering, the benchmark includes **2,443 high-quality consultation scenarios** that test how well LLMs recommend safe medications in realistic contexts.  
Evaluation results reveal that even leading LLMs struggle with **implicit drug risks and complex interaction reasoning**, highlighting the need for improved prompting and domain-specific fine-tuning.

RxSafeBench provides a valuable resource for researchers and developers aiming to build **safer, more reliable AI-driven clinical decision support systems**.

---

## Leaderboard

### Contraindication Part

| Department | Qwen2-7B | Qwen2-72B | Llama-3.1-8B | Llama-3.1-70B | Llama-3.1-405B | GPT-4 | ChatGLM-Turbo | DeepSeek-R1 | Average |
|-----------|----------|-----------|---------------|---------------|----------------|-------|---------------|-------------|---------|
| Internal Medicine | 39.01 | 47.13 | 46.80 | 34.26 | 48.71 | 46.14 | 48.71 | 57.62 | 46.05 |
| Dermatology | 38.21 | 42.28 | 48.36 | 35.77 | 45.22 | 46.34 | 47.15 | 62.60 | 45.74 |
| Pediatrics | 44.00 | 42.86 | 39.13 | 44.00 | 31.82 | 28.00 | 44.00 | 48.00 | 40.23 |
| Surgery | 37.39 | 38.60 | 41.28 | 24.56 | 45.98 | 43.48 | 42.61 | 58.26 | 41.52 |
| Ophthalmology | 19.05 | 38.10 | 27.78 | 14.29 | 31.58 | 23.81 | 38.10 | 71.43 | 33.02 |
| Obstetrics & Gynecology | 43.28 | 40.91 | 47.62 | 39.39 | 39.34 | 37.31 | 43.28 | 59.70 | 43.85 |
| Psychiatry | 27.47 | 29.67 | 33.33 | 29.67 | 40.79 | 34.07 | 37.36 | 57.14 | 36.19 |
| Otolaryngology | 50.00 | 47.73 | 51.28 | 50.00 | 52.38 | 56.82 | 54.55 | 75.00 | 54.72 |
| Neurology | 32.35 | 29.41 | 41.18 | 35.29 | 40.62 | 23.53 | 41.18 | 58.80 | 37.80 |
| Orthopedic | 0.00 | 75.00 | 25.00 | 25.00 | 25.00 | 0.00 | 25.00 | 25.00 | 25.00 |
| Urology | 25.00 | 40.00 | 29.41 | 35.00 | 50.00 | 40.00 | 25.00 | 60.00 | 38.05 |
| Stomatology | 35.71 | 71.43 | 57.14 | 50.00 | 77.78 | 50.00 | 57.14 | 71.43 | 58.83 |
| **Total** | 37.54 | 43.24 | 44.60 | 34.02 | 45.98 | 42.90 | 45.81 | 59.27 | 44.17 |

---

### Drug Interaction Part

| Department | Qwen2-7B | Qwen2-72B | Llama-3.1-8B | Llama-3.1-70B | Llama-3.1-405B | GPT-4 | ChatGLM-Turbo | DeepSeek-R1 | Average |
|-----------|----------|-----------|---------------|---------------|----------------|-------|---------------|-------------|---------|
| Internal Medicine | 28.86 | 31.67 | 24.46 | 28.24 | 27.70 | 34.01 | 33.54 | 41.50 | 31.25 |
| Dermatology | 18.75 | 28.75 | 24.76 | 18.75 | 32.48 | 20.62 | 22.50 | 35.00 | 25.20 |
| Pediatrics | 28.57 | 20.41 | 20.00 | 14.29 | 21.05 | 22.45 | 14.29 | 24.49 | 20.69 |
| Surgery | 30.32 | 29.03 | 21.30 | 20.65 | 23.36 | 29.03 | 25.16 | 31.61 | 26.31 |
| Ophthalmology | 13.89 | 19.44 | 19.05 | 11.43 | 6.67 | 25.00 | 19.44 | 38.89 | 19.23 |
| Obstetrics & Gynecology | 22.22 | 19.75 | 18.87 | 20.99 | 25.33 | 29.63 | 25.93 | 32.10 | 24.35 |
| Psychiatry | 25.45 | 30.00 | 12.00 | 22.73 | 31.96 | 30.91 | 31.82 | 43.64 | 28.56 |
| Otolaryngology | 30.43 | 41.30 | 28.00 | 32.61 | 26.83 | 39.13 | 47.83 | 50.00 | 37.02 |
| Neurology | 10.42 | 4.17 | 16.22 | 12.50 | 23.40 | 25.00 | 20.83 | 27.08 | 17.45 |
| Orthopedic | 37.50 | 37.50 | 40.00 | 25.00 | 66.67 | 50.00 | 50.00 | 37.50 | 43.02 |
| Urology | 34.38 | 18.75 | 10.34 | 21.88 | 0.00 | 28.12 | 6.25 | 43.75 | 20.43 |
| Stomatology | 28.57 | 14.29 | 16.67 | 7.14 | 14.29 | 14.29 | 21.43 | 14.29 | 16.37 |
| **Total** | 26.38 | 28.41 | 22.27 | 23.71 | 27.10 | 30.36 | 29.06 | 38.12 | 28.18 |
