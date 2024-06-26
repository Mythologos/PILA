# PILA

**Authors**:
* Stephen Bothwell, David Chiang, Brian Krostenko (University of Notre Dame)
* Brian DuSell (ETH Zürich)

**Maintainer**: Stephen Bothwell

## Summary

This repository contains the **P**roto-**I**talic to **La**tin (PILA) dataset. 
It models reflex-etymon relationships between these two languages, 
promoting deeper study of historical linguistics in the Italic region. 
It also provides a variety of both phonetic and non-phonetic metadata.
All this is purposed toward work in computational historical linguistics, 
permitting deeper studies of this language pair on a systematic level. 

For the code that was used to create this dataset from raw TSV data and 
further tools used to analyze, study, and apply it, see the [PILA-Code](https://github.com/Mythologos/PILA-Code) repository.

### Statistics

The tables below summarize basic statistics of our dataset in its current version.
The first table describes statistics relative to the languages involved in the data.
The second table describes statistics which examine the relationship between the two languages.

| Object         | Latin     | Proto-Italic | All       |
|----------------|-----------|--------------|-----------|
| Forms          | 2860      | 2916         | 5776      |
| Phones         | 15974     | 18779        | 34753     |
| Phone Types    | 33        | 41           | 48        |
| Average Length | 5.6 ± 1.4 | 6.4 ± 1.8    | 6.0 ± 1.7 |

### Use 

This dataset is licensed under a Creative Commons Attribution-Sharealike 4.0 International (CC-BY-SA) license. 
For more information, please see https://creativecommons.org/licenses/by-sa/4.0/.

## Contents

This dataset follows the Cross-Linguistic Data Format (CLDF) specification. 
A detailed description generated from the metadata is available in the `data/cldf` folder.

As a high-level overview, the dataset contains seven main files, a bibliography, and a metadata file. 
We describe each in turn:
1. `Wordlist-metadata.json`: a JSON file describing the structure of the other tables. 
It was generated by the PyCLDF library (Forkel, 2023) automatically.
It specifies what columns can and cannot contain and also denotes relationships between tables 
(*i.e.*, via primary and foreign keys) in a standardized format.
2. `forms.csv`: a CSV file containing information on both Latin and Proto-Italic forms.
Each form is connected with its corresponding language (`Language_ID`), meaning (`Parameter_ID`), lemma (`Lemma_ID`, if applicable), 
gloss (`Gloss_ID`, if applicable), and morphological tags (`Tag_ID`, if applicable). 
Its form as a whole (`Form`) and tokenized phones (`Segments`) are also provided. 
3. `cognates.csv`: a CSV file serving to link Latin and Proto-Italic forms in terms of their cognate relationships. 
Each form (`Form_ID`) links with a cognate set ID (`Cognateset_ID`).
4. `languages.csv`: a CSV file which contains basic information about the languages involved in this dataset, 
including languages IDs (`ID`), names (`Name`), approximate locations (`Latitude`, `Longitude`), and linguistic resource codes (`Glottocode`, `ISO639P3Code`).
5. `lemmata.csv`: a CSV file which contains orthographic lemmata (`Name`) and an ID (`ID`) for each lemmata.
Currently, these are only stored for and linked to Latin forms in `forms.csv`.
6. `glosses.csv`: a CSV file which contains information about irregular changes and other special notations for our word forms. 
These are spread across five categories which serve as booleans. 
These irregularities are generally explained in the `Comment` category,
and we use a tag for that irregularity in square brackets (*e.g.*, `[Association]`) to denote a reference to that irregularity type.
7. `tags.csv`: a CSV file which contains sets of morphological information represented in PILA's Latin forms. 
These tags are roughly based on Perseus' style of morphological tagging (Crane, 1991), 
although it has been adapted to reflect the isolated environments of these forms.
8. `overlaps.csv`: a CSV file which links forms in our dataset to other datasets. 
Linked datasets are named in the `Dataset` column and cited in the `Source` column. 
IDs for the PILA form are given in the `Form_ID` column and for the other dataset in the `Other_Form_ID` column.
9. `sources.bib`: a collection of resources in BibTeX format used in the process of creating this data. 
Keys in any `Source` column of any table of the dataset should cross-reference a key in this file.

Below, we provide a few subsections on finer details of some our datasets, such as notation or class information.
Other essential statistics and details regarding our dataset can be found in the automatically-generated `README.md` file, 
courtesy of PyCLDF (Forkel, 2023), in the `cldf` directory.

### Forms

In this subsection, we discuss our data transcription schemes. 
Originally, our etymon-reflex pair data was sourced from Wiktionary (Wiktionary Contributors, 2017).
Because of the relatively direct connections between Latin and Proto-Italic orthography and their phonetics, 
we chose to largely preserve the forms as-is for our dataset to avoid re-transcribing all the data. 

However, since different contributors applied different transcription schemes for Proto-Italic forms, 
we had to perform a number of passes to make all the data consistent with itself. 
We attempted to follow modern standards of Italic historical linguistics--
in particular, de Vaan's *Etymological Dictionary of Latin and the other Italic Languages* (de Vaan, 2008).
However, at times, we diverged from de Vaan's (or Wiktionary contributors') notation to better reflect the underlying phonetics.

For more details about specific changes we made to reflect phonetics, see Section 4.2.3 of our paper.

### Glosses

In this subsection, we describe the types of irregular changes which we flag in our data. 
Our `glosses.csv` file contains five such types, each represented as a boolean flag. 
We define each and provide an example, showing both the form that resulted from Proto-Italic in Latin and 
one that would have been expected if the phenomenon at hand did not have an effect:
1. **Association**: A form with a change attributable to its association with another word or semantic set.
    - \*kleiments > cleːmeːns, and not cliːmeːns
2. **Borrowing**: A form with a sound change different from standard Latin and/or from another Italic dialect.
    - \*gᵂoːs > boːs, and not voːs 
3. **Morphology**: A form where morphosemantics undid, blocked, or otherwise interfered with expected sound changes.
    - \*mensen > meːnsis, and not meːnsen
4. **Paradigm Leveling**: A form which exhibits changes taken from another part of its own paradigm or lexical family.
    - \*weznos > veːris, and not veːnus
5. **Phonology**: A form with an uncommon or unexpected phonological phenomenon.
    - \*dikitos > digitus, and not dicitus

### Overlaps

In this subsection, we indicate what was used to index each dataset that was involved in dataset compatibility study. 
With this information, the indices in `overlaps.csv` can be used to connect data between PILA and these datasets. 

The meaning of each entry index for the non-PILA datasets is as follows:
- *Ab Initio* (Ciobanu and Dinu, 2014; Ciobanu and Dinu, 2018): a zero-based row index. 
- *Ab Antiquo*: Additions (Meloni *et al.*, 2021): a zero-based row index.
- *Ab Antiquo*: Full (Meloni *et al.*, 2021): a zero-based row index.
- Coglust (Wu and Yarowsky, 2018): a zero-based row index and a zero-based column index, separated by a dash.
- CogNet (Batsuren *et al.*, 2019; 2022): a `Concept ID` value, which is a mixture of alphanumeric characters. 
Multiple rows containing the same Latin term connect using that ID.
- IE-CoR (Heggarty *et al.*, 2022): an `ID` with either an `f` or a `cs` appended to it. 
The `f` is used when the ID comes from the FormTable; the `cs` is used when the ID comes from the CognatesetTable.
- IELEX (Linguistics Research Center, 2024): a numerical `id` from the table containing reflexes.
- JAMBU (Arora *et al.*, 2023): an `ID` from the FormTable, which is a set of two numbers separated by a dash.
- Romance (Luo, 2022): a collection of semicolon-separated zero-based row indices.

### Parameters

Although we do store a `Parameter_ID`, we do not have a `parameters.csv` table with which meanings of Latin and Proto-Italic forms correspond. 
This is mainly because our focus for PILA has been phonological and morphological rather than semantic. 
However, the IDs used correspond to rows of our original table, 
meaning that all forms with the same ID still should be related in meaning. 
The handling of `Parameter_ID` may be changed in future versions of PILA to accommodate for studies examining the relationship between phonological changes and semantics, 
as well as to adhere more closely to norms of CLDF datasets.

### Tags

Our dataset supplies multiple inflected forms of certain Latin and Proto-Italic words, 
permitting studies of sound change to account for changes in stems, in morphemes, and at the boundaries between stems and morphemes. 
To indicate the forms that were selected, we supply a set of morphological tags in `tags.csv`. 
We base our tags on those for Morpheus, the morphological analyzer for the Perseus Project (Crane, 1991). 
See [this file](https://github.com/PerseusDL/treebank_data/blob/master/v2.1/Latin/TAGSET.txt) for the Morpheus tagset.
We make adjustments due to the fact that our forms have no sentential context.
We also add the *inflection class* category, rounding out the number of morphological attributes to 10.

Our morphological tagging categories are as follows, presented in alphabetical order: 
case, degree, gender, inflection class, mood, number, part-of-speech, person, tense, and voice.
We currently have the following categories available:
- **Case**: Nominative, Genitive, Dative, Accusative, Ablative, Locative, Vocative, Any
- **Degree**: Positive, Comparative, Superlative
- **Gender**: Masculine, Feminine, Neuter, Masculine/Feminine, Masculine/Neuter, Feminine/Neuter, Masculine/Feminine/Neuter
- **Inflection Class**: 1, 2, 3, 4, 5, Special
  - Currently, the same values are used for nominal and verbal inflections; 
  as a result, one should take care to consider the part-of-speech when determining whether the class is talking about a declension (nominal) or conjugation (verbal).
  - The "Special" class is used for irregular paradigms.
- **Mood**: Indicative, Imperative, Subjunctive, Infinitive
- **Number**: Singular, Plural
- **Part-of-Speech**: Adjective, Adverb, Conjunction, Determiner, Interjection, Noun, Numeral, Participle, Preposition, Pronoun, Verb
- **Person**: 1st, 2nd, 3rd
- **Tense**: Present, Imperfect, Future, Perfect, Pluperfect, Future Perfect
- **Voice**: Active, Deponent, Passive

Note that these attributes have been created to suit the needs of the data and may not be feature-complete. 
At the same time, attributes have been added that are currently not present in our data to support additional data.
Moreover, certain forms could be different parts of speech in different contexts.
If the data point was derived from Wiktionary, we checked to see whether there was a specific part-of-speech corresponding to an etymology. 
Otherwise, we manually selected a part-of-speech to apply for the time being.

This tagging system may be subject to change in future versions of PILA, particularly in light of modern standards of Latin morphological tagging. 
For instance, see [the tagging scheme](https://github.com/CIRCSE/LT4HALA/blob/master/2022/data_and_doc/EvaLatin_2022_guidelines-TEST.pdf) 
drafted for the EvaLatin 2022 shared task (Sprugnoli *et al.*, 2022).

## Contributing

This repository is intended to provide a single, definitive version of this dataset for future work and research. 
However, if there are issues or mistakes with the data, we would be glad to investigate them. 
Please open an issue to start a conversation on the subject. 

Any future updates of the dataset will be tagged with a version number to make it easy to designate and compare results. 
The current version is `v1.0.0`, and changes in version should follow the general principles of [semantic versioning](https://semver.org/).

## Citations

### Our Work

To cite this dataset, please use the following paper's citation:

```
@inproceedings{bothwellPILA2024,
  title = {{{PILA}}: {{A}} Historical-Linguistic Dataset of {{Proto-Italic}} and {{Latin}}},
  booktitle = {Proceedings of the {{The}} 2024 {{Joint International Conference}} on {{Computational Linguistics}}, {{Language Resources}} and {{Evaluation}}},
  author = {Bothwell, Stephen and DuSell, Brian and Chiang, David and Krostenko, Brian},
  year = "2024",
  month = may,
  publisher = {European Language Resources Association},
  address = {Turin, Italy},
  abstract = {Computational historical linguistics seeks to systematically understand processes of sound change, including during periods at which little to no formal recording of language is attested. At the same time, few computational resources exist which deeply explore phonological and morphological connections between proto-languages and their descendants. This is particularly true for the family of Italic languages. To assist historical linguists in the study of Italic sound change, we introduce the Proto-Italic to Latin (PILA) dataset, which consists of roughly 3,000 pairs of forms from Proto-Italic and Latin. We provide a detailed description of how our dataset was created and organized. Then, we exhibit PILA's value in two ways. First, we present baseline results for PILA on a pair of traditional computational historical linguistics tasks. Second, we demonstrate PILA's capability for enhancing other historical-linguistic datasets through a dataset compatibility study.},
  langid = {english},
  annotation = {To appear.}
}
```

### Others' Work

For the creation of this dataset, we primarily consulted Wiktionary in the formation of the initial dataset. 
We also used Michiel de Vaan's *Etymological Dictionary of Latin and the other Italic Languages* as a major supplementary resource.
Furthermore, we consulted a variety of etymological dictionaries and grammars in the process of creating this dataset.
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

@book{baldiFoundationsLatin2002,
  title = {The {{Foundations}} of {{Latin}}},
  author = {Baldi, Philip},
  year = {2002},
  publisher = {{Mouton de Gruyter}},
  address = {{Berlin; New York}},
  langid = {english}
}

@book{ernoutDictionnaireEtymologiqueLangue2001,
  title = {Dictionnaire \'Etymologique de La Langue {{Latine}}},
  author = {Ernout, Alfred and Meillet, Alfred},
  year = {2001},
  publisher = {{Klinksieck}},
  address = {{Paris}}
}

@book{leumannLateinscheLautUnd1977,
  title = {Lateinsche {{Laut-}} Und {{Formenlehre}}},
  author = {Leumann, Manu},
  year = {1977},
  publisher = {{C.H. Beck}},
  address = {{Munich}}
}

@book{meiserHistorischeLautUnd2010,
  title = {Historische {{Laut-}} Und {{Formenlehre}} Der Lateinischen {{Sprache}}},
  author = {Meiser, Gerhard},
  year = {2010},
  publisher = {{Wissenschaftliche Buchgesellschaft}},
  address = {{Darmstadt}}
}

@book{sihlerNewComparativeGrammar1995,
  title = {New {{Comparative Grammar}} of {{Greek}} and {{Latin}}},
  author = {Sihler, Andrew},
  year = {1995},
  publisher = {{Oxford University Press}},
  address = {{New York; Oxford}}
}

@book{waldeLateinischesEtymologischesWorterbuch1938,
  title = {Lateinisches Etymologisches {{W\"orterbuch}}},
  author = {Walde, Alois and Hofmann, J.B.},
  year = {1938},
  publisher = {{Carl Winter}},
  address = {{Heidelberg}}
}
```

We also cite a variety of other works which aided in the development of this data. 
For these works, see the `data/cldf/sources.bib` file. 
Sources are linked with their contributed information where applicable in `Source` columns.

Regarding the discussions within this file, papers cited here not otherwise included in our cited works are as follows:

``` 
@inproceedings{aroraJambuHistoricalLinguistic2023,
  title = {{{JAMBU}}: {{A}} Historical Linguistic Database for {{South Asian}} Languages},
  booktitle = {Proceedings of the 20th {{SIGMORPHON}} Workshop on Computational Research in Phonetics, Phonology, and Morphology},
  author = {Arora, Aryaman and Farris, Adam and Basu, Samopriya and Kolichala, Suresh},
  year = {2023},
  month = jul,
  pages = {68--77},
  xpublisher = {{Association for Computational Linguistics}},
  xaddress = {{Toronto, Canada}},
  doi = {10.18653/v1/2023.sigmorphon-1.8},
  abstract = {We introduce JAMBU, a cognate database of South Asian languages which unifies dozens of previous sources in a structured and accessible format. The database includes nearly 287k lemmata from 602 lects, grouped together in 23k sets of cognates. We outline the data wrangling necessary to compile the dataset and train neural models for reflex prediction on the Indo- Aryan subset of the data. We hope that JAMBU is an invaluable resource for all historical linguists and Indologists, and look towards further improvement and expansion of the database.}
}

@inproceedings{batsurenCogNetLargescaleCognate2019,
  title = {{{CogNet}}: {{A}} Large-Scale Cognate Database},
  booktitle = {Proceedings of the 57th Annual Meeting of the Association for Computational Linguistics},
  author = {Batsuren, Khuyagbaatar and Bella, G{\'a}bor and Giunchiglia, Fausto},
  year = {2019},
  month = jul,
  pages = {3136--3145},
  xpublisher = {{Association for Computational Linguistics}},
  xaddress = {{Florence, Italy}},
  doi = {10.18653/v1/P19-1302},
  abstract = {This paper introduces CogNet, a new, large-scale lexical database that provides cognates -words of common origin and meaning- across languages. The database currently contains 3.1 million cognate pairs across 338 languages using 35 writing systems. The paper also describes the automated method by which cognates were computed from publicly available wordnets, with an accuracy evaluated to 94\%. Finally, it presents statistics about the cognate data and some initial insights into it, hinting at a possible future exploitation of the resource by various fields of lingustics.}
}

@article{batsurenLargeEvolvingCognate2022,
  title = {A Large and Evolving Cognate Database},
  author = {Batsuren, Khuyagbaatar and Bella, G{\'a}bor and Giunchiglia, Fausto},
  year = {2022},
  month = mar,
  journal = {Language Resources and Evaluation},
  volume = {56},
  number = {1},
  pages = {165--189},
  issn = {1574-0218},
  doi = {10.1007/s10579-021-09544-6},
  abstract = {We present CogNet, a large-scale, automatically-built database of sense-tagged cognates\textemdash words of common origin and meaning across languages. CogNet is continuously evolving: its current version contains over 8~million cognate pairs over 338 languages and 35~writing systems, with new releases already in preparation. The paper presents the algorithm and input resources used for its computation, an evaluation of the result, as well as a quantitative analysis of cognate data leading to novel insights on language diversity. Furthermore, as an example on the use of large-scale cross-lingual knowledge bases for improving the quality of multilingual applications, we present a case study on the use of CogNet for bilingual lexicon induction in the framework of cross-lingual transfer learning.}
}

@inproceedings{ciobanuBuildingDatasetMultilingual2014,
  title = {Building a Dataset of Multilingual Cognates for the {{Romanian}} Lexicon},
  booktitle = {Proceedings of the Ninth International Conference on Language Resources and Evaluation ({{LREC}})},
  author = {Ciobanu, Alina Maria and Dinu, Liviu},
  year = {2014},
  month = may,
  pages = {1038--1043},
  xpublisher = {{European Language Resources Association (ELRA)}},
  xaddress = {{Reykjavik, Iceland}},
  abstract = {Identifying cognates is an interesting task with applications in numerous research areas, such as historical and comparative linguistics, language acquisition, cross-lingual information retrieval, readability and machine translation. We propose a dictionary-based approach to identifying cognates based on etymology and etymons. We account for relationships between languages and we extract etymology-related information from electronic dictionaries. We employ the dataset of cognates that we obtain as a gold standard for evaluating to which extent orthographic methods can be used to detect cognate pairs. The question that arises is whether they are able to discriminate between cognates and non-cognates, given the orthographic changes undergone by foreign words when entering new languages. We investigate some orthographic approaches widely used in this research area and some original metrics as well. We run our experiments on the Romanian lexicon, but the method we propose is adaptable to any language, as far as resources are available.},
  url = {https://aclanthology.org/L14-1184/}
}

@inproceedings{ciobanuInitioAutomaticLatin2018,
  title = {Ab {{Initio}}: {{Automatic Latin}} Proto-Word Reconstruction},
  booktitle = {Proceedings of the 27th {{International Conference}} on {{Computational Linguistics}}},
  author = {Ciobanu, Alina Maria and Dinu, Liviu P.},
  year = {2018},
  month = aug,
  volume = {27},
  pages = {1604--1614},
  publisher = {{Association for Computational Linguistics}},
  address = {{Santa Fe, New Mexico, USA}},
  abstract = {Proto-word reconstruction is central to the study of language evolution. It consists of recreating the words in an ancient language from its modern daughter languages. In this paper we investigate automatic word form reconstruction for Latin proto-words. Having modern word forms in multiple Romance languages (French, Italian, Spanish, Portuguese and Romanian), we infer the form of their common Latin ancestors. Our approach relies on the regularities that occurred when the Latin words entered the modern languages. We leverage information from all modern languages, building an ensemble system for proto-word reconstruction. We use conditional random fields for sequence labeling, but we conduct preliminary experiments with recurrent neural networks as well. We apply our method on multiple datasets, showing that our method improves on previous results, having also the advantage of requiring less input data, which is essential in historical linguistics, where resources are generally scarce.},
  langid = {english}
}

@article{craneGeneratingParsingClassical1991,
  title = {Generating and Parsing {{Classical Greek}}},
  author = {Crane, Gregory},
  year = {1991},
  month = jan,
  journal = {Literary and Linguistic Computing},
  volume = {6},
  number = {4},
  pages = {243--245},
  issn = {0268-1145},
  doi = {10.1093/llc/6.4.243},
  urldate = {2024-03-25},
  abstract = {This paper will describe the development of a rule based system for the analysis of Greek morphology and provide background for a Greek morphological database created by this system. While this paper focuses on classical Greek, a highly inflected Indo-European language, our work was intended from the outset to provide a case study that would illustrate the problems of morphological analysis and the possibilities that a working morphological system might open up for research M{\textasciiacute}uch of the impetus for out work on Greek morphological sprang from work in Akkadian and Sumerian, and from the frustrations that scholars inevitably face when they attempt to work with primary material beyond their immediate area of specialization. A system for morphological analysis is both a tool for those specializing in the target language and a gateway whereby those from other disciplines may enter more deeply the primary soruce texts of ancient Greece.Working with a database of 40,000 stems, 13,000 inflections, and 2,500 irregular forms, Morpheus, the parser described in this paper has (as of October 1990) been used to analyze roughly 3,000,000 words, including texts in a variety of dialects from the eighth century BC to the second century AD and has been used to create a morphological database. This morphological database plays a major role in binding together 40 megabytes of primary sources within the hypermedia database on ancient Greece developed by the Perseus Project.1 At the same time, the database exists as a separate entity distinct from the larger Perseus database, and we plan in early 1992 to distribute for linguistic analysis a fuller version of the database, covering those Greek texts in the Thesaurus Linguae Graecae from Homer to the fourth centuryThis paper deals with the reasons why this parser was developed and the problems that we encountered. A parser for Greek morphology was not new even in 1984 when we began, but out parser was designed to control phenomena (such as Greek diacritics and dialects) that earlier work had not addressed. This paper will describe the initial purposes and rationale for devising our parser, and the problems that we encountered in striving for a higher level of precision. Its purpose is to predict problems and highlight possible solutions for those working in Greek and to serve as an example of one approach for those working in other languages.}
}

@misc{forkelPycldfPythonLibrary,
  title = {Pycldf: {{A}} Python Library to Read and Write {{CLDF}} Datasets},
  shorttitle = {Pycldf},
  author = {Forkel, Robert},
  urldate = {2023-10-05},
  copyright = {Apache Software License},
  keywords = {linguistics}
}

@article{heggartyLanguageTreesSampled2023,
  title = {Language Trees with Sampled Ancestors Support a Hybrid Model for the Origin of {{Indo-European}} Languages},
  author = {Heggarty, Paul and Anderson, Cormac and Scarborough, Matthew and King, Benedict and Bouckaert, Remco and Jocz, Lechos{\l}aw and K{\"u}mmel, Martin Joachim and J{\"u}gel, Thomas and Irslinger, Britta and Pooth, Roland and Liljegren, Henrik and Strand, Richard F. and Haig, Geoffrey and Mac{\'a}k, Martin and Kim, Ronald I. and Anonby, Erik and Pronk, Tijmen and Belyaev, Oleg and {Dewey-Findell}, Tonya Kim and Boutilier, Matthew and Freiberg, Cassandra and Tegethoff, Robert and Serangeli, Matilde and Liosis, Nikos and Stro{\'n}ski, Krzysztof and Schulte, Kim and Gupta, Ganesh Kumar and Haak, Wolfgang and Krause, Johannes and Atkinson, Quentin D. and Greenhill, Simon J. and K{\"u}hnert, Denise and Gray, Russell D.},
  year = {2023},
  journal = {Science},
  volume = {381},
  number = {6656},
  pages = {eabg0818},
  publisher = {{American Association for the Advancement of Science}},
  doi = {10.1126/science.abg0818},
  urldate = {2023-09-12},
  abstract = {The origins of the Indo-European language family are hotly disputed.~Bayesian phylogenetic analyses of core~vocabulary have~produced~conflicting results,~with some supporting a farming~expansion out of Anatolia \textasciitilde 9000~years before present (yr B.P.),~while others support a spread with~horse-based pastoralism out of the Pontic-Caspian Steppe \textasciitilde 6000~yr B.P.~Here we present an extensive database of Indo-European core vocabulary that eliminates past inconsistencies in cognate coding. Ancestry-enabled phylogenetic analysis of this dataset indicates that few ancient languages are direct ancestors of modern clades and produces a root age of \textasciitilde 8120 yr B.P. for the family. Although this date is not consistent with the Steppe hypothesis, it does not rule out an initial homeland south of the Caucasus, with a subsequent branch northward onto the steppe and then across Europe. We reconcile this hybrid hypothesis with recently published ancient~DNA~evidence from the steppe and the northern Fertile Crescent.~ Languages of the Indo-European family are spoken by almost half of the world?s population, but their origins and patterns of spread are disputed. Heggarty et al. present a database of 109 modern and 52 time-calibrated historical Indo-European languages, which they analyzed with models of Bayesian phylogenetic inference. Their results suggest an emergence of Indo-European languages around 8000 years before present. This is a deeper root date than previously thought, and it fits with an initial origin south of the Caucasus followed by a branch northward into the Steppe region. These findings lead to a ?hybrid hypothesis? that reconciles current linguistic and ancient DNA evidence from both the eastern Fertile Crescent (as a primary source) and the steppe (as a secondary homeland). ?SNV Indo-European languages emerged south of the Caucasus around 8300 years ago, followed by an expansion northward to the Steppe regions.}
}

@misc{lrcIELEX2024,
  type = {Lexicon},
  title = {Indo-{{European Lexicon}}: {{PIE}} Etyma and {{IE}} Reflexes},
  shorttitle = {{{IELEX}}},
  author = {{Linguistics Research Center}},
  year = {2024},
  month = jan,
  urldate = {2024-01-05},
  url = {https://lrc.la.utexas.edu/lex},
  langid = {english},
}

@phdthesis{luoAutomaticMethodsSound2021,
  title = {Automatic Methods for Sound Change Discovery},
  author = {Luo, Jiaming},
  year = {2021},
  month = sep,
  urldate = {2024-03-01},
  abstract = {Describing the phonological history of languages has been a central topic in historical linguistics. In this thesis, we develop automatic methods to discover patterns of sound change in different settings of input and output conditions. More specifically, we focus on three challenging tasks: (1) automatic decipherment, (2) automatic decipherment in unsegmented scripts, and (3) automatic sound law induction. We show that a careful model design that implements historical linguists' priors and intuitions is essential for the success of these methods. In addition, we demonstrate that these computational methods can provide relevant evidence to answer important research questions in historical linguistics.},
  copyright = {In Copyright - Educational Use Permitted},
  langid = {english},
  school = {Massachusetts Institute of Technology},
  annotation = {Accepted: 2022-02-07T15:19:26Z},
  url = {https://dspace.mit.edu/handle/1721.1/140021}
}

@inproceedings{meloniAntiquoNeuralProtolanguage2021,
  title = {Ab Antiquo: {{Neural}} Proto-Language Reconstruction},
  booktitle = {Proceedings of the 2021 {{Conference}} of the {{North American Chapter}} of the {{Association}} for {{Computational Linguistics}}: {{Human Language Technologies}}},
  author = {Meloni, Carlo and Ravfogel, Shauli and Goldberg, Yoav},
  year = {2021},
  month = jun,
  pages = {4460--4473},
  xpublisher = {{Association for Computational Linguistics}},
  xaddress = {{Online}},
  doi = {10.18653/v1/2021.naacl-main.353},
  abstract = {Historical linguists have identified regularities in the process of historic sound change. The comparative method utilizes those regularities to reconstruct proto-words based on observed forms in daughter languages. Can this process be efficiently automated? We address the task of proto-word reconstruction, in which the model is exposed to cognates in contemporary daughter languages, and has to predict the proto word in the ancestor language. We provide a novel dataset for this task, encompassing over 8,000 comparative entries, and show that neural sequence models outperform conventional methods applied to this task so far. Error analysis reveals a variability in the ability of neural model to capture different phonological changes, correlating with the complexity of the changes. Analysis of learned embeddings reveals the models learn phonologically meaningful generalizations, corresponding to well-attested phonological shifts documented by historical linguistics.},
}

@inproceedings{sprugnoliOverviewEvaLatin20222022,
  title = {Overview of the {{EvaLatin}} 2022 Evaluation Campaign},
  booktitle = {Proceedings of the Second Workshop on Language Technologies for Historical and Ancient Languages},
  author = {Sprugnoli, Rachele and Passarotti, Marco and Cecchini, Flavio Massimiliano and Fantoli, Margherita and Moretti, Giovanni},
  year = {2022},
  month = jun,
  pages = {183--188},
  publisher = {European Language Resources Association},
  address = {Marseille, France},
  abstract = {This paper describes the organization and the results of the second edition of EvaLatin, the campaign for the evaluation of Natural Language Processing tools for Latin. The three shared tasks proposed in EvaLatin 2022, i.,e.,Lemmatization, Part-of-Speech Tagging and Features Identification, are aimed to foster research in the field of language technologies for Classical languages. The shared dataset consists of texts mainly taken from the LASLA corpus. More specifically, the training set includes only prose texts of the Classical period, whereas the test set is organized in three sub-tasks: a Classical sub-task on a prose text of an author not included in the training data, a Cross-genre sub-task on poetic and scientific texts, and a Cross-time sub-task on a text of the 15th century. The results obtained by the participants for each task and sub-task are presented and discussed.}
}

@misc{wiktionarycontributorsCategoryLatinTerms2017,
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
  url = {https://en.wiktionary.org/wiki/Category:Latin_terms_derived_from_Proto-Italic}
}

@inproceedings{wuCreatingLargescaleMultilingual2018,
  title = {Creating Large-Scale Multilingual Cognate Tables},
  booktitle = {Proceedings of the Eleventh International Conference on Language Resources and Evaluation ({{LREC}})},
  author = {Wu, Winston and Yarowsky, David},
  year = {2018},
  month = may,
  publisher = {{European Language Resources Association (ELRA)}},
  address = {{Miyazaki, Japan}},
  url = {https://aclanthology.org/L18-1538.pdf}
}
```