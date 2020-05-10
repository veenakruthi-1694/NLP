# NLP
====================================

You need to have [Python](www.itnota.com/install-python-windows-server/) installed.
 
# spaCy
spaCy is a free, open-source library for advanced Natural Language Processing (NLP) in Python.
spaCy is designed specifically for production use and helps you build applications that process and “understand” large volumes of text. It can be used to build information extraction or natural language understanding systems, or to pre-process text for deep learning.

# Install spaCy
spaCy is compatible with 64-bit CPython 2.7 / 3.5+ and runs on Unix/Linux, macOS/OS X and Windows. The latest spaCy releases are available over [pip ](https://pypi.org/project/spacy/) and [conda](https://anaconda.org/conda-forge/spacy).

## Conda ##
 Thanks to our great community, we’ve been able to re-add conda support. You can also install spaCy via conda-forge:
 
 $conda install -c conda-forge spacy 

## Pip ##
 Using pip, spaCy releases are available as source packages and binary wheels (as of v2.0.13).

 $ pip install -U spacy

## NPL ##
Natural Language Processing (NLP) is all about leveraging tools, techniques and algorithms to process and understand natural language-based data, which is usually unstructured like text, speech and so on. 

## Tokenization ##
Segmenting text into words, punctuations marks etc.
## Part-of-speech (POS) ##
Tagging	Assigning word types to tokens, like verb or no
## Dependency Parsing ## 
Assigning syntactic dependency labels, describing the relations between individual tokens, like subject or object.
## Lemmatization ##	
Assigning the base forms of words. For example, the lemma of “was” is “be”, and the lemma of “rats” is “rat”.
## Sentence Boundary Detection (SBD) ##	
Finding and segmenting individual sentences.
## Named Entity Recognition (NER) ##
Labelling named “real-world” objects, like persons, companies or locations.
## Entity Linking (EL) ##
Disambiguating textual entities to unique identifiers in a Knowledge Base.
## Similarity ##
Comparing words, text spans and documents and how similar they are to each other.
## Text Classification ##
Assigning categories or labels to a whole document, or parts of a document.
## Rule-based Matching ##
Finding sequences of tokens based on their texts and linguistic annotations, similar to regular expressions.
## Training ##
Updating and improving a statistical model’s predictions.
## Serialization ##
Saving objects to files or byte strings.

## Linguistic Annotations ##
spaCy provides a variety of linguistic annotations to give you insights into a text’s grammatical structure.
This includes the word types, like the parts of speech, and how the words are related to each other.
### Example ###
import spacy

nlp = spacy.load("en_core_web_sm")

doc = nlp("Apple is looking at buying U.K.")

for token in doc:

    print(token.text, token.pos_, token.dep_)
### Output ###
Apple PROPN nsubj
is AUX aux

looking VERB ROOT

at ADP prep

buying VERB pcomp

U.K. PROPN compound

### Tokenization ###
spaCy first tokenizes the text, i.e. segments it into words, punctuation and so on. 
This is done by applying rules specific to each language.
### Example ###
import spacy

nlp = spacy.load("en_core_web_sm")

doc = nlp("Apple is looking at buying U.K. startup for $1 billion")

for token in doc:
    print(token.text)
### Output ###
Apple
is
looking
at
buying
U.K.
startup
for
$
1
billion

### part of speech tags and Dependecies ###
spaCy can parse and tag a given Doc. This is where the statistical model comes in, which enables spaCy to make a prediction of which tag or label most likely applies in this context.
### Example ###
import spacy

nlp = spacy.load("en_core_web_sm")

doc = nlp("Apple is looking at buying U.K. startup for $1 billion")

for token in doc:
    print(token.text, token.lemma_, token.pos_, token.tag_, token.dep_,
            token.shape_, token.is_alpha, token.is_stop)
 ### Output ###
 Apple Apple PROPN NNP nsubj Xxxxx True False
 
is be AUX VBZ aux xx True True

looking look VERB VBG ROOT xxxx True False

at at ADP IN prep xx True True

buying buy VERB VBG pcomp xxxx True False

U.K. U.K. PROPN NNP compound X.X. False False

### Named Entities ###
A named entity is a “real-world object” that’s assigned a name – for example, a person, a country, a product or a book title.
### Example ###
import spacy

nlp = spacy.load("en_core_web_sm")

doc = nlp("Apple is looking at buying U.K. startup for $1 billion")

for ent in doc.ents:
    print(ent.text, ent.start_char, ent.end_char, ent.label_)
### Output ###
Apple 0 5 ORG

U.K. 27 31 GPE

$1 billion 44 54 MONEY

### Pipeline ###
When you call nlp on a text, spaCy first tokenizes the text to produce a Doc object.
The Doc is then processed in several different steps – this is also referred to as the processing pipeline.


## Text pre-processing and Wrangling ##

## Removing HTML tags\noise ##

unstructured text contains a lot of noise, especially if you use techniques like web or screen scraping

## Removing accented characters ##

 simple example — converting é to e.
### Example ###
def remove_accented_chars(text):

    text = unicodedata.normalize('NFKD', text).encode('ascii', 'ignore').decode('utf-8', 'ignore')
    
    return text

remove_accented_chars('Sómě Áccěntěd těxt')
### Output ###
'Some Accented text'

## Removing special characters\symbols ##
Special characters and symbols are non-alphanumeric characters or even occasionally numeric characters , which add to the extra noise in unstructured text. simple regular expressions can be used to remove them.
### Example ###

def remove_special_characters(text, remove_digits=False):

    pattern = r'[^a-zA-z0-9\s]' if not remove_digits else r'[^a-zA-z\s]'
    
    text = re.sub(pattern, '', text)
    
    return text

remove_special_characters("Well this was fun! What do you think? 123#@!", 
                          remove_digits=True)
 ### Output ###
 Well this was fun What do you think 

Handling contractions

## Stemming ##
Word stems are also known as the base form of a word, and we can create new words by attaching affixes to them in a process known as inflection. Consider the word JUMP. You can add affixes to it and form new words like JUMPS, JUMPED, and JUMPING. In this case, the base word JUMP is the word stem.
The reverse process of obtaining the base form of a word from its inflected form is known as stemming.
### Example ###
def simple_stemmer(text):

    ps = nltk.porter.PorterStemmer()
    text = ' '.join([ps.stem(word) for word in text.split()])
    return text

simple_stemmer("My system keeps crashing his crashed yesterday")
### Output ###
'My system keep crash hi crash yesterday'

## Lemmatization ##
Lemmatization is very similar to stemming, where we remove word affixes to get to the base form of a word.
The root word is always a lexicographically correct word, but the root stem may not be so.
### Example ###
def lemmatize_text(text):

    text = nlp(text)
    
    text = ' '.join([word.lemma_ if word.lemma_ != '-PRON-' else word.text for word in text])
    
    return text

lemmatize_text("My system keeps crashing! his crashed yesterday")
### Output ###
'My system keep crash ! his crash yesterday'

## Stop word removal ##
Words which have little or no significance, especially when constructing meaningful features from text, are known as stopwords or stop words.
These can be articles, conjunctions, prepositions and so on. Some examples of stopwords are a, an, the, and the like.
## Expanding Contractions ##
Contractions are shortened version of words or syllables. They often exist in either written or spoken forms in the English language. These shortened versions or contractions of words are created by removing specific letters and sounds.
### Examples ###
do not to don’t and I would to I’d.
## Understanding Language Syntax and Structure ##
Typical parsing techniques for understanding text syntax are 

### Parts of Speech (POS) Tagging ###

1.NOUN:The POS tag symbol for nouns is N.

2.VERB:The POS tag symbol for verbs is V.

3.ADJECTIVE:The POS tag symbol for adjectives is ADJ .

4.ADVERB:The POS tag symbol for adverbs is ADV.

### Shallow Parsing or Chunking ###
Noun phrase (NP): These are phrases where a noun acts as the head word. Noun phrases act as a subject or object to a verb.

Verb phrase (VP): These phrases are lexical units that have a verb acting as the head word. Usually, there are two forms of verb phrases. One form has the verb components as well as other entities such as nouns, adjectives, or adverbs as parts of the object.

Adjective phrase (ADJP): These are phrases with an adjective as the head word. Their main role is to describe or qualify nouns and pronouns in a sentence, and they will be either placed before or after the noun or pronoun.

Adverb phrase (ADVP): These phrases act like adverbs since the adverb acts as the head word in the phrase. Adverb phrases are used as modifiers for nouns, verbs, or adverbs themselves by providing further details that describe or qualify them.

Prepositional phrase (PP): These phrases usually contain a preposition as the head word and other lexical components like nouns, pronouns, and so on. These act like an adjective or adverb describing other words or phrases.

### Constituency Parsing ###
Constituent-based grammars are used to analyze and determine the constituents of a sentence. 
These grammars can be used to model or represent the internal structure of sentences in terms of a hierarchically ordered structure of their constituents.

### Dependency Parsing ###
In dependency parsing, we try to use dependency-based grammars to analyze and infer both structure and semantic dependencies and relationships between tokens in a sentence. 
The basic principle behind a dependency grammar is that in any sentence in the language, all words except one, have some relationship or dependency on other words in the sentence. 
The word that has no dependency is called the root of the sentence. 
The verb is taken as the root of the sentence in most cases. 
