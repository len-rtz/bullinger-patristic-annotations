# Text Resue Detection with PASSIM

## Overview of Scripts
### 'xml-to-json.ipynb'
Extracts text from TEI XML files and converts them to JSON format suitable for PASSIM processing

**Input files, both TEI-XML**
- complete set of Bullinger letters (ca. 13,000 files), with <text><body><div><p><s> tags (sentence-level)
- created subset of Corpus Corporum (data/cc-tei) (ca. 700 files), with <text><body><p> tags (paragraph-level)

**What it does:**
After chunking the patristic documents into 300 word chunks with 50 word overlap:
1. Parse TEI XML
2. Extract Metadata
3. Find all <s> or <p> elements in <body>
4. Concatenate text (for Bullinger letters excluding <note> elements)
5. Clean whitespace
6. output = id, text, series, metadata

Saved in 'data/passim/bullinger-letters.json' and 'data/passim/patristic-sources.json' 


### 'passim-normalization.ipynb'
Normalizes Latin and runs PASSIM text reuse detection to find shared passages between Bullinger's letters and patristic sources.

**Input files**
JSON-files of Bullinger Letters and Patristic Sources (data/passim)

**What it does:**
Relatively basic text normalisation such as replacement of j to i and the ligature expansion of e.g. æ to ae. As well as removal of punctuation and normalization of whitespace. Additionally a 'corpus' label is added for PASSIM filtering. After normalization a combined JSON file is created and PASSIM is executed on it.

**Parameter Breakdown:**

| Parameter | Value | Description | Impact on Results |
|-----------|-------|-------------|-------------------|
| `--fields corpus` | - | Use `corpus` field for grouping | Enables cross-corpus filtering |
| `--filterpairs "corpus != corpus2"` | - | Only match across corpora | Prevents Bullinger→Bullinger matches |
| `-n` | 25 | N-gram size (characters) | Longer n-grams = more specific|
| `-m` | 15 | Minimum match length (chars) | Filters short matches |
| `-g` | 20 | Gap tolerance (chars) | Allows word reordering within matches, crucial because letters contain split up quotes and comments |
| `-a` | 20 | Alignment flexibility (chars) | too, handles editorial insertions |
| `--pcopy` | 0.3 | Min proportion overlap (30%) | to catch partial/fragmentary quotations |

**Output**
Clusters of similar matches in a JSON file ('data/passim/passim-output_normalized.json')

### 'passim-analysis.ipynb'
Analyzes PASSIM output to generate statistics and create a CSV-lookup file.

**Input file:**
Output of PASSIM run 'data/passim/passim-output_normalized.json'

**What it does:**
- provides statistic over clusters and citations (total clusters, total matches, larges clusters etc.)
- exports a CSV overview of the clusters / pairs of text from the Bullinger letters and patristic sources in preparation for the annotation

