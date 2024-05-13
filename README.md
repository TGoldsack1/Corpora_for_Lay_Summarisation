# Corpora-for-Lay-Summarisation

This repository contains the code and data for the paper "[Making Science Simple: Corpora for the Lay Summarisation of Scientific Literature](https://aclanthology.org/2022.emnlp-main.724/)", published in EMNLP 2022.

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
  "year": str,                    # year of publication
  "title": str,                   # title
  "sections": List[List[str]],    # main text, divided in to sections
  "headings" List[str],           # headings of each section
  "abstract": List[str],          # abstract
  "summary": List[str],           # lay summary
  "keywords": List[str]           # keywords/topic of article
}
```
**Note:** For the majority of experiments in the paper, our model input consists of the `abstract` concatenated with `sections`.

## Huggingface Datasets

The datasets will are also available on the Huggingface Datasets library ([page link](https://huggingface.co/datasets/tomasg25/scientific_lay_summarisation)).

They can be retrieved as follows:

```
from datasets import load_dataset

dataset = load_dataset("tomasg25/scientific_lay_summarisation", "plos") # replace "plos" with "elife" for eLife dataset
```

**Note:** Both datasets are provided in a slightly different format (using strings instead of lists) via huggingface - see the dataset page on huggingface for details.  

## Human Evaluation Annotations

The annotations created as part of the expret-based human evaluation described in the paper are available in the `human_eval` folder.

## BioLaySumm Shared Task

These datasets have also been utilised as the basis for the BioLaySumm shared task, which has been hosted by the BioNLP workshop at ACL 2023 and 2024. Both editions of the task have used the same training and validation sets as provided here, with new test sets being introduced for each edition. More information on each edition of the task can be found on the [BioLaySumm website](https://biolaysumm.org/).

We provide the test sets for both editions below:

* [BioLaySumm 2024](https://drive.google.com/drive/folders/1M1q8EwUpMt4eM9hfLS_ZXYfBHc3YusjC?usp=sharing)
* [BioLaySumm 2023](https://drive.google.com/drive/folders/16oohd1_dxayYjfS--UOk_iQ5M4uJ54ve?usp=drive_link)

## Citation

When using either dataset, please use the following BibTeX entry:

```
@inproceedings{goldsack-etal-2022-making,
    title = "Making Science Simple: Corpora for the Lay Summarisation of Scientific Literature",
    author = "Goldsack, Tomas  and
      Zhang, Zhihao  and
      Lin, Chenghua  and
      Scarton, Carolina",
    editor = "Goldberg, Yoav  and
      Kozareva, Zornitsa  and
      Zhang, Yue",
    booktitle = "Proceedings of the 2022 Conference on Empirical Methods in Natural Language Processing",
    month = dec,
    year = "2022",
    address = "Abu Dhabi, United Arab Emirates",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2022.emnlp-main.724",
    doi = "10.18653/v1/2022.emnlp-main.724",
    pages = "10589--10604",
    abstract = "Lay summarisation aims to jointly summarise and simplify a given text, thus making its content more comprehensible to non-experts. Automatic approaches for lay summarisation can provide significant value in broadening access to scientific literature, enabling a greater degree of both interdisciplinary knowledge sharing and public understanding when it comes to research findings. However, current corpora for this task are limited in their size and scope, hindering the development of broadly applicable data-driven approaches. Aiming to rectify these issues, we present two novel lay summarisation datasets, PLOS (large-scale) and eLife (medium-scale), each of which contains biomedical journal articles alongside expert-written lay summaries. We provide a thorough characterisation of our lay summaries, highlighting differing levels of readability and abstractivenessbetween datasets that can be leveraged to support the needs of different applications. Finally, we benchmark our datasets using mainstream summarisation approaches and perform a manual evaluation with domain experts, demonstrating their utility and casting light on the key challenges of this task.",
}
```
