# EncycNet_Relations
CSV data of all relations (**work in progress**) in the EncycNet knowledge graph. Includes broad and fine-grained Wikidata classification of entries. All files are tab-separated. Classification files are stored as `.p` ([pickle](https://wiki.python.org/moin/UsingPickle])) to keep Wikimedia objects functional.

All files (especially classification) are still subject to optimization.

## Directories
* "Classification" includes one file per encyclopedia, where Wikimedia objects as well as extracted hypernym paths and broad classification (person, location, object, abstract) from those objects are stored. Provides the basis for encyclopedia alignment.
* "Relations" includes one folder per encyclopedia, where one file corresponds to one relation (e.g. synonym, hypernym, etc.).

## Naming conventions of relation files
* examples: "Meyers-1905_i_synonym.csv", "Meyers-1905_si_technicalterm_synonym_language.csv"
* {encyclopedia name and year}\_{tag}\_{list of relations seperated by _ }.csv
* English only
* no uppercase in filename except for encyclopedia
* only one letter per XML-tag used
* all relations files must include columns "EntryID", "headword", and at least one relation column
* relation names are stated in singular and are not abbreviated
* relation names **must** match the column header in the file (same names and order)
* columns for additional IDs for references are titled "target" and are listed in the filename as well
* merge CSV files where naming conventions will result in the same filename (e.g. Lemmasynonym1, Lemmasynonym2, etc.)

| Letter   |      Tag     |
|----------|:-------------:|
| i |  italic |
| s |    spaced   |
| b | bold |
| r | reference |
| n | no tag |

## List of encyclopedias used

TODO

## Future work
* match the extracted relations to Wikidata relations
* evaluation through gold data (precision and recall)
* transform to RDF*
* include Python toolbox for easy handling of the data
