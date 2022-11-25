# EncycNet_Relations
CSV data of all relations (work in progress) in the EncycNet knowledge graph. Includes broad and fine-grained Wikidata classification of entries. All files are tab-separated.

## Naming conventions of relation files
* examples: "Meyers-1905_i_synonym.csv", "Meyers-1905_si_technicalterm_synonym_language.csv"
* {encyclopedia name and year}\_{tag}\_{list of relations}.csv
* English only
* no uppercase except for encyclopedia
* only one letter per XML-tag used
* relation names are stated in singular and are not abbreviated
* relation names **must** match the column header in the file
* merge CSV files that would have the same name (e.g. Lemmasynonym1, Lemmasynonym2, etc.)

| Letter   |      Tag     |
|----------|:-------------:|
| i |  italic |
| s |    spaced   |
| b | bold |
| r | reference |
| n | no tag |
