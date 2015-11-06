# DMOS : A Generic Document Recognition Method, Application to an Automatic Generator of Musical Scores, Mathematical Formulae and Table Structures Recognition Systems

## Abstract

* Generic document recognition method : DMOS
  * gramatical formalism : EPF
  * parser : introduce context in segmentation
* use on :
  * musical score
  * mathematical formulae
  * recursive table structure
  * military forms of the 19th century
* validation of the system on 5000 military forms

## Introduction

* develop a generator of recognition system for structured document
* time and energy saving

* difference between document : Domain Specific Knowledge

* introduce a tool to easily change the DSK
  * use of a grammatical formalism

* DMOS : Description and MOdification of Segmentation
  * grammatical formalism : EPF : Enhanced Position Formalism
    * description language for structured documents
    * graphical, syntactical, semantical description
  * dynamic structure of the parser
    * try different segmentation with the help of context

* Separating knowledge from program
  * generic method
  * enhance recognition quality

## Related Work

* literature grammars for object and document recognition
  * Trees and Web grammars
    * limited expressiveness
    * complex syntax
  * Plex grammars
    * less limited expressiveness
    * complex syntax
  * Graph grammars
    * important expressiveness
    * complex definition of production rules
    * difficult when knowledge is complex

* Conclusion
  * syntax of grammars too complex
  * no context in segmentation
* new grammatical formalism
  * simple syntax
  * important expressiveness

## DMOS : A Generic Document Recognition Method

* DMOS : Descriptionand MOdification of Segmentation
  * EPF : Enhanced Position Formalism
    * describe the document
  * associated parser
    * contextual segmentation

### Presentation of the EPF Formalism

* EPF is extension in bi-D of DCG : Definite Clause Grammars in mono-D
  * translation in Prolog

* terminals
  * line-segments
  * pixel arrays
    * components, connected or not, represent a symbol

* bi-dimensional structure
  * add of six-operators to mono-D

#### Position Operator AT

```Prolog
A && AT(pos) && B
```

A, and at the position pos in relation to A, we find B

&& : concatenation operator
A, B : terminal or non-terminal

#### Factorisation Operator \#\#

associated with AT operator

```Prolog
A && (AT(pos1) && B ##
      AT(pos2) && C)
```

Basically an AND operator

```Prolog
beamedNote ::= beam &&
    (AT(rightTip) && noteGR ##
     notesInBetween ##
     AT(leftTip) && noteGR)
```

::= : constructor of a grammar rule

#### Save Operators ---> and <----

---> save an instance of A
<--- refer to instance of A

```Prolog
(A ---> labelForA) &&
AT(pos1) && B && AT(pos2) &&
(A <--- labelForA)
```

allow bi-directionnal position relation

describing a rectangle

```Prolog
rectangle ::=
    (segV ---> segLeftSide) &&
    AT(touchUp) && segH &&
    AT(touchRight) && segV &&
    AT(touchDown) && segH &&
    AT(touchLeft) &&
    (segV <--- segLeftSide).
```

#### Declaration Operator DECLARE

can use DECLARE operator to specify the scope of the label

```Prolog
exampleFig ::=
    DECLARE(segLeftSide) (
        rectangle && triangle
    ).

triangle ::=
    (segV <--- segLeftSide) &&
    AT(touchUp) && segDiag &&
    AT(touchRight) && segDiag &&
    AT(touchLeft) &&
    (segV <--- segLeftSide).
```

#### Space Reduction Operator IN ... DO

specify area where a rule should apply

```Prolog
tableStructure ::= ...
    ... insideAcell.

insideAcell ::=
    IN(cellBoundingBox)
      DO(tableStructure).
```

### Presentation of the Associated Parser

* parser
  * image processing level
  * contains segment and connected component
  * cursor
    * current position in the image
    * element to be parsed
    * research zone
      * modified by AT operator

* traditional parser don't context

* a segment is not necessarily an object
* a connected component is not necessarily an object
* use of context to correctly detect an object

discrepancy between the way knowledge describe an object and the way an object have to be recognized

## A Generator of Document Recognition Systems

DMOS method

* generator of structured document recognition systems
  * an EPF grammar
  * a classifier (if necessary)
  * compiled EPF grammar results in a parser

* can produce new recognition system from association of different grammar

### Musical Scores Recognition System


