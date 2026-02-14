# Evaluation Dataset

The evaluation dataset is designed to test whether transformer embeddings can identify patristic references in Heinrich Bullinger's 16th-century correspondence. The dataset was created from manually annotated letters using INCEpTION.

## Dataset Statistics
- **Total annotations / query-candidate pairs**: 100
- **Unique letters**: 67
- **Patristic sources**: 49 works (45,920 chunks, ~6.9M tokens)
- **Letter corpus**: 67 letters (19,017 chunks, ~557K tokens)


### By Language
- **Latin-to-Latin**: [92] annotations
- **Greek-to-Latin**: 4 annotations
- **Latin-to-Early New High German**: 4 annotations

## Data Formats
### validation_annotations.json

Complete annotation dataset with metadata:
```json
{
  "metadata": {
    "total_annotations": 100,
    "total_letters": 67,
    "explicit_refs": 50,
    "implicit_refs": 50,
    "allusion_refs": 0,
    "description": "Ground truth patristic references for validation"
  },
  "annotations": [
    {
      "letter_chunk_id": "10015_sent_188_190",
      "source_chunk_id": "035_Augustinus-Hipponensis_In-Joannis-evangelium-tractatus-CXXIV_window_712",
      "letter_text": "Pro modulo meo capio, quod vobis adpono; ubi adperitur, pascor vobiscum, ubi clauditur, pulso vobiscum",
      "patristic_text": "pro modulo meo capio quod vobis appono; ubi aperitur, pascor vobiscum; ubi clauditur, pulso vobiscum.",
      "patristic_source": "Augustinus, In Joannis Evangelium, Tractatus XVII",
      "reference_type": "explicit",
      "confidence": "high",
      "church_fathers": "P18700",
      "detection_source": "passim",
      "begin": 17555,
      "end": 17657,
      "letter_id": "10015"
    },
```

### ir_ground_truth.json

Ground truth for information retrieval evaluation (chunk-level):
```json
{
  "metadata": {
    "description": "Ground truth for IR evaluation (chunk-level)",
    "total_queries": 100,
    "skipped_annotations": 0,
    "by_reference_type": {
      "explicit": 50,
      "implicit": 50
    }
  },
  "ground_truth": [
    {
      "query_chunk_id": "10015_sent_188_190",
      "relevant_chunks": [
        "035_Augustinus-Hipponensis_In-Joannis-evangelium-tractatus-CXXIV_window_712"
      ],
      "letter_id": "10015",
      "reference_type": "explicit",
      "confidence": "high",
      "church_fathers": "P18700"
    },
```

This structure enables standard IR evaluation metrics (Recall@k, Precision@k, MRR).

## Files
- `validation_annotations.json`: Complete annotation dataset with full text and metadata
- `ir_ground_truth.json`: Structured ground truth for IR evaluation
- `bdc_chunks.json`: Chunked Bullinger letters (queries)
- `psc_chunks.json`: Chunked patristic sources (candidates)

## Usage

For IR evaluation, use `ir_ground_truth.json` to compare system predictions against ground truth:
```python
# Load ground truth
with open('ir_ground_truth.json') as f:
    gt_data = json.load(f)

# For each query chunk, system should retrieve the relevant patristic chunk
for entry in gt_data['ground_truth']:
    query_id = entry['query_chunk_id']
    expected_result = entry['relevant_chunks'][0]  # Single relevant chunk per query
```

## Limitations
- Cross-lingual references are underrepresented (4 Greek-to-Latin, 4 Latin-to-ENHG)
- Single relevant chunk per query (reflects one-to-one annotation structure)