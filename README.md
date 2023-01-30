# EncycNet_Relations
CSV data of all relations (**work in progress**) in the EncycNet knowledge graph. Includes broad and fine-grained Wikidata classification of entries. All files are tab-separated. Classification files are stored as `.p` ([pickle](https://wiki.python.org/moin/UsingPickle)) to keep Wikimedia objects functional.

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
* all relations files must have their own index (0, 1, 2, ..., n), further included are columns "EntryID", "headword", and at least one relation column
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

| Title                                                                    | Eds.                                      | Year      | Volumes | Description                                                                                                       | Number of entries | Number of tokens |
|--------------------------------------------------------------------------|-------------------------------------------|-----------|---------|-------------------------------------------------------------------------------------------------------------------|-------------------|------------------|
| Brockhaus Conversations-Lexikon oder kurzgefaßtes Handwörterbuch         | Friedrich Arnold Brockhaus                | 1809-1811 | 8       | First edition of Brockhaus general encyclopedia: 6 volumes + 2 supplements.                                                | 6,960             | 1,186,000        |
| Brockhaus Bilder-Conversations-Lexikon                                   | Friedrich Arnold Brockhaus                | 1837-1841 | 4       | Illustrated general encyclopedia covering everyday subjects in a non-scientific way.                              | 7,049             | 2,604,000        |
| Brockhaus Kleines Konversations-Lexikon                                  | Friedrich Arnold Brockhaus                | 1911      | 2       | General, pocketbook edition encyclopedia.                                                                         | 82,780            | 2,434,000        |
| Damen Conversations Lexikon                                              | Carl Herloßsohn                           | 1834-1838 | 10      | General encyclopedia explicitly marketed for middle-class women.                                                  | 7,099             | 1,461,000        |
| Herders Conversations-Lexikon                                            | Raphael Herder, Benjamin Herder           | 1854-1857 | 5       | General encyclopedia with short explanations of various topics.                                                   | 39,755            | 2,256,000        |
| Meyers Großes Konversations-Lexikon                                      | Joseph Meyer                              | 1905-1909 | 20      | Comprehensive general encyclopedia  for the general population.                                                   | 156,264           | 17,437,000       |

## Future work
* match the extracted relations to Wikidata relations
* evaluation through gold data (precision and recall)
* add reliability scores through evaluation
* transform to RDF*
* include Python toolbox for easy handling of the data
