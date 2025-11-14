# Church Fathers Dataset Documentation

## Overview
The folder 'data/church-fathers' contains the data that are relevant for linking the Person TEI-Tags from Bullinger Digital to broader patristic text collections and identifiers.

### Files
- **'persons.xml'**  
  A direct download of the Bullinger Digital Edition’s TEI person index, originally located at:  
  [https://github.com/stazh/bullinger-korpus-tei/blob/main/data/index/persons.xml](https://github.com/stazh/bullinger-korpus-tei/blob/main/data/index/persons.xml)

- **'manual-church-fathers.csv'**  
  A manually curated list of Church Fathers, prepared using data from external scholarly sources and the Bullinger TEI person index.

- **'church-fathers-gnd.csv'**
  The result of the script researching the entries of 'manual-church-fathers.csv' in 'persons.xml' and extracting the GND identifier for each.

- **'manual-church-fathers-gnd.csv'**
  The manually completed list of church fathers with their GND-ID and Wikipedia article link.

- **'church-fathers-gnd-cc.csv'**
  The result of the script that loads the 'manual-church-fathers-gnd.csv', queries the Corpus Corporum database for each church father using their GND ID, extracts the corresponding CC ID


## Data Sources and Methodology

### 1. Source Overview
- **Primary reference list:**  
  [BKV (Bibliothek der Kirchenväter) – Overview of Works and Authors](https://bkv.unifr.ch/de/works)

- **Secondary reference lists:** https://www.ccel.org/fathers, http://chrysologus.blogspot.com/2011/06/who-are-fathers-of-church-chronological.html, https://en.wikipedia.org/wiki/List_of_Church_Fathers 

- **Linked TEI person records:**  
  [Bullinger Digital Edition — `persons.xml`](https://github.com/stazh/bullinger-korpus-tei/blob/main/data/index/persons.xml)

### 2. Curation Process
1. Scanned the list of Church Fathers from the BKV project’s overview page
2. For each author, manually checked whether a corresponding TEI `<person>` entry exists in the Bullinger Digital corpus (`persons.xml`). It was chosen to do this manually, as there are many alternative writings to each church fathers name
3. When a match was found, the relevant PER-ID was extracted and recorded in a CSV file
4. The entries were cross-checked along other available overview lists of church fathers (ref. secondary reference lists)
5. Each entry in `manual-church-fathers.csv` therefore includes: 
   - Bullinger TEI person ID
   - one variation of fore- and surname

### 3. Script for Extracting GND and Wikipedia identifiers 
The 'persons.xml' index from the Bullinger Digital Project contains general identifiers such as GND entries and Wikipedia URLs. The script 'script/church-fathers.ipynb' scans this index for each ID listed in 'manual-church-fathers.csv' and extracts the corresponding GND ID and Wikipedia URL, when available. The results are saved in 'church-fathers-gnd.csv'.

Eight Church Fathers without a GND entry remained; these were added manually in 'manual-church-fathers-gnd.csv'. Missing Wikipedia links were also supplemented where possible, and duplicate entries were removed.

The csv-file 'manual-church-fathers-gnd.csv' resulting from that script and manual edits serves as a bridge between:
- **Bullinger Digital’s TEI person data**, and  
- **Corpus Corporum** or other relevant external sources
as enabling GND-based cross-referencing allows automated retrieval of texts and metadata for the same authors from external corpora.  

### 4. Script for Extracting CC ID from Corpus Corporum (CC)
In order to scrape available works / full texts of each church father mentioned in the Bullinger Digital Corpus, this script searches the GND for each church father on https://mlat.uzh.ch/. Therefore the 'manual-church-fathers-gnd.csv' is loaded and a HTTP search request for each 'gnd_id' is looped through each Church Father in the CSV. Out of the XML response the  <cc_idno> element is extracted. Lastly the GND match is verified by comparing the <external> element "DNB" attribute to the GND-ID of the search. The result is a CSV-file including (Bullinger-PER-)ID, Name, GND ID, and CC ID.