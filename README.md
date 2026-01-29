# bullinger-patristic-annotations
This repository contains the working files, data and results of a manually annotated dataset of patristic references in Heinrich Bullinger’s 16th-century correspondence, created to evaluate NLP methods for detecting text reuse and intertextual references.

## Anotated Dataset
- **Total Annotations:** 100 Annotations (50 explicit, 50 implicit) in 67 letters
- **Reference Types:** Explicit citations, implicit allusions
- **Church Fathers Mentioned:** 19 (Top 3: Augustinus (55%), Hieronymus (11%), Tertullian (9%))
- **Language:** mostly Latin, few examples Greek (1) and Early New High German (4)

### Jaccard Analysis 
Analysing the Jaccard coefficient of the lemmatised Latin annotations yields the following results. Explicit references have an average of 70% lexical overlap with the patristic sources while the annotated implicit references have only 12% lexical overlap with the source. Verbatims or close verbatism yield up to 100% lexical overlap while the highest lexical overlap for implicit references is 28% (for more detailed overview see [scripts/jaccard-scores.ipynb](scripts/jaccard-scores.ipynb)).

### Methodology of Annotation
To create this dataset, three approaches of finding prospective letters were developed and explored. The full documentation of this methodology can be found in [docs/methodology](docs/methodology.md). 

## Evaluation Dataset
As these annotations are intended to be used in a IR task, trying to find patristic references in Bullingers letters, a evaluation set was created (ref. [docs/evaluation-dataset.md](docs/evaluation-dataset.md)):
- [candidates.jsonl](annotations/evaluation_dataset/candidates.jsonl) - 97 unique patristic references
- [queries.jsonl](annotations/evaluation_dataset/queries.jsonl) - 100 Bullinger passages 

## Repository Structure
```
├── annotations/                    # final annotated dataset in JSON and XMI
│   ├── evaluation-dataset/         # from annotation stemming queries, candidates and their sources
├── data/      
│   ├── cc-tei/                     # TEI-XML downloads from Corpus Corporum from Church Fathers tagged in Bullinger Digital
│   ├── church-fathers/             # Datafiles that are relevant for linking the Person TEI-Tags from Bullinger Digital to e.g. Corpus Corporum
│   ├── passim/                     # normalised JSON files of Bullinger letters + Patristic Corpora, PASSIM Output
│   ├── bullinger-filtered-letters/ # Subset of Bullinger letters with PER-Tag
│   ├── bullinger-plaintext/        # TXT files of Bullinger letters for annotation in INCEpTION
│   ├── citations/                  # Lookup CSV files that resulted from Passim + Footnote Extraction
├── scripts/                        # Data processing scripts
├── docs/                           # Documentation and Methodology
```
## Data Sources

### Bullinger Correspondence Corpus
Full corpus at: [Bullinger Digital (GitHub)](https://github.com/stazh/bullinger-korpus-tei), parts (letters with PER-Tag) are included in this repository.

### Patristic Source Texts
Full corpus at: [Corpus Corporum](https://mlat.uzh.ch/browser?path=/), parts are included in this repository. Accessed and downloaded at using [`scripts/cc-tei-download.ipynb`](scripts/cc-tei-download.ipynb)

## Worth noting
- the letters were not fully annotated (not every knowable reference in a letter was annotated as such)
- the annotations do not exclusively relate to theological concepts but also reused metaphors (e.g. annotation in letter 11754) orignally used by church fathers

## Related Resources
- [Bullinger Translations](https://github.com/bullinger-digital/bullinger-translations)
- [Open Greek & Latin](https://www.opengreekandlatin.org)
- [Patrologia Graeca](https://patrologia.graeca.org/patrologia/pg_https.html)
- [Patristic Text Archive](https://pta.bbaw.de/en/)
- [Digitale Versionen Heinrich Bullinger Briefwechsel (HBBW) der Bullinger Stiftung](http://teoirgsed.uzh.ch/SedWM.cgi?fn=Swd_Briefe&lng=1) 
- [Editionen Heinrich Bullinger Briefwechsel (HBBW)](https://www.tvz-verlag.ch/wissenschaft-und-studium-editionen/heinrich-bullinger/c-99)
- [Bibliothek der Kirchenväter](https://bkv.unifr.ch/de)
- [Text Alignment Network](https://textalign.net)