# Evaluation Dataset
The evaluation dataset is designed to test whether transformer embeddings can identify implicit patristic references in Heinrich Bullinger's 16th-century correspondence. The dataset was created from the manually annotated letters using INCEpTION.

The dataset was created using the script [query-candidates.ipynb](../scripts/query-candidates.ipynb)

## Dataset Statistics
- **Total annotations**: 100
- **Unique patristic candidates**: 97
- **Unique Bullinger letters**: 67
- **Valid query-candidate pairs**: 100

Note: The difference between 100 queries and 97 candidates is due to three patristic texts cited multiple times in different passages.

## Data Formats
### candidates.jsonl
Each line contains one patristic text reference:
```
json{
    "patristic_id": "PAT_001", 
    "patristic_text": "Etiam in crastinum diem invitamus Charitatem vestram. Cras illi habent, ut audivimus, mare in theatro: nos habeamus portum in Christo.", 
    "source": "Augustinus, Ennarationes in Psalmos, 23", 
    "church_father_id": "P18700", 
    "church_father": "Augustinus"
}
```

### queries.jsonl
Each line contains one letter passage with a patristic reference:
```
json{
    "query_id": "BULL_2902", 
    "annotation_id": 2902, 
    "letter_id": "12805", 
    "query_text": "N. Recipiunt hic sese tandem in portum unde sese tueantur, et cuius praesidio et munimento a se omnem erroris aut peccati suspicionem repellant.",
    "ground_truth_patristic_ids": ["PAT_001"], 
    "metadata": {
        "reference_type": "implicit", 
        "confidence": "high", 
        "detection_source": "scholar", 
        "source_file": "CURATION_USER3640810787533886868.json"}
}
```
