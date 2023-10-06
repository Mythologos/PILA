# Wordlist

**CLDF Metadata**: [Wordlist-metadata.json](./Wordlist-metadata.json)

**Sources**: [sources.bib](./sources.bib)

| property                                             | value                                                         |
|------------------------------------------------------|---------------------------------------------------------------|
| [dc:conformsTo](http://purl.org/dc/terms/conformsTo) | [CLDF Wordlist](http://cldf.clld.org/v1.0/terms.rdf#Wordlist) |


## <a name="table-formscsv"></a>Table [forms.csv](./forms.csv)

| property                                             | value                                                           |
|------------------------------------------------------|-----------------------------------------------------------------|
| [dc:conformsTo](http://purl.org/dc/terms/conformsTo) | [CLDF FormTable](http://cldf.clld.org/v1.0/terms.rdf#FormTable) |
| [dc:extent](http://purl.org/dc/terms/extent)         | 5812                                                            |


### Columns

| Name/Property                                                          | Datatype                            | Description                                                                                                                                                                                                                                                                                                                                                                                                                     |
|------------------------------------------------------------------------|-------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [ID](http://cldf.clld.org/v1.0/terms.rdf#id)                           | `string`                            | Primary key                                                                                                                                                                                                                                                                                                                                                                                                                     |
| [Language_ID](http://cldf.clld.org/v1.0/terms.rdf#languageReference)   | `string`                            | A reference to a language (or variety) the form belongs to<br>References [languages.csv::ID](#table-languagescsv)                                                                                                                                                                                                                                                                                                               |
| [Parameter_ID](http://cldf.clld.org/v1.0/terms.rdf#parameterReference) | `string`                            | A reference to the meaning denoted by the form                                                                                                                                                                                                                                                                                                                                                                                  |
| `Gloss_ID`                                                             | `string`                            | References [glosses.csv::ID](#table-glossescsv)                                                                                                                                                                                                                                                                                                                                                                                 |
| `Tag_ID`                                                               | `string`                            | References [tags.csv::ID](#table-tagscsv)                                                                                                                                                                                                                                                                                                                                                                                       |
| [Form](http://cldf.clld.org/v1.0/terms.rdf#form)                       | `string`                            | The written expression of the form. If possible the transcription system used for the written form should be described in CLDF metadata (e.g. via adding a common property `dc:conformsTo` to the column description using concept URLs of the GOLD Ontology (such as [phonemicRep](http://linguistics-ontology.org/gold/2010/phonemicRep) or [phoneticRep](http://linguistics-ontology.org/gold/2010/phoneticRep)) as values). |
| [Segments](http://cldf.clld.org/v1.0/terms.rdf#segments)               | list of `string` (separated by ` `) | 
| [Comment](http://cldf.clld.org/v1.0/terms.rdf#comment)                 | `string`                            | 
| [Source](http://cldf.clld.org/v1.0/terms.rdf#source)                   | list of `string` (separated by `;`) | References [sources.bib::BibTeX-key](./sources.bib)                                                                                                                                                                                                                                                                                                                                                                             |

## <a name="table-cognatescsv"></a>Table [cognates.csv](./cognates.csv)

| property                                             | value                                                                 |
|------------------------------------------------------|-----------------------------------------------------------------------|
| [dc:conformsTo](http://purl.org/dc/terms/conformsTo) | [CLDF CognateTable](http://cldf.clld.org/v1.0/terms.rdf#CognateTable) |
| [dc:extent](http://purl.org/dc/terms/extent)         | 5812                                                                  |


### Columns

| Name/Property                                                            | Datatype                            | Description                                                                                                    |                                                                                                   
|--------------------------------------------------------------------------|-------------------------------------|----------------------------------------------------------------------------------------------------------------|
| [ID](http://cldf.clld.org/v1.0/terms.rdf#id)                             | `string`                            | Primary key                                                                                                    |                                                                                                    
| [Form_ID](http://cldf.clld.org/v1.0/terms.rdf#formReference)             | `string`                            | References the form which is judged to belong to a cognate set.<br>References [forms.csv::ID](#table-formscsv) |
| [Cognateset_ID](http://cldf.clld.org/v1.0/terms.rdf#cognatesetReference) | `string`                            | References the cognate set a form is judged to belong to.                                                      |
| [Segment_Slice](http://cldf.clld.org/v1.0/terms.rdf#segmentSlice)        | list of `string` (separated by ` `) | Specifies the slice of morphemes of the form in case of partial cognacy.                                       |
| [Alignment](http://cldf.clld.org/v1.0/terms.rdf#alignment)               | list of `string` (separated by ` `) | The segments of the form aligned with respect to all other forms in the cognate set.                           |
| [Source](http://cldf.clld.org/v1.0/terms.rdf#source)                     | list of `string` (separated by `;`) | References [sources.bib::BibTeX-key](./sources.bib)                                                            |

## <a name="table-glossescsv"></a>Table [glosses.csv](./glosses.csv)

| property                                     | value |
|----------------------------------------------|-------|
| [dc:extent](http://purl.org/dc/terms/extent) | 233   |


### Columns

| Name/Property | Datatype | Description |
|---------------|----------|-------------|
| `ID`          | `string` | Primary key |
| `Analogy`     | `string` |             |
| `Archaism`    | `string` |             |
| `Borrowing`   | `string` |             |
| `Dead`        | `string` |             |
| `Inflection`  | `string` |             |
| `Morphology`  | `string` |             |
| `Paradigm`    | `string` |             |
| `Phonology`   | `string` |             |
| `Remodeling`  | `string` |             |
| `Comment`     | `string` |             |
| `Source`      | `string` |             |

## <a name="table-languagescsv"></a>Table [languages.csv](./languages.csv)

| property                                             | value                                                                   |
|------------------------------------------------------|-------------------------------------------------------------------------|
| [dc:conformsTo](http://purl.org/dc/terms/conformsTo) | [CLDF LanguageTable](http://cldf.clld.org/v1.0/terms.rdf#LanguageTable) |
| [dc:extent](http://purl.org/dc/terms/extent)         | 2                                                                       |


### Columns

| Name/Property                                                    | Datatype  | Description |
|------------------------------------------------------------------|-----------|-------------|
| [ID](http://cldf.clld.org/v1.0/terms.rdf#id)                     | `string`  | Primary key |
| [Name](http://cldf.clld.org/v1.0/terms.rdf#name)                 | `string`  |             |
| [Macroarea](http://cldf.clld.org/v1.0/terms.rdf#macroarea)       | `string`  |             | 
| [Latitude](http://cldf.clld.org/v1.0/terms.rdf#latitude)         | `decimal` |             |
| [Longitude](http://cldf.clld.org/v1.0/terms.rdf#longitude)       | `decimal` |             |
| [Glottocode](http://cldf.clld.org/v1.0/terms.rdf#glottocode)     | `string`  |             |
| [ISO639P3code](http://cldf.clld.org/v1.0/terms.rdf#iso639P3code) | `string`  |             | 

## <a name="table-tagscsv"></a>Table [tags.csv](./tags.csv)

| property                                     | value |
|----------------------------------------------|-------|
| [dc:extent](http://purl.org/dc/terms/extent) | 112   |


### Columns

| Name/Property      | Datatype | Description |
|--------------------|----------|-------------|
| `ID`               | `string` | Primary key |
| `Case`             | `string` |             | 
| `Degree`           | `string` |             | 
| `Gender`           | `string` |             | 
| `Inflection_Class` | `string` |             | 
| `Mood`             | `string` |             | 
| `Number`           | `string` |             | 
| `Part_of_Speech`   | `string` |             | 
| `Person`           | `string` |             | 
| `Tense`            | `string` |             |
| `Voice`            | `string` |             |
| `Comment`          | `string` |             | 
| `Source`           | `string` |             |