# Attribute, Cite, or Quote? A Survey on Evidence-based Text Generation with Large Language Models

This repository contains the annotated data for our survey on evidence-based text-generation with LLMs.

## Contents
- [Abstract](#abstract)
- [Methodology](#methodology)
- [Datasets](#datasets)
- [License](#license)


## Abstract
The increasing adoption of LLMs has been accompanied by growing concerns regarding their reliability and trustworthiness. 
As a result, a growing body of research focuses on evidence-based text generation with LLMs, aiming to link model outputs 
to supporting evidence to ensure traceability and verifiability. However, the field is fragmented due to inconsistent 
terminology, isolated evaluation practices, and a lack of unified benchmarks. To bridge this gap, we systematically 
analyze 134 papers, introduce a unified taxonomy of evidence-based text generation with LLMs, and investigate 300 
evaluation metrics across seven key dimensions. Thereby, we focus on approaches that use citations, attribution, or 
quotations for evidence-based text generation. Building on this, we examine the distinctive characteristics and 
representative methods in the field. Finally, we highlight open challenges and outline promising directions for future 
work.


## Methodology
We identified targeted keywords to guide the literature search on evidence-based text generation. To stay focused on the 
LLM-based paradigm while covering related concepts, we applied the following search string:

**("large language model" OR "llm") AND ("citation" OR "attribution" OR "quote")**

The search string was matched against the title and abstract of each publication. To ensure comprehensive coverage, we 
queried nine literature databases.


| **Literature Database** | **No. of Papers** |
| ----------------------- | ----------------- |
| ACL Anthology           | 54                |
| ACM Digital Library     | 7                 |
| arXiv                   | 59                |
| ICML Proceedings        | 0                 |
| ICLR Proceedings        | 3                 |
| IEEE Xplore             | 4                 |
| NeurIPS Proceedings     | 3                 |
| ScienceDirect           | 0                 |
| Springer Nature         | 4                 |
| **Total**               | **134**           |

In February 2025, we ran the search and removed duplicates, yielding 805 unique publications. Subsequently, we used the 
following inclusion criteria to identify studies relevant to our research focus: 
- (1) studies that aim to generate natural language text with \acp{llm}, 
- (2) studies that deliberately incorporate references to sources of evidence during text generation, and 
- (3) studies that are written in English with the full texts electronically accessible. 

Publications not meeting all criteria were excluded from the final dataset.
The first two authors independently screened all titles and abstracts, consulting full texts as needed. The inclusion 
decisions were made jointly, resulting in 134 relevant publications.

We categorized each publication by contribution type: approach, application, resource, evaluation, survey, and position:

| **Contribution Type** | **Description**                                                                                                                                                       |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Approach**          | An approach consists of a set of novel methods, techniques, and procedures that need to be systematically executed to achieve a concrete goal.                        |
| **Application**       | An application is a documented implementation of an existing approach, technique, or method in the form of a software library, prototype, or full application system. |
| **Resource**          | A resource is a published data set that supports approaches, techniques, methods, or applications, e.g., text corpora or benchmarks.                                  |
| **Evaluation**        | Evaluations of existing approaches, techniques, or methods as well as the introduction of new evaluation approaches including, e.g., new metrics or frameworks.       |
| **Survey**            | A survey analyses and synthesizes findings from multiple studies to systematically review a research field or gather evidence on a topic.                             |
| **Position**          | A position paper presents a personal perspective on the suitability or direction of a specific research aspect, without presenting new empirical evidence.            |


All 134 studies were categorized along the defined dimensions, with annotation split between the first two authors. 
Regular reviews refined the scheme and resolved labeling ambiguities. Each paper could be assigned multiple values per 
dimension if needed.


## Datasets
As a result we have three Datasets which can be mapped:

**publications.csv** This dataset contains all publication metadata and the categorization of each paper:
- Title: Paper tile
- Abstract: Paper abstract
- Year: Year of publication
- Url: Url to access paper
- Authors: Authors of the paper
- Annotator: Anonymized annotator how categorized the paper
- Contribution Type: approach, application, resource, evaluation, survey, or position
- Citation term: Term used to describe concept of integrating evidence: attribution, citation, or quote
- Task name: Name used in paper to describe evidence-based text generation: e.g. citation generation, attributed text generation
- Citation modality: Modality of content which is cited: texts, graphs, tables, or visuals
- Evidence level: Level of granularity of citation: document, paragraph, sentence, token, triple, table, table cell, image, bounding box
- Citation style: How are references to the underlying evidence presented to the user: in-line citation, citation report, passage, narrative citations, highlight gradient, quote
- Citation visibility: Are citations visible to user: finale response, intermediate text
- Citation frequency: How many citations per claim are provided: single, multiple
- Multilinguality: Are the authors using multilingual data: yes, or no
- Parametric: Do the authors use a parametric attribution approach: no, pure llm, data-centric, model-centric
- Non-parametric: Do the authors use a non-parametric attribution approach: no, post-retrieval, post-generation, in-context, in-generation
- Prompting: Which prompting strategies are used: zero-shot, few-shot, chain-of-thought, chain-of-citation, chain-of-quote, conflict-aware, active-oriented, role play, self-consistency
- Pre-training: Does the approach require to pre-train an LLM: yes, or no
- Fine-tuning: Does the approach fine-tune an LLM: no, supervised fine-tuning, self-supervised fine-tuning, reinforcement learning
- Task: Overall task of the paper: e.g. question answering, summarization, grounded text generation, citation text generation, etc.
- Dataset: Extraction of all datasets or benchmarks used (can be mapped with datasets.csv) -> If a paper uses a complete benchmark, we only annotate the benchmark instead of the individual datasets
- Evaluation: Extraction of all metrics or frameworks used (can be mapped with evaluation.csv) -> If a paper uses a complete framework, we only annotate the framework instead of the individual metrics

**evaluation.csv** This dataset contains all metrics and frameworks extracted from publications.csv (Mapping with columns "metric abbreviation" and "framework"):
- Metrik name: Long name of the metric
- Metric abbreviation: Short name of the metric
- Framework: If metric is part of a framework, the framework is listed here
- Evaluation Method: Methodology of evaluation metric: e.g. human evaluation, inference-based, lexical overlap, llm-as-a-judge, retrieval-based semantic similarity-based
- Evaluation Dimension: What is evaluated: e.g. attribution, citation, correctness, linguistic quality, preservation, relevance, retrieval
- Description: Short description of metric (extracted from paper if available)
- Source: URL of paper, which describes the metric

**datasets.csv** This dataset contains all datasets and benchmarks extracted from publications.csv (Mapping with columns "dataset" and "benchmark"):
- Dataset: Name of dataset
- Benchmark: If dataset is part of a benchmark, the benchmark is listed here
- Dataset task: Task the dataset can be used for: e.g. question answering, summarization, etc.
- Source: URL to dataset or paper introducing the dataset


## License
[License](LICENSE)
