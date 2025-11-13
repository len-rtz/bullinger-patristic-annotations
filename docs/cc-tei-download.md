# TEI XML Downloader for Church Fathers (Corpus Corporum)
The Python script "cc-tei-download" downloads TEI XML files of works and texts from the Corpus Corporum for a list of Church Fathers provided in a CSV file. It iterates over authors with valid Corpus Corporum IDs (cc_id) and saves the XML files in structured folders.

## Features
- Reads a CSV of Church Fathers with their CC IDs
- Iterates through each author and their works
- Downloads all accessible TEI XML texts for each work
- Normalizes server-side XML paths to public URLs
- Organizes XMLs in per-author folders

## Input
The CSV file church-fathers-gnd.cc.csv should have the following columns:

## Output
A folder called tei/ is created in the directory "../data/cc-tei". Each author has a dedicated folder named after their CC-ID.
All TEI XML files for each author’s accessible works are downloaded inside their folder.

## Features 
1. Reading the CSV file and selects rows with a non-empty cc_id
2. For each author, creating a folder for saving XML files
3. Fetching all works of an author with querying "https://mlat.uzh.ch/php_modules/navigate.php?load=<cc_id>&group_by=" to list works of the author
4. Fetching texts for each work with query ".../navigate.php?load=<author_id>/<work_id>&group_by=" to list individual texts
5. Extracting xml_file_path from the XML
6. Normalising paths to a public URL (https://mlat.uzh.ch/data/...)
7. Downloading and saving each TEI XML file in the author’s folder