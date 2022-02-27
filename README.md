
# Multilingual News Article Similarity
[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

## Introduction
This repository is the code for Team Innovator's submission of [SemEval 2022 Task 8](https://competitions.codalab.org/competitions/33835) paper titled "Multi-Task Training with Hyperpartisian and Semantic Relation for Multi-Lingual News Article Similarity". The shared task emphasizes finding the similarity of multilingual news articles irrespective of the style of writing, political spin, tone, or any othermore subjective "design decision" imposed by a medium/outlet. We propose a pipeline consisting of text rank to filter irrelevant information followed by a multi-task approach which allows multiple sub-tasks to share the same encoder during training thereby facilitating knowledge transfer. 

## Data
The model is trained on multiple subtasks as outlined below. The results are evaluated on [SemEval dataset](https://competitions.codalab.org/competitions/33835#learn_the_details-timetable) found [here](https://competitions.codalab.org/my/datasets/download/8379dc75-c824-4ea7-bf00-9d29cb644af5).  

### SemEval Dataset
The SemEval dataset consists of a csv file with each row corresponding to a pair of article. For each article, `url_lang`, `link` and `id` is mentioned. Along with it, the similarity score across `Geography`, `Entities`, `Time`, `Narrative`, `Style`, `Tone` and `Overall` are mentioned. The final evaluation is done on the `Overall` similarity. The content of the news article is extracted using the script given [here](https://github.com/euagendas/semeval_8_2022_ia_downloader).

### Subtask Dataset

| Subtask | Description | Dataset |
|--|--|--|
| Semantic Textual Similarity  | Determine how semantically similar two pieces of text are. | [STS benchmark](https://huggingface.co/datasets/glue#stsb) |
| Hyperpartisan detection | Given a news article, decide whether it follows a hyperpartisan argumentation, i.e., whether it exhibits blind, prejudiced, or unreasoning allegiance to one party, faction, cause, or person. | [Hyperpartisan News Detection](https://pan.webis.de/data.html#pan-semeval-hyperpartisan-news-detection-19) |
| Stance detection | It involves estimating the relative perspective (or stance) of two pieces of text respective to a topic, claim or issue. | [Fake News Challenge - 1](https://github.com/FakeNewsChallenge/fnc-1) |
| Fake news inference detection | Fake news Detection using the Natural Language Inference. This entails categorizing a piece of text into categories such as "pants-on-fire", "false", "barely true", "half-true", "mostly true", and "true." | [Fake News Inference Dataset](https://ieee-dataport.org/open-access/fnid-fake-news-inference-dataset) |
| Paraphrase detection | Determine whether a particular sentence is a paraphrase of the original text. | [Microsoft Research Paraphrase Corpus](https://huggingface.co/datasets/glue#mrpc) |

The preprocessed version of the above datasets are available under `dataset` folder and some are used directly through [hugging-face glue-dataset](https://huggingface.co/datasets/glue) so there is no need to download the datasets. 

## Models
The models can be run locally by cloning the current repository or through google colab using the following links. The pearson score reported are for the validation dataset during training.

| Model | Pearson Score | Link |
|--|--|--|
| **Main Model:** Multi-task Training | 0.835 | [![Open In Collab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/16OqdubHi1OZDhr7Y6XsVyMwIfn7nmImo?usp=sharing) |
| **Experiment 1:** Multi-Objective Weighted Loss Training | 0.811|[![Open In Collab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1lgA3N4kqCnsmrU7i34AvJvsmJCe6d4jh?usp=sharing) |
| **Experiment 2:** Multi-task Training with Multilingual Text Rank | 0.737|[![Open In Collab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1ZTdl_Qq-TkAJaznYWcQ2ZkpjjLdIj0VM?usp=sharing) |

## Setup
1. Clone the current repository and upload it in google drive 
2. Open the concerning notebook in the training module folder and enable GPU access
3. Connect the notebook to your google drive. You can see the tutorial [here](https://colab.research.google.com/notebooks/io.ipynb)
4. Install the dependencies mentioned in the initial cells and the rest of the cells

## Contributors
1. Nidhir Bhavsar* (Navrachana University, Gujarat, India):  nidbhavsar989@gmail.com
2. Rishikesh Devanathan* (Indian Institute of Technology Patna, India) rishi.devanathan@gmail.com
3. Aakash Bhatnagar*  (Navrachana University, Gujarat, India):  akashbharat.bhatnagar@gmail.com 
4. Tirthankar Ghosal (UFAL, MFFCharles University, Czech Republic):    tghosal@acm.org
5. Muskaan Singh (IDIAP Research Institute, Switzerland)

\* denotes equal contribution
