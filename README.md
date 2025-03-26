# Relations and classification of entries in EncycNet
CSV data of the relations (**work in progress**) in the EncycNet knowledge graph. Includes broad and fine-grained Wikidata classification of entries. All files are tab-separated. Classification files are stored as `.p` ([pickle](https://wiki.python.org/moin/UsingPickle)) to keep Wikimedia objects functional.

Relations:

+ Meyers-1905: completed :white_check_mark:
+ Herder-1854: completed :white_check_mark:
+ Brockhaus-1809: completed :white_check_mark:
+ Brockhaus-1837: completed :white_check_mark:
+ Brockhaus-1911: in progress :arrow_right:
+ DamenConvLex-1834: in progress :arrow_right:

Be aware that all data was extracted automatically and the content within the relation files can be rather fuzzy.

You can find the latest version of the knowledge graph, which contains Meyers-1905, Herder-1854, Brockhaus-1837, Brockhaus-1809 as of now, on zenodo:

[![DOI](https://zenodo.org/badge/doi/10.5281/zenodo.10219192.svg)](http://dx.doi.org/10.5281/zenodo.10219192)

## Directories
* "Classification" includes one file per encyclopedia, where Wikimedia objects as well as extracted hypernym paths and broad classification (person, location, object, abstract) from those objects are stored. Provides the basis for encyclopedia alignment.
* "Relations" includes one folder per encyclopedia, where one file corresponds to one relation (e.g. synonym, hypernym, etc.).

## Example query with RDFLib
[RDFLib](https://rdflib.readthedocs.io/en/stable/) is a Python package for handling RDF graphs. You may work with EncycNet like so:
1. Download the [latest version of the graph from zenodo](http://dx.doi.org/10.5281/zenodo.10219192) and install RDFLib with
`$ pip install rdflib`
2. Import the library and load the graph:
```python 
from rdflib import ConjunctiveGraph, query, Literal
from rdflib.namespace import Namespace

G = ConjunctiveGraph()
G.parse('EncycNet_Ver02.ttl', format='trig')

wiki = Namespace('https://www.wikidata.org/wiki/')
encycnet = Namespace('http://encycnet.digital-humanities.de/fullarticle.html?articleID=')
```
3. Traverse the graph by iterating over triples with or without constraints (e.g. all fictional entities, 'None' may indicate a wildcard for any of **s**ubject, **p**redicate, **o**bject, sub**g**raph):
```python 
for s, p, o, g in G.quads((None, wiki['Property:P31'], Literal('fiktionale Entität'), None)):
    print(f"{s} ist fiktiv")
```
4. Use SPARQL to find entities (e.g. all that are subclass of "science"):
```python 
q = """
SELECT DISTINCT ?item ?name
WHERE {
    ?item wiki:Property:P2561 ?name .
    ?item wiki:Property:P279* "Wissenschaft" .
} 
LIMIT 20 """

result = G.query(q, initNs={'wiki': wiki})
for row in result:
    print(f"{row['item']} {row['name']}")
```

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
* evaluation through gold data (precision and recall)
* add reliability scores through evaluation
