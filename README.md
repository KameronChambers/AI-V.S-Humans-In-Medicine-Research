# AI-V.S-Humans-In-Medicine-Research
AI v.s Humans: Answering whether or not AI should play a greater role than humans in cardiovascular procedures.

# Comparative Diagnostic Efficacy: Algorithmic ECG Classification vs. Clinician Interpretation

> **Empirical benchmark evaluating diagnostic classification accuracy and computational latency of a Python-based ECG analysis model against human clinical interpretations.**

[![Python Version](https://img.shields.io/badge/python-3.x-blue.svg)](#)
[![Data Source](https://img.shields.io/badge/Dataset-MIT--BIH%20Arrhythmia-green.svg)](https://physionet.org/content/mitdb/)
[![Paper](https://img.shields.io/badge/Research-PDF%20Preprint-red.svg)](paper/ecg-ai-diagnostic-benchmark.pdf)

---

## 📌 Executive Summary
This independent study investigates the operational tradeoffs between algorithmic machine learning classification and human practitioner interpretation in detecting cardiac abnormalities from Electrocardiograms (ECGs). 

Using the standard **MIT-BIH Arrhythmia Database**, a custom diagnostic terminal pipeline was tested over repeated trials against published empirical baseline data from medical clinicians (Tahri Sqalli et al., 2021). The benchmark evaluates two primary metrics:
1. **Diagnostic Classification Accuracy:** Sensitivity in identifying abnormal vs. normal cardiac rhythm records.
2. **Latency / Processing Throughput:** Time elapsed (in seconds) from record ingestion to diagnostic classification.

---

## 📊 Empirical Findings & Performance Tradeoffs

| Evaluation Metric | Clinician Baseline ($n=16$) | Algorithmic Model ($n=1, 3\text{ trials}$) | Net Variance |
| :--- | :--- | :--- | :--- |
| **Mean Diagnostic Accuracy** | 55.6% | **91.0%** (80% / 94% / 100%) | **+35.4% (Model Advantage)** |
| **Mean Ingestion Latency** | **36.4s** (13.2s – 59.5s) | 85.8s (86.5s / 85.0s / 85.8s) | +49.4s (Clinician Advantage) |

* **Accuracy Advantage:** The diagnostic model demonstrated a **35.4% higher accuracy** in correctly categorizing abnormal arrhythmia records compared to baseline clinical trainees.
* **Latency Overhead:** The model required an average of **85.8 seconds per classification cycle**, reflecting computational constraints on local execution compared to human heuristic scanning.
* **Clinical Implications:** Algorithmic systems serve best not as unilateral diagnostic replacements, but as secondary verification pipelines to eliminate false-negative oversight in high-stakes environments.

---

## 🏗️ Repository Architecture & Data Flow

```text
[MIT-BIH ECG Signal Data]
           │
           ▼
[Preprocessing & Feature Ingestion] ──► [Classification Pipeline (Python)]
                                                        │
                      ┌─────────────────────────────────┴─────────────────────────────────┐
                      ▼                                                                   ▼
       [Diagnostic Output: Normal / Arrhythmia]                          [Execution Latency Logging]
