# bullinger-patristic-annotations
Working files to create an annotated dataset of patristic references (Church Fathers) in Heinrich Bullinger's 16th-century correspondence.

## Overview of Result (Annotated Dataset)

- **Total Annotations:** 100 Annotations (50 explicit, 50 implicit) in 67 letters
- **Reference Types:** Explicit citations, implicit allusions
- **Church Fathers Mentioned:** 19 (Top 3: Augustinus (54%), Hieronymus (11%), Tertullian (9%))
- **Language:** mostly Latin, few examples Greek and Early New High German

## Methodology Creation of this Dataset
To create this dataset, three approaches of finding prospective letters were developed and explored. The full documentation of this methodology can be found in docs/methodology. 

## Repository Structure
```
├── annotations/                    # final annotated dataset in JSON and XMI
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
Full corpus at: [Corpus Corporum](https://mlat.uzh.ch/browser?path=/), parts are included in this repository. Accessed and downloaded at using "scripts/scrape-cc.ipynb"

## Related Resources
- [Bullinger Translations](https://github.com/bullinger-digital/bullinger-translations)
- [Open Greek & Latin](https://www.opengreekandlatin.org)
- [Patrologia Graeca](https://patrologia.graeca.org/patrologia/pg_https.html)
- [Digitale Versionen Heinrich Bullinger Briefwechsel (HBBW) der Bullinger Stiftung](http://teoirgsed.uzh.ch/SedWM.cgi?fn=Swd_Briefe&lng=1) 
- [Editionen Heinrich Bullinger Briefwechsel (HBBW)](https://www.tvz-verlag.ch/wissenschaft-und-studium-editionen/heinrich-bullinger/c-99)
- [Bibliothek der Kirchenväter](https://bkv.unifr.ch/de)
- [Bibleox](https://bibleox.com)