# Annotation Schema
## Layer 1: Patristic Reference Span (Primary Annotation)
- **Layer Type**: Span 
- **Layer Name**: PatristicReference
- **Description**: Marks the text in letter that contains a patristic reference

### Features of Layer 1
#### Feature 1: reference_type 
- **Type**: Single-choice (String)
- **Tagset**: EXPLICIT (direct quotation or close paraphrase), IMPLICIT (conceptual reference without direct wording)
- **Description**: Type of reference based on textual similarity

#### Feature 2: church_father 
- **Type**: Single-choice (String)
- **Tagset**: TEI PER-ID's from Bullinger-Digital
- **Description**: Which Church Father is being referenced

#### Feature 3: patristic_work
- **Type**: Single-choice (String)
- **Tagset**: ID's from Patristic Corpus
- **Description**: Which Church Fathers work is being referenced

#### Feature 4: patristic_text
- **Type**: Free text (String) - Long text
- **Description**: The actual text from the patristic source being referenced

#### Feature 5: confidence
- **Type**: Single-choice (String)
- **Tagset**: HIGH, MEDIUM, LOW
- **Description**: Annotator's confidence level

#### Feature 6: detection_source
- **Type**: Single-choice (String)
- **Tagset**: TEI (found by accessing PER-TEI tags), SCHOLAR (from scholarship reading), PASSIM (found using PASSIM)
- **Description**: How this candidate was identified

