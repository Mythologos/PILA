# PILA

**Authors**:
* Stephen Bothwell, David Chiang, Brian Krostenko (University of Notre Dame)
* Brian DuSell (ETH Zürich)

**Maintainer**: Stephen Bothwell

## Summary

This repository contains the **P**roto-**I**talic to **La**tin dataset. 
It models reflex-etymon relationships between these two languages. 
It also provides a variety of both phonetic and non-phonetic metadata.
All this is purposed toward work in computational historical linguistics, 
permitting deeper studies of this language pair on a systematic level relative to 
current findings in historical linguistics. 

### Statistics

The tables below summarize basic statistics of our dataset in its current version.
The first table describes statistics relative to the languages involved in the data.
The second table describes statistics which examine the relationship between the two languages.

| Object         | Latin     | Proto-Italic | All       |
|----------------|-----------|--------------|-----------|
| Forms          | 2857      | 2915         | 5772      |
| Phones         | 15956     | 18766        | 34721     |
| Phone Types    | 33        | 44           | 49        |
| Average Length | 5.6 ± 1.4 | 6.4 ± 1.8    | 6.0 ± 1.7 |

### Use 

**[[TODO: License]]**

## Background

**[[TODO: provide background description]]**

## Contents

This dataset follows the Cross-Linguistic Data Format (CLDF) specification. 
A detailed description generated from the metadata is available in the `data/cldf` folder.

As a high-level overview, the dataset contains six main files and a metadata file. 
We will describe each in turn:
1. `Wordlist-metadata.json`: a JSON file describing the structure of the other tables. 
It was generated by the PyCLDF library (Forkel) automatically.
It specifies what columns can and cannot contain and also denotes relationships between tables 
(*i.e.*, via primary and foreign keys) in a standardized format.
2. `forms.csv`: a CSV file containing information on both Latin and Proto-Italic forms.
Each form is connected with its corresponding language (`Language_ID`), meaning (`Parameter_ID`), 
gloss (`Gloss_ID`, if applicable), and tags (`Tag_ID`, if applicable). 
Its form as a whole (`Form`) and phoneme tokens (`Segments`) are also provided.
3. `cognates.csv`: a CSV file serving to link Latin and Proto-Italic forms in terms of their cognate relationships. 
Each form (`Form_ID`) links with a cognate set ID (`Cognateset_ID`).
4. `languages.csv`: a CSV file which contains basic information about the languages involved in this dataset, 
including languages IDs (`ID`), names (`Name`), approximate locations (`Latitude`, `Longitude`), and linguistic resource codes (`Glottocode`, `ISO639P3Code`).
5. `glosses.csv`: a CSV file which contains information about irregular changes and other special notations for our word forms. 
These are spread across nine categories which serve as booleans. 
These irregularities are generally explained in the `Comment` category,
and we use a tag for that irregularity in square brackets (*e.g.*, `[Analogy]`) to denote a reference to that irregularity type.
6. `tags.csv`: a CSV file which contains morphological information concerning the Latin forms involved in the dataset. 
We provide information such as `Part_of_Speech`, `Inflection_Class`, and a host of other morphological tags. 
7. `overlaps.csv`: a CSV file which links forms in our dataset to other datasets. 
Link datasets are named in the `Dataset` column and cited in the `Source` column. 
IDs for the PILA form are given in the `Form_ID` column and for the other dataset in the `Other_Form_ID` column.
8. `sources.bib`: a collection of resources in BibTeX format used in the process of creating this data. 
Keys in any `Source` column of any table of the dataset should cross-reference a key in this file.

**[[TODO: part-of-speech tags remain vague, and the notation used needs to be made clear. 
Might use the codes.csv file from CLDF to store such data and avoid the need to exhaustively explain it.]]**

## Contributing

This repository is intended to provide a single, definitive version of this dataset for future work and research. 
However, if there are issues or mistakes with the data, we would be glad to investigate them. 
Please open an issue to start a conversation on the subject. 

Any future updates of the dataset will be tagged with a version number so as to make it easy to designate and compare results. 
The current version is `v1.0`.

## Citations

### Our Work

To cite this dataset, please use the following paper citation:

```
...
```

### Others' Work

For the creation of this dataset, we primarily consulted Wiktionary in the formation of the initial dataset. 
We also used Michiel de Vaan's *Etymological Dictionary of Latin and the other Italic Languages* as a major supplementary resource.
We provide their citations here:

```
@misc{wiktionary2017,
  title = {Category:{{Latin}} Terms Derived from {{Proto-Italic}}},
  shorttitle = {Category},
  author = {{Wiktionary contributors}},
  year = {2017},
  month = jul,
  journal = {Wiktionary, the free dictionary},
  urldate = {2022-02-15},
  abstract = {Fundamental \guillemotright{} All languages \guillemotright{} Latin \guillemotright{} Terms by etymology \guillemotright{} Terms derived from other languages \guillemotright{} Indo-European languages \guillemotright{} Italic languages \guillemotright{} Proto-Italic Latin terms that originate from Proto-Italic.},
  copyright = {Creative Commons Attribution-ShareAlike License},
  langid = {english},
  annotation = {Page Version ID: 47078291},
}

@book{deVaan2008,
  title = {Etymological {{Dictionary}} of {{Latin}} and the Other {{Italic Languages}}},
  author = {{de Vaan}, Michiel},
  year = {2008},
  series = {Leiden {{Indo-European Etymological Dictionary Series}}},
  number = {7},
  publisher = {{Brill}},
  address = {{Leiden; Boston}},
  isbn = {978-90-04-16797-1},
  langid = {english},
  keywords = {Italic languages and dialects -- Etymology -- Dictionaries,Latin language -- Etymology -- Dictionaries,Proto-Indo-European language -- Etymology -- Dictionaries}
}
```

We also cite a variety of other works which aided in the development of this data. 
For these works, see the `data/cldf/sources.bib` file. 
Sources are linked with their contributed information where applicable in `Source` columns.

Regarding the discussions within this file, papers cited here not otherwise included in our cited works are as follows:

``` 
@misc{forkelPycldfPythonLibrary,
  title = {Pycldf: {{A}} Python Library to Read and Write {{CLDF}} Datasets},
  shorttitle = {Pycldf},
  author = {Forkel, Robert},
  urldate = {2023-10-05},
  copyright = {Apache Software License},
  keywords = {linguistics}
}
```