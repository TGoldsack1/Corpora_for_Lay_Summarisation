# Corpora-for-Lay-Summarisation

This repository contains the code and data for the paper "[Making Science Simple: Corpora for the Lay Summarisation of Scientific Literature](https://arxiv.org/abs/2210.09932)", accepted in EMNLP 2022.

## Data

Download links for PLOS and eLife, the two datasets introduced in our paper, are given below:

* [PLOS](https://drive.google.com/file/d/1lZ6PCAtXvmGjRZyp3vQQCEgO_yerH62Q/view?usp=sharing) (~1.3GB uncompressed)
* [eLife](https://drive.google.com/file/d/1WKW8BAqluOlXrpy1B9mV3j3CtAK3JdnE/view?usp=sharing) (~330MB uncompressed)

Each dataset contains full biomedical research articles paired with expert-written lay summaries. PLOS articles are retrieved from journals published by [the Public Library of Science (PLOS)](https://plos.org/). Similarly, eLife articles are obtained from the [eLife](https://elifesciences.org/) journal. More details/anlaysis on the content of each dataset are provided in the paper.

## Data format
Each dataset consists of 3 files: `train.json`, `val.json`, and `test.json` - corresponding to the training, validation, and test splits. All files are in JSON format and contain a list of JSON objects, each of which contains data for a single article. The JSON objects are in the following format:

```
{
  "id": str,                      # unique identifier
  "year": int,                    # year of publication
  "title": str,                   # title
  "sections": List[List[str]],    # main text, divided in to sections
  "headings" List[str],           # headings of each section
  "abstract": List[str],          # abstract
  "summary": List[str],           # lay summary
  "keywords": List[str]           # keywords/topic of article
}
```

## Huggingface Datasets

These datasets will also be made available via the Huggingface datasets library (coming soon).

## Citation

When using either dataset, please cite the following:

```
"Making Science Simple: Corpora for the Lay Summarisation of Scientific Literature"
Tomas Goldsack, Zhihao Zhang, Chenghua Lin, Carolina Scarton
EMNLP 2022
```
