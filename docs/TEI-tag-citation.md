# Patristic Citation Extraction Script
This script processes TEI XML letters to extract references to Church Fathers and prepare them for annotation and further lookup in scholarly resources. It identifies possible patristic citations from XML `<persName>` and `<note>` tags.

The script 'extract-tei-citations.ipynb' performs the following tasks:
- Loads Church Fathers metadata from CSV (`church-fathers-gnd-cc.csv`)
- Iterates through a directory of TEI XML letters
- Extracts sentences containing `<persName>` references to Church Fathers
- Identifies footnotes that contain patristic citations (keywords like `Vgl.`, `Cf.`, `PG`, etc.)
- Parses structured citations from footnote text
- Compiles all references into a DataFrame and saves them for annotation
- Prepares a lookup list that is saved in data/citations

## Filtered / Tagged Letters Preprocessing
Before extracting citations, letters were filtered to keep only those mentioning Church Fathers ('subset-tagged-letters.ipynb')

**Steps**:
1. Load Church Fathers CSV 
2. For each XML letter: Parse <persName> elements and check if any reference matches a Church Father ID
3. If yes, copy the file to ../data/bullinger-filtered-letters/
4. Track which Church Fathers appears in each file for a statistic output

## Output of 'extract-tei-citations.ipynb'
"data/citation/patristic_citations_for_annotation.csv" that contains sentences, Church Father IDs/names, footnotes, parsed citations
