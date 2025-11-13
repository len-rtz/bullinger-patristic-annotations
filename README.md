# bullinger-patristic-annotations
Working files to create an annotated dataset of patristic references (Church Fathers) in Heinrich Bullinger's 16th-century correspondence

## Overview of Result (Annotated Dataset)

- **Total Annotations:** 
- **Reference Types:** Explicit citations, implicit allusions
- **Church Fathers Covered:** 
- **Time Period:** 
- **Language:** Latin

## Current Repository Structure
```
├── data/      
│   ├── cc-tei/                     # TEI-XML downloads from Corpus Corporum from Church Fathers tagged in Bullinger Digital
│   ├── church-fathers/             # Datafiles that are relevant for linking the Person TEI-Tags from Bullinger Digital to e.g. Corpus Corporum
│   ├── passim/                     # normalized JSON files of Bullinger letters + Patristic Corpora, PASSIM Output
│   ├── bullinger-filtered-letters/ # Subset of Bullinger letters with PER-Tag
│   ├── bullinger-plaintext/        # TXT files of all Bullinger letters for annotation in INCEpTION
│   ├── citations/                  # Lookup CSV files that resulted from Passim + Footnote Extraction
├── scripts/                        # Data processing scripts
├── docs/                           # Documentation and annotation method
```
## Data Sources

### Bullinger Correspondence Corpus
Not included in this repository. Access the full corpus at: [Bullinger Digital (GitHub)](https://github.com/stazh/bullinger-korpus-tei)

## Patristic Source Texts
Partly included in this repository. Accessed and downloaded at using "scripts/scrape-cc.ipynb"

## Related Resources
