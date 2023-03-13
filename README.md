# Relations and classification of entries in EncycNet
CSV data of the relations (**work in progress**) in the EncycNet knowledge graph. Includes broad and fine-grained Wikidata classification of entries. All files are tab-separated. Classification files are stored as `.p` ([pickle](https://wiki.python.org/moin/UsingPickle)) to keep Wikimedia objects functional.
Currently focusing on *Meyers-1905* for pushing the relations files, rest to follow.

Files (especially classification) are generally still subject to optimization.

## Directories
* "Classification" includes one file per encyclopedia, where Wikimedia objects as well as extracted hypernym paths and broad classification (person, location, object, abstract) from those objects are stored. Provides the basis for encyclopedia alignment.
* "Relations" includes one folder per encyclopedia, where one file corresponds to one relation (e.g. synonym, hypernym, etc.).

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
* add descriptions for relation files
* match the extracted relations to Wikidata relations
* evaluation through gold data (precision and recall)
* add reliability scores through evaluation
* transform to RDF*
* include Python toolbox for easy handling of the data
