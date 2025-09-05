# Fine-tuning MT Models for Kyrgyz on the OLDI-Seed Dataset

CHECK THE LICENSE:

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

This repository contains the code and results for our submission to the **WMT25 Open Language Data Initiative (OLDI) Shared Task**. Our work focuses on creating a high-quality Kyrgyz-English parallel dataset by translating the OLDI-Seed corpus and demonstrating its value by fine-tuning several state-of-the-art multilingual machine translation models.

## Introduction

[TODO: Maybe smth from Abstract?]

## Repository Structure

The repository is organized by model, with each directory containing the necessary experiment files.


## Models and Experiments

All experiments were conducted by fine-tuning pre-trained models on our 6,193 parallel sentence pairs. The notebooks contain code for data preprocessing, training, and evaluation.

### mT5 (`google/mt5-base`)
TODO: E.g.: [This directory contains the experiment for fine-tuning the mT5-base model. mT5 was pre-trained on a large multilingual corpus that includes Kyrgyz, making it a solid baseline for this task.]

### mBART-50 (`facebook/mbart-large-50`)
The mBART-50 model was not pre-trained on Kyrgyz. For this experiment, we first expanded its tokenizer vocabulary with Kyrgyz tokens before proceeding with fine-tuning. This step is crucial for enabling the model to process and generate Kyrgyz text effectively. In the corresponding folder there are notebooks of fine-tuning (also there are thir copies without tensorboard outputs for proper rendering in the github's browser - with prefix "no_widgets") and json files with results for both directions (EN-KY) and for both datasets - flores+ and X-WMT.

### M2M100 (`facebook/m2m100_418M-base`)
TODO: E.g.: [Similar to mBART, the M2M100 model does not include Kyrgyz in its original 100 languages. We performed vocabulary expansion for this model as well before fine-tuning, adapting it for the new language pair.]

### NLLB-200 (`facebook/nllb-200-distilled-600M`)
TODO: E.g.: [NLLB-200 is a powerful model with strong out-of-the-box support for Kyrgyz. The notebook in this directory details the fine-tuning process on our dataset to further specialize its performance and evaluate its capabilities on specific benchmarks.]

## Getting Started (Maybe delete these section?)

To replicate our results, please follow these steps:

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/your-username/your-repo-name.git
    cd your-repo-name
    ```

2.  **Create a virtual environment and activate it:**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    ```

3.  **Install the required dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

4.  **Download the data:**
    Please follow the instructions in the `data/README.md` file to obtain the OLDI-Seed dataset used for training.

## Experimental Results

We evaluated the fine-tuned models on two standard benchmarks: **FLORES+** and **X-WMT**. The results demonstrate the quality of our dataset, particularly when used to fine-tune strong baselines like NLLB-200.

#### Table 1: Performance on the FLORES+ Benchmark

|           | mT5                               | mBART                             | m2m100                            | **nllb-200**                        |
| :-------- | :-------------------------------- | :-------------------------------- | :-------------------------------- | :---------------------------------- |
| **en-ky** | BLEU: 1.42<br>chrF++: 25.12       | BLEU: 5.33<br>chrF++: 30.82       | BLEU: 0.55<br>chrF++: 34.44       | **BLEU: 9.68**<br>**chrF++: 45.34**  |
| **ky-en** | BLEU: 5.13<br>chrF++: 35.05       | BLEU: 8.00<br>chrF++: 31.12       | BLEU: 8.47<br>chrF++: 37.14       | **BLEU: 19.48**<br>**chrF++: 50.45** |

#### Table 2: Performance Comparison on the X-WMT Benchmark

Our fine-tuned NLLB-200 model sets a new state-of-the-art on this benchmark, significantly outperforming previously published baselines.

|           | mT5                               | mBART                             | m2m100                            | **nllb-200 (Ours)**                 | Bilingual XWMT (Baseline)        | Multilingual MNMT (Baseline)     |
| :-------- | :-------------------------------- | :-------------------------------- | :-------------------------------- | :---------------------------------- | :------------------------------- | :------------------------------- |
| **en-ky** | BLEU: 1.20<br>chrF++: 27.04       | BLEU: 4.49<br>chrF++: 27.17       | BLEU: 0.99<br>chrF++: 31.06       | **BLEU: 12.73**<br>**chrF++: 43.74** | BLEU: 2.33<br>chrF++: 0.27       | BLEU: 4.64<br>chrF++: 0.34       |
| **ky-en** | BLEU: 4.59<br>chrF++: 32.79       | BLEU: 6.23<br>chrF++: 28.62       | BLEU: 5.84<br>chrF++: 34.32       | **BLEU: 19.33**<br>**chrF++: 46.24** | BLEU: 4.65<br>chrF++: 0.29       | BLEU: 10.87<br>chrF++: 0.39      |

## How to Cite

If you use our dataset or code in your research, please cite our paper:

```bibtex
@inproceedings{your-lastname-2025-kyrgyz,
    title     = "The Kyrgyz Seed Dataset Submission to the {WMT}25 Open Language Data Initiative Shared Task",
    authors    = "Murat Jumashev and Alina Tillabaeva and Aida Kasieva and Turgunbek Omurkanov and Akylai Musaeva and Meerim Emil kyzy and Gulaiym Chagataeva and Jonathan Washington",
    booktitle = "Proceedings of the Tenth Conference on Machine Translation ({WMT}25)",
    year      = "2025",
    address   = "[Conference Location]",
    publisher = "Association for Computational Linguistics",
    url       = "[Link to paper when available]",
}
