### Explanations of relation files for Meyer-1905

*lemmasynonym_originlanguage* - Synonyms listed directly after the headword; if possible the language of that synonym is given.

### General file todos:

*enumeration* :heavy_check_mark:
* leading/trailing punctuation :heavy_check_mark:
* manual cleaning (nur semantische Ausdrücke) :heavy_check_mark:
	
*enumeration of hypernyms* 
* leading/trailing punctuation 
* remove tags 
* file name / column name :

*subcategories* :heavy_check_mark:
* leading/trailing punctuation :heavy_check_mark:
* leading enumeration :heavy_check_mark:
* manual cleaning (nur semantische Ausdrücke) :heavy_check_mark:

*b_synonyms*
* manual cleaning (nur semantische Ausdrücke)

*examples*
* leading/trailing punctuation
* comma split explode
* remove very short results (weniger als zwei Zeichen im Ergebnis)
* NEU (Freitag besprechen): Doppelte Zeilen löschen (.drop_duplicates())

*hypernym_author* :heavy_check_mark:

*hyponym*
* resolve abbrev

*lemmasynonym_originlanguage* :heavy_check_mark:

*meaning* :heavy_check_mark:

*originlanguage*
* trailing punct.

*sogenannt*
* D.name und Spaltenname Englisch
* trailing punct.

*i_synonyms*
* could be removed? Double check if everything already in lemmasynonym_originlanguage

*term_author*
* remove? (duplicate of hypernym_author?)

*term_origin*
* split explode comma und semicolon
* leading/trailing punct.

*title-source* :heavy_check_mark:

*title-translation* :heavy_check_mark:

*class*
* leading/trailing punct.

*division/genera/group/order/pronunciation/variety* :heavy_check_mark:

Removed:
lemma-extension, lemmaaddition, lemmasynonym, synonym_lat, abbreviation, authors, brackets-after-lemma, hyponym_alignment (too short, doubles, or sonderdatei)
