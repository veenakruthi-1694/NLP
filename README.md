# NLP
====================================

You need to have [Python](www.itnota.com/install-python-windows-server/) installed.

To Run above import from spaCy(libraries which are used in the program) 


Create a folder on your computer to use for your Python programs, such as ~/pythonpractice.

Open up your favorite text editor and create a new file called hello.py containing just the following 2 lines

## ! /usr/bin/python ##

print('Hello, world!')

Note:

If you have both python version 2.6.1 and version 3.0 installed (Very possible if you are using a debian or debian-based(ubuntu, Mint, …) distro, and ran sudo apt-get install python3 to have python3 installed), use

## ! /usr/bin/python3 ##

print('Hello, world!')

save your hello.py program in the ~/pythonpractice folder.

Open up the terminal program. In KDE, open the main menu and select "Run Command..." to open Konsole. In GNOME, open the main menu, open the Applications folder, open the Accessories folder, and select Terminal.

Type cd ~/pythonpractice to change directory to your pythonpractice folder, and hit Enter.

Type chmod a+x hello.py to tell Linux that it is an executable program.

Type ./hello.py to run your program!

In addition, you can also use ln -s hello.py /usr/bin/hello to make a symbolic link hello.py to /usr/bin under the name hello, then run it by simply executing hello.

Compile() :  
Consider a situation where we have a piece of Python code in a string and we want to compile it so that we can later run it when needed. The compile method does this task. It takes sourcecode as input and returns a code object which is ready to be executed.

### Syntax ###
compile(source, filename, mode, flags=0, dont_inherit=False, optimize=-1)
Parameters :
#### Source ####  
It can be a normal string, a byte string, or an AST object
#### Filename #### 
This is the file from which the code was read. If it wasn’t read from a file, you can give a name yourself.

#### Mode #### 
Mode can be exec, eval or single.
a. eval – If the sorce is a single expression.
b. exec – It can take a block of a code that has Python statements, class and functions and so on.
c. single – It is used if consists of a single interactive statement

#### Flags (optional) and dont_inherit (optional) #### 
Default value=0. It takes care that which future statements affect the compilation of the source.
#### Optimize (optional) #### 
It tells optimization level of compiler. Default value -1.

###  code to demonstrate working of compile(). ### 
  
#### Creating sample sourcecode to multiply two variables ####
 x and y
 
srcCode = 'x = 10\n  y = 20\n 

mul = x * y\n 

print("mul =", mul)'
  
#### Converting above source code to an executable #### 
execCode = compile(srcCode, 'mulstring', 'exec') 
  
#### Running the executable code. #### 
exec(execCode)

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
("Apple is looking at buying U.K.")
### Output ###
Apple PROPN nsubj

is AUX aux

looking VERB ROOT

at ADP prep

buying VERB pcomp

U.K. PROPN compound

split into individual words and annotated – it still holds all information of the original text, like whitespace characters. 

### Tokenization ###
spaCy first tokenizes the text, i.e. segments it into words, punctuation and so on. 
This is done by applying rules specific to each language.
### Example ###
("Apple is looking at buying U.K.")
### Output ###
Apple
is
looking
at
buying
U.K.

Tokenizer exception: Special-case rule to split a string into several tokens or prevent a token from being split when punctuation rules are applied.

Prefix: Character(s) at the beginning, e.g. $, (, “, ¿.

Suffix: Character(s) at the end, e.g. km, ), ”, !.

Infix: Character(s) in between, e.g. -, --, /, ….

### part of speech tags and Dependecies ###
spaCy can parse and tag a given Doc. This is where the statistical model comes in, which enables spaCy to make a prediction of which tag or label most likely applies in this context.
### Example ###
("Apple is looking at buying U.K.")
### Output ###

      Apple   Apple   PROPN    NNP   nsubj   Xxxxx  True   False
 
      is      be      AUX      VBZ   aux      xx    True   True

      looking look    VERB     VBG   ROOT     xxxx  True    False

      at      at       ADP     IN     prep     xx    True    True

      buying   buy     VERB    VBG    pcomp    xxxx  True    False

      U.K.     U.K.    PROPN    NNP   compound  X.X.  False  False

Text: The original word text.  eg:apple

Lemma: The base form of the word.eg:apple

POS: The simple UPOS part-of-speech tag.eg:propn

Tag: The detailed part-of-speech tag.eg:nnp

Dep: Syntactic dependency, i.e. the relation between tokens.eg:nsubj

Shape: The word shape – capitalization, punctuation, digits.eg:xxxxx

is alpha: Is the token an alpha character? eg:true

is stop: Is the token part of a stop list, i.e. the most common words of the language? eg:false

### Named Entities ###
A named entity is a “real-world object” that’s assigned a name – for example, a person, a country, a product or a book title.
### Example ###
("Apple is looking at buying U.K. startup for $1 billion")
### Output ###


     Apple               	 0	          5	       ORG	       Companies, agencies, institutions.

     U.K.	                27	         31	       GPE	       Geopolitical entity, i.e. countries, cities, states.

    $1 billion	           44          54   	    MONEY	     Monetary values, including unit.

Text: The original entity text eg:apple,U.k,billion

Start: Index of start of entity in the Doc eg:0,27,44

End: Index of end of entity in the Doc eg:5,31,54

Label: Entity label, i.e. type eg:org,gpe,money

### Pipeline ###
When you call nlp on a text, spaCy first tokenizes the text to produce a Doc object.
The Doc is then processed in several different steps – this is also referred to as the processing pipeline.

    
     tokenizer                 	Tokenizer	                     Segment text into tokens.

     tagger          	          Tagger	                        Assign part-of-speech tags.

     parser	                    DependencyParser		             Assign dependency labels.

     ner	                       EntityRecognizer	             	Detect and label named entities.

     textcat	                   TextCategorizer	              	Assign document labels.

     …             	            custom components		            Assign custom attributes, methods or properties.

The processing pipeline always depends on the statistical model and its capabilities.

## Vocab,hashes and lexemes ## 
SpaCy tries to store data in a vocabulary, the Vocab, that will be shared by multiple documents.
To save memory, spaCy also encodes all strings to hash values – in this case for example, “coffee” has the hash 3197928453018144401.
Entity labels like “ORG” and part-of-speech tags like “VERB” are also encoded. Internally, spaCy only “speaks” in hash values.
 
Token: A word, punctuation mark etc. in context, including its attributes, tags and dependencies.

Lexeme: A “word type” with no context. Includes the word shape and flags, e.g. if it’s lowercase, a digit or punctuation.

Doc: A processed container of tokens in context.

Vocab: The collection of lexemes.

StringStore: The dictionary mapping hash values to strings, for example 3197928453018144401 → “coffee”.

Text: The original text of the lexeme eg:coffee

Orth: The hash value of the lexeme eg:3197928453018144401	

Shape: The abstract word shape of the lexeme eg:xxxx

Prefix: By default, the first letter of the word string eg:c

Suffix: By default, the last three letters of the word string eg:fee

is alpha: Does the lexeme consist of alphabetic characters? eg:true

is digit: Does the lexeme consist of digits? eg:False


The mapping of words to hashes doesn’t depend on any state. 
To make sure each value is unique, spaCy uses a hash function to calculate the hash based on the word string.
 
## Knowledge Base ##
The knowledge base (KB) uses the Vocab to store its data efficiently.
A knowledge base is created by first adding all entities to it. Next, for each potential mention or alias, a list of relevant KB IDs and their prior probabilities is added. The sum of these prior probabilities should never exceed 1 for any given alias.

Mention: A textual occurrence of a named entity, e.g. ‘Miss Lovelace’.

KB ID: A unique identifier referring to a particular real-world concept, e.g. ‘Q7259’.

Alias: A plausible synonym or description for a certain KB ID, e.g. ‘Ada Lovelace’.

Prior probability: The probability of a certain mention resolving to a certain KB ID, prior to knowing anything about the context in which the mention is used.

Entity vector: A pretrained word vector capturing the entity description.

## Serialization ##
If you’ve been modifying the pipeline, vocabulary, vectors and entities, or made updates to the model, you’ll eventually want to save your progress,This means you’ll have to translate its contents and structure into a format that can be saved, like a file or a byte string. This process is called serialization. spaCy comes with built-in serialization methods
##### Method        Returns    Example #####
      to_bytes	     bytes  	   data = nlp.to_bytes()

      from_bytes	   object 	   nlp.from_bytes(data)

      to_disk      	-  	       nlp.to_disk("/path")

      from_disk  	  object	    nlp.from_disk("/path")
 ## Training ##
spaCy’s models are statistical and every “decision” they make – for example, which part-of-speech tag to assign, or whether a word is a named entity – is a prediction. This prediction is based on the examples the model has seen during training.

Training data: Examples and their annotations.

Text: The input text the model should predict a label for.

Label: The label the model should predict.

Gradient: Gradient of the loss function calculating the difference between input and expected output.
## Language data ##
Every language is different – and usually full of exceptions and special cases, especially amongst the most common words. Some of these exceptions are shared across languages, while others are entirely specific – usually so specific that they need to be hard-coded.

## Stop words ##
[stop_words.py](https://github.com/explosion/spaCy/blob/master/spacy/lang/en/stop_words.py) :
List of most common words of a language that are often useful to filter out, for example “and” or “I”. Matching tokens will return True for is_stop.

## Tokenizer exceptions ##
[tokenizer_exceptions.py](https://github.com/explosion/spaCy/blob/master/spacy/lang/de/tokenizer_exceptions.py) :
Special-case rules for the tokenizer, for example, contractions like “can’t” and abbreviations with punctuation, like “U.K.”.

## Norm exceptions ##
[norm_exceptions.py](https://github.com/explosion/spaCy/blob/master/spacy/lang/norm_exceptions.py)	:
Special-case rules for normalizing tokens to improve the model’s predictions, for example on American vs. British spelling.

## Punctuation rules ##
[punctuation.py](https://github.com/explosion/spaCy/blob/master/spacy/lang/punctuation.py) :	
Regular expressions for splitting tokens, e.g. on punctuation or special characters like emoji. Includes rules for prefixes, suffixes and infixes.

## Character classes ##
[char_classes.py](https://github.com/explosion/spaCy/blob/master/spacy/lang/char_classes.py)	: 
Character classes to be used in regular expressions, for example, latin characters, quotes, hyphens or icons.

## Lexical attributes ##
[lex_attrs.py](https://github.com/explosion/spaCy/blob/master/spacy/lang/en/lex_attrs.py)	:
Custom functions for setting lexical attributes on tokens, e.g. like_num, which includes language-specific words like “ten” or “hundred”.

## Syntax iterators ##
[syntax_iterators.py](https://github.com/explosion/spaCy/blob/master/spacy/lang/en/syntax_iterators.py) :	
Functions that compute views of a Doc object based on its syntax. At the moment, only used for noun chunks.

## Tag map ##
[tag_map.py](https://github.com/explosion/spaCy/blob/master/spacy/lang/en/tag_map.py)	: 
Dictionary mapping strings in your tag set to Universal Dependencies tags.

## Morph rules ##
[morph_rules.py](https://github.com/explosion/spaCy/blob/master/spacy/lang/en/morph_rules.py)	:
Exception rules for morphological analysis of irregular words like personal pronouns.

## Lemmatizer ##
spacy-lookups-data:	Lemmatization rules or a lookup-based lemmatization table to assign base forms, for example “be” for “was”.

## Text pre-processing and Wrangling ##

## Removing HTML tags\noise ##

unstructured text contains a lot of noise, especially if you use techniques like web or screen scraping

## Removing accented characters ##

 simple example — converting é to e.
### Example ###
remove_accented_chars('Sómě Áccěntěd těxt')
### Output ###
'Some Accented text'

## Removing special characters\symbols ##
Special characters and symbols are non-alphanumeric characters or even occasionally numeric characters , which add to the extra noise in unstructured text. simple regular expressions can be used to remove them.
### Example ###
remove_special_characters("Well this was fun! What do you think? 123#@!", 
                          remove_digits=True)
 ### Output ###
 Well this was fun What do you think 
## Stemming ##
Word stems are also known as the base form of a word, and we can create new words by attaching affixes to them in a process known as inflection. Consider the word JUMP. You can add affixes to it and form new words like JUMPS, JUMPED, and JUMPING. In this case, the base word JUMP is the word stem.
The reverse process of obtaining the base form of a word from its inflected form is known as stemming.
### Example ###
simple_stemmer("My system keeps crashing his crashed yesterday")
### Output ###
'My system keep crash hi crash yesterday'

## Lemmatization ##
Lemmatization is very similar to stemming, where we remove word affixes to get to the base form of a word.
The root word is always a lexicographically correct word, but the root stem may not be so.
### Example ###
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
