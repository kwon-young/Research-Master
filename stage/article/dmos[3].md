# Using Logic Programming Languages For Optical Music Recognition

## Abstract

Problematic

:   current OMR don't use rules for musical notation to their full potential.

Use new grammar to guide graphical segmentation and recognition.
Grammar describe relation between graphical objects.
Grammar implemented using λProlog.

* higher-order dialect of Prolog
* automatic translation from Prolog to λProlog

Validated on a prototype of OMR.

## Introduction

problem in document analysis

* separate knowledge from matching mechanism
* recognition paradox :
if you want to recognize correctly, you have first to decompose correctly,
but in order to decompose correctly you should have already recognized.

In OMR, high density of symbols is the biggest challenge.
Aim is to use fully rules of music writings.

Music notation formalized by a grammar.
Label a primitive only when a rule apply.

Multi domain method.

Take advantage of logic programming in syntactic analysis.

Validation

* already works on full scores
* detect recognition errors.

## Recognizing Music Scores

### Related Work

Erasing staff line (not on the scope of the search)

Objects recognition problems :

* scaling to complex score
* dealing with noise
* touching object
* broken objects

### Primitives : Segments and Symbols

Constructed and Symbolics

* Pysical level : how symbols are physically write in the score
* Logical level : syntactic way of using notes in writing music

These two level can be modeled by grammar.

terminals of grammar are :

* segments
* symbols

Robust segments extracting.

### Presentation of the grammar

two level of parsing

* graphical correspond to physical level
* syntatic correspond to logical level

operators :

* position connector
* factorization notation

#### Graphical part

use of encapsulated variables. From most simplest primitives to more complex assemblage.
use of position operators with different meaning.
use of rules.

#### Syntactic part

notion of step to manage simultaneity in full scores.
dynamic markings, phrasing slurs ... informations bind at step levels.

#### Staves System

map_staff operator apply the rule for every possible object in a bar system.

### Presentation of the Parser

hierarchical representation of a music score :

Score is a list of bar systems.
a bar system is a list of bars.
...

use of a cursor with following attributes :

* current position in the images;
* the element to parse (segment or a connected component)
* a research zone, modified by the position operator

also called head of the parsing list. Search of the next element to be parsed is done by using the research zone.
The parsed structure is parsed using rules in every possible way until the combination of parsed element matches the rules.
Possible to do some clustering using the context.

## Implementation of the Grammar with λProlog 

λProlog is a dialect of Prolog.
grammar ancestry is DCG (Definite Clause Grammars)

### λProlog

not a functionnal version of Prolog.
used to handle encoding terms with variables.

$x -> 3 + sin(2*3.14)$ in λProlog is : 
`x\ (3 + (sin (2* x)))`{.Prolog}

use of λterms, universal and existential quantifications, implications.

pseudo prolog code is compiled to λProlog. 

### Touching Objects: Segment - Symbol

use of a `delay` operator to delay the treatment of some symbol or segments.
the parser can then manage touching objects.

### Full Score

add operator to directly treat list of object.

### Future Processing of Other Difficulties

Objective : add a classifier like RBF to the grammar to be able to decide if a structure is correctly parsed.

## Compilation of the Grammar with λProlog

????

## Conclusion

### Music score recognition

recog system for music score guided with a grammar, works on full scores.
all recog rules are formalised in the grammar.
grammar used both in physical level and logical level.
Separation of the tools and the grammar.
can reconstruct broken objects, decompose touching objects, deal with scaling up.
more reliable result.

λProlog use because of the formal approach.
low level recognition in C.
λProlog also used to code the compiler of the grammar.

