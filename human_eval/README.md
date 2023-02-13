# Human Evaluation Annotations

This folder contains the annotations created as part of the expert-based human evaluation described in the paper. Each `jsonl` file contains the annotations of a one annotator (annotator 1 or 2) for the evaluation samples on one dataset (PLOS or eLife). Each line in these files consists of a JSON object that contains the annotations for a single article / generated summary. These JSON objects are in the following format:

```
{
  "id": str,                      # unique article identifier
  "abstract": List[str],          # reference abstract
  "lay summary": List[str],       # reference lay summary
  "prediction": str,              # predicted lay summary (BART baseline)
  "scores": dict                  # expert annotations 
}
```

Where the `scores` dictionary contains the fields "Comprehensiveness", "Layness", and "Factuality" mapped to the Likert scale score (1-5) provided by the annotator for each criteria.