---
title: Segmentation and recognition of symbols for printed and handwritten music scores
author: Kwon-young Choi
date: December 8, 2015
tags: OMR, OCR, neural net, lstm, cnn, bibliography
bibliography: stage.bib
---

# Introduction

* state of art of OMR
    * hybrid field 
        * structured document recognition
        * image recognition
    * multiple phase
        * preprocessing
        * staff removal
        * symbol segmentation
        * symbol recognition
        * semantic reconstruction
* dmos system
    * general purpose document recognition
    * grammar
    * parser
    * classifier
        * reject notion
* music symbol segmentation and recognition
    * merging the two phase
        * pro
        * cons
    * different techniques used
        * markov chains
    * use of deep learning techniques
        * in OCR with lstm networks
        * in object recognition with convolutional

# Internship subject definition

* Improve dmos system for OMR.
    * pbm : overlapping and broken symbol
    * objectif : working on very large orchestral score and handwritten score

# Optical Music Recognition (OMR)

Optical Music Recognition

:   Recognition, representation and storage of musical scores in a machine-readable format. [@rebelo_optical_2012]

Hybrid problem between structured document recognition and graphics recognition.

OMR usefull, because manually annotating score are very time consuming.
A lot of scores are stored in image based format.

Structure of a score:

* graphical information
    * 2D structural rules
    * hierarchical structure
    * multiple elements in scores
        * staff
        * attributive symbols at the beginnings
        * bar lines
        * notes and rests
        * slurs
        * Dynamic and tempo marking 
* textual information like lyrics

Main problem in OMR:

* high density of symbols
* high connectivity between symbols
* high variation of symbols
* high combination possibilities
* overlapping and broken symbols
    * this is the main challenge nowadays

Stage of OMR are:

* preprocessing
* staff removal
* symbol segmentation
* symbol recognition
* music score reconstruction

![Stage of OMR, From @rebelo_optical_2012.](OMR_stages.jpg)

Main objective of this document is to study symbol segmentation and recognition.
First, fast overview of preprocessing, staff removal, music score reconstruction.
Then, extensive study of different techniques in symbol segmentation and recognition.
In OMR and then in OCR and image recognition.

## Preprocessing

Techniques reviewed in [@rebelo_optical_2012 and @fornes_analysis_2014].

* binarization
* skew correction for staff line
* noise removal for bad scanning and digitalization
* blurring
* morphological operation

## Staff removal

Staff are a group of five line that define the pitch of notes and the direction of time.
Why staff removal ?
Because they connect all symbols together, so segmentation is impossible.
Main challenge of OMR.

Main techniques reviewed in [@rebelo_optical_2012 and @fornes_analysis_2014].

* Projection and Run Lengths
    * cannot deal with overlapping symbol
    * fast to compute
* Candidates Assemblage and Contour Tracking
    * can deal with overlapping symbols
    * relatively fast to compute
* Graph Path Search
    * deal well with overlapping symbols
    * slow to compute
* Hough transform

## Music score reconstruction

Use of grammar and syntactical rules to formalize the music score.

### DMOS system : Generic Document Recognition Method


The DMOS system [@couasnon_dmos:_2001] is system developed by the Intuidoc team at the Irisa lab.
DMOS

:   Description and MOdification of Segmentation.

General method for recognition of structured documents.
Used initially on OMR for orchestral scores, then on various forms, especially on old military forms.

Main purpose is to separate the semantic and graphic knowledge of the program that do the recognition task because there is a `discrepancy between the way knowledge describe an object and the way object have to be recognized` [@couasnon_dmos:_2001].

* use a grammar for formalizing the syntax and graphical organization of the documents
    * this grammar is derived of the EPF grammar (Enhanced Position Formalism)
    * expressed in λProlog
    * use simple *terminals* like line or connected components to expressed complex structures.
* this grammar is compiled to appropriate parser that do the low-level image recognition of the image documents.
    * use of the context for segmentation and recognition
    * do as few error as possible



# References
