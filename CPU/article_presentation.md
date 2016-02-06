# Analysing the Relationship between Learning Styles and Navigation Behaviour in Web-Based Educational System

## Authors

Nabila Bousbia.
doctor in Computer Science : trace analysis, user modelling and learning styles.

Issam Rebaï.
Professor at TB : learning metadata, affective and ubiquitous computing.

Jean-Marc Labat.
Professor at Paris6 University : cognitive modelling of problem solving, serious games.

Amar Balla
Doctor in Computer Science : adaptative hypermedia, student modelling.

## Domain

Learning style, navigation behaviour, trace analysis.

## Abstract

Automatically deduce *learning style* from *browsing behaviour*.
Relationship between learning style and browsing behaviour.
Experiment with 27 students on e-learning platform.
browsing behaviour evaluated from navigation types based on *trace analysis*.

Measure using *Index of Learning Styles* by Felder and Solomon 1996.

## Introduction

Domain : Learning style on the context of use of computers in education.

Learning styles (LS)

:   Reed and Oughton 1997
    > how individuals prefer to organize and represent information.
    Strategies in the way of managing and organizing the information.
    Implementation of these behaviour and strategies.

Educational Hypermedia Systems (EHS).
Better adaptation of LS for each user.

Almost 70 models of LS.
Some already implemented on EHS.
Detection of LS from questionnaire.

We want *automatic* detection of LS.
By using trace of learner's activities.

Study relationship between LS and browsing behaviour.

## Background

### Learning Style

LS : individual's learning preferences.
Many definitions and implementations.

Chevrier et al. 2000 :

#. a specific way of behaving, predisposition, preferences related to learning and teaching context.
#. information processing.
#. personality characteristics.

Riding and Rayner definition 2001

:   > The expression learning style refers to a set of individual differences,
    > which include not only an expressed personal preference concerning teaching
    > or an association with a particular form of learning activity,
    > but also to individual differences that can be found in the psychology
    > of intelligence or personality."

LS :

* strategies in the way of managing and organizing informations
* implementing behaviours and strategies

71 models of LS.

3 dimensions of LS :

* preferences (sensory or environment)
* cognitive ability / personality
* learning process

Curry's "onion" model (Curry 1983) *Mettre une image dans le diapo*

Here we consider dynamic LS, it's changing over time.

### Learning Style and EHS

Still young research. Used for adaptation and customization of learning.

Felder and Silberman's model (FSLSM) of LS used here.

* can quantify LS
* good degree of validity and reliability/internal consistency
* suitable for EHS
* suitable to use with multimedia
* easily administered to university student

LS model are traditionally proposed for face to face interaction.

To adapt to EHS, add layer to the model.

Traditional LS identification : questionnaire.
But individual are not reliable, ask the right question.
Assumption of questionnaire :

* individual motivation
* student must be aware of their own LS
* student's beliefs
* LS stable over time, if not : how to update ?

Solution : analyse LS from behaviour analysis.

### Learning Style on the Web

Studies in psychology, education and computer science show that :
Strong relationship between LS and navigation behaviour in Web application.

field dependance or independance ??
:   how people perceive and memorize information (Chapelle: 1995)

+-------------------------------------+-------------------------------------------+
| Field independence                  | Field dependence                          |
+=====================================+===========================================+
| 1. Impersonal orientation           | 1. Personal orientation                   |
| i.e. reliance on internal frame of  | i.e. reliance on external frame           |
| reference in processing information | of reference in processing information    |
+-------------------------------------+-------------------------------------------+
| 2. Analytic                         | 2. Holistic                               |
| i.e. perceives a field in terms of  | i.e. perceives field as a whole; parts    |
| its component parts; parts are      | are fused with background                 |
| distinguished from background       |                                           |
+-------------------------------------+-------------------------------------------+
| 3. Independent                      | 3. Dependent                              |
| i.e. sense of separate identity     | i.e. the self view is derived from others |
+-------------------------------------+-------------------------------------------+
| 4. Socially sensitive               | 4. Not so socially aware                  |
| i.e. greater skill in               | i.e. less skilled in interpersonal/social |
| interpersonal/social relationships  | relationships                             |
+-------------------------------------+-------------------------------------------+



: from http://www.eltnewsletter.com/back/June2002/art1022002.htm

* format
    + FI : benefit from media, detailed ressource
      analytical LS
* accessibility on learning path
    * FD : use of site map
    * FI : use index, search engine, url
* structure
    * FD : prefer linear structure over non-linear structure
* performance
    * FI : more performance on hypermedia resource

no unanimity on difference between FI and FD.

Other studies, other dimensions of learning styles.

* performance
    * verbal style : prefer hierarchical structure
    * visual style : prefer relational structure
    * global style : prefer adapted interface
    * analytic user : strong navigation skill, no particular preference to a type of interface

summerize : LS significant factor in learning in EHS

## Proposal

Trace Based System (TBS) : automatically deduce LS from behaviour.

digital trace in log files : trace learner activites inside and outside EHS.

indicators choice :

* survey of teacher's wanted feedback
* state of art on studies on digital traces
* studies above

Generally low level indicators : directly calculated from traces.
Difficult to be interpreted by teachers.

different approach : "navigation type" indicator.
class navigation behaviour :

* Overviewing : panoramic view of the course
* Studying : partial or complete reading of the course page
* Deepening : stay a long time of a course
* Flitting : wandering without strategy

qualitative, high-level indicators

Three layer learning styles :

* Educational preferences
* Learning process
* Cognitive ability

add image of hierarchical computing of indicators

