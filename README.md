
# Multilingual News Article Similarity
[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

## Introduction
This repository is the code for Team Innovator's submission of [SemEval 2022 Task 8](https://competitions.codalab.org/competitions/33835) paper titled "Multi-Task Training with Hyperpartisian and Semantic Relation for Multi-Lingual News Article Similarity". The shared task emphasizes finding the similarity of multilingual news articles irrespective of the style of writing, political spin, tone, or any othermore subjective "design decision" imposed by a medium/outlet. We propose a pipeline consisting of text rank to filter irrelevant information followed by a multi-task approach which allows multiple sub-tasks to share the same encoder during training thereby facilitating knowledge transfer. 

## Data
The model is trained on multiple subtasks as outlined below. The results are evaluated on [SemEval dataset](https://competitions.codalab.org/competitions/33835#learn_the_details-timetable) found [here](https://competitions.codalab.org/my/datasets/download/8379dc75-c824-4ea7-bf00-9d29cb644af5). 

| Subtask | Description | Dataset |
|--|--|--|
| Semantic Textual Similarity  | Determine how semantically similar two pieces of text are. | [STS benchmark](https://huggingface.co/datasets/glue#stsb) |
| Hyperpartisan detection | Given a news article, decide whether it follows a hyperpartisan argumentation, i.e., whether it exhibits blind, prejudiced, or unreasoning allegiance to one party, faction, cause, or person. | [Hyperpartisan News Detection](https://pan.webis.de/data.html#pan-semeval-hyperpartisan-news-detection-19) |
| Stance detection | It involves estimating the relative perspective (or stance) of two pieces of text respective to a topic, claim or issue. | [Fake News Challenge - 1](https://github.com/FakeNewsChallenge/fnc-1) |
| Fake news inference detection | Fake news Detection using the Natural Language Inference. This entails categorizing a piece of text into categories such as "pants-on-fire", "false", "barely true", "half-true", "mostly true", and "true." | [Fake News Inference Dataset](https://ieee-dataport.org/open-access/fnid-fake-news-inference-dataset) |
| Paraphrase detection | Determine whether a particular sentence is a paraphrase of the original text. | [Microsoft Research Paraphrase Corpus](https://huggingface.co/datasets/glue#mrpc) |

The preprocessed version of the above datasets are available under `dataset` and some are used directly through [hugging-face glue-dataset](https://huggingface.co/datasets/glue). 
