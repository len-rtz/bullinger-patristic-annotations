# Selection of Letters to be annotated
To find prospective letters for annotation, three approaches were developed and explored. They are documented here.

## Methodology
### TEI-Tags and Footnotes (Explicit and Implicit Reference)
The Bullinger Digital project provides the letters in XML-TEI format with tagged mentioned person-tags. This was used as one starting point to find relevant letters and text passages for annotation. All citations around the mention of a church father was scraped and saved in a csv-file (ref. docs/TEI-tag-citation). This list was manually scanned worked through to find promissing implicit and explicit mentions of church fathers beliefs and theories.

#### Example:
| file_name |file_id |sentence_text |church_father_id | church_father_name | footnote_text |citation_parsed|
|---|---|---|---|---|---|---|
| 11171.xml	  | file11171  | Quemadmodum nanque deus per vos, fideleis et constantes ministros suos, verbi et invisibilis et visibilis synceritatem a fumis et fucis asseruit, ita et mendatiorum istorum nebulas clarissima veritatis luce dissipabit.  | p18700  |  Augustinus von Hippo |  Vgl. Augustins Bezeichnung der Sakramente als "verba visibilia" in: Contra Faustum, 19, 16 (CSEL XXV 513, 7-10) | Contra Faustum, 19, 16 (CSEL XXV 513, 7-10)  |			

### PASSIM Analysis (Explicit References)
To find explicit references (verbatims) the text reuse analysis library PASSIM was used. Therefore the works from all relevant church fathers were scraped from "Corpus Corporum". After chunking and normalisation those were compared to the normalised letters dataset of Bullinger Digital (ref. docs/passim). This yielded a list of explicit quotes / matching text that can be found in both, patristic sources and Bullingers letters, datasets. Within this list are lots of false positives due to bible verbatims in both datasets. This list was too manually scanned and worked through to find promissing explicit references of church fathers works in the letters.

#### Example:
| cluster_id | bullinger_id  | bullinger_text  | cluster_size  | patristic_id  |  patristic_text | patristic_author  | patristic_title  |
|---|---|---|---|---|---|---|---|
| 1011  |  file10041 | tsi deus caro et sanguis etsi nostris puriora idem tamen et substantia et forma qua ascendit talis etiam descensurus ut angeli adfirmant agnoscendis scilicet eis  | 2 |   |   |   |   |
| 1011  |   |   |  2 | toa0275.stoa026.opp-lat2_chunk103  | tsi sermo primarius caro et sanguis etsi nostris purior idem tamen et substantia et forma quam ascendit talis etiam descensurus ut angeli adfirmant agnoscendus scilicet eis   | Tertullianus150-230  |  De carnis resurrectione |


### Bullinger Editionen (Implicit References)
Manual Keyword Search, such as "Anspielung", "Taufe", "Eucharistie", "Sakramente")

### Example:
![Briefe von Januar bis März 1547 | TVZ., https://www.tvz-verlag.ch/buch/briefe-von-januar-bis-maerz-1547-9783290182786/?page_id=1, P. 138
](photos/Editionen-Example.png)

## Annotation Process
