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
    * pbm : improve segmentation and recognition of overlapping and broken symbols
    * way to improve dmos:
        * use new techniques of deep learning for segmenting and recognizing music symbols
    * objectif : working on very large orchestral score and handwritten score

# Optical Music Recognition (OMR)

## Definition

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

## State of art of OMR

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

### Preprocessing

Techniques reviewed in [@rebelo_optical_2012 and @fornes_analysis_2014].

* binarization
* skew correction for staff line
* noise removal for bad scanning and digitalization
* blurring
* morphological operation

### Staff removal

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

### Music symbol segmentation and recognition

[@rebelo_optical_2009]

Variability in music symbol is source of complexity.
Digitalization and paper degradation adds noise and difficulty for this operations.

Usual way of segmenting a music score:

* extract graphics primitives like:
    * line
    * blobs
    * circles
    * ...
    * joins these graphical primitives for recognition stage.
* extract symbol with template matching
    * comparison of regions of the images with templates of music symbols
    * slow to compute
    * low robustness
* simple operation
    * compute simple feature of candidates as bounding box, projections, morphological operations
    * compare with same features extracted from an region of interest of the image to recognize a symbol.
* symbol descriptors
    * use symbol descriptors instead of the raw pixel information
        * centroids
        * Zernike moments
        * decision trees
* use of classifiers
    * HMM : segmentation and recognition phase are merged.
    * NN
    * SVM
    * k-NN

### Music score reconstruction

Interpret spatial relation between different primitives or symbol recognize.

* Reconstruct musical notation for primitives.
* Complex two dimensional structure.
* Positional information is very important.
* Context is very important

Techniques used:

* use of a fuzzy modeling
* use of grammar
    * grammar guide recognition
    * grammars can correct recognition errors
    * Rule based grammar: [example @couasnon_dmos:_2001]
    * Graph based grammar

#### DMOS system : Generic Document Recognition Method


The DMOS system [@couasnon_dmos:_2001] is system developed by the Intuidoc team at the Irisa lab.
DMOS

:   Description and MOdification of Segmentation.

General method for recognition of structured documents.

Main purpose is to separate the semantic and graphic knowledge of the program that do the recognition task because there is a `discrepancy between the way knowledge describe an object and the way object have to be recognized` [@couasnon_dmos:_2001].

* use a grammar for formalizing the syntax and graphical organization of the documents
    * this grammar is derived of the EPF grammar (Enhanced Position Formalism)
    * expressed in $\lambda$Prolog
    * two levels of grammar
        * physical level : image base level
        * logical level : work on the semantic level of the document
    * use simple *terminals* like line or connected components to expressed complex structures
    * use of spatial and logical operator to construct the graphical semantic of the document
* this grammar is compiled and converted into an appropriate parser that do the low-level image recognition of the image documents.
    * use of the context for segmentation and recognition
    * do as few error as possible

Used initially on OMR for orchestral scores, then on various forms, especially on old military forms.

# Symbol classification with prior segmentation

There techniques are used after the step of segmentation.
Comparative study in [@rebelo_optical_2009].
We test regions of interest of the image using different classifiers:
Use of raw pixel inputs.
dataset is a set of symbols. 60% used for training, 40% used for validation.

* k-NN
    * simple algorithm
    * use of euclidean distance
    * better results than NN and HMM.
* NN
    * use of Multi Layered Perceptron
    * use of backward-propagation algorithm for training the neural nets
    * disappointing results
        * the study has been conducted in 2009
        * very outdated
        * there are new way of using neural nets using deep learning and recurrent neural network.
* SVM
    * radial basis function network used.
    * best classifiers at the time.
    * need first a segmentation phase

## Merging recognition and segmentation phase for classification of music symbols using HMM

Almost never implemented on OMR.
Implemented in [@pugin_optical_2006].

* avoid staff removal
* avoid segmentation phase
* because these step are important source of errors
* dataset have been generated by annotating manually partitions with graphical informations
    * 240 pages of music scores
    * 175 different symbols
* imitate speech recognition by using a sliding windows
* hypothesis of having only a succession of notes from left to right
    * do not handles chords
    * use a left-right HMM: sequential and unidirectional model
* extract 4 to 40 features from raw image
* trained using Baum-Welch algorithm.
* ~ 96% recognition rate
    * but recognition rate are highly dependent of features chose, sliding windows width ...

# Overview of latest techniques used in OCR and speech recognition

Main problems of OMR are segmentation and recognition of overlapping and broken symbols.
Even if printed score are well recognized, handwritten score are still very challenging for nowadays OMR systems.
These problems could be resolved by using more context information and avoiding context information.

In the history of OCR:

* First used NN or SVM for classifying letters.
* Then avoid the segmentation phase by using HMM
* Lately, using deep learning techniques and new structures of neural networks
    * avoid segmentation phase
    * use of context information by using recurrent neural network

## Using context information with recurrent neural network

In [@hochreiter_long_1997], presentation of a new recurrent neural network structure

* recurrent neural network have the problem of vanishing and exploding gradient during training phase
* these RNN truncate the gradient in order to avoid these problems
* ensure constant error flow through "constant error carrousels"
* unit of the network is not a neuron but a memory cell constituted of
    * multiplicative input gate unit.
        * protect memory stored in the unit from irrelevant input.
        * need to learn which error to release.
    * multiplicative output gate.
        * protect other units from irrelevant memory of the unit.
        * need to learn which error to keep.

Network Topology : 3 fully connected layer, input-hidden-output.

Network pro: have long time memory
These network could be used in OMR because they use context information.

In [@messina_segmentation-free], they applied this kind of network architecture on recognizing line of handwritten Chinese text without explicit segmentation.

* use of multi-dimensional LSTM-RNN
    * multidimensional because they use a horizontal and vertical sliding windows.
* use Connectionist Temporal classification introduced by [@graves_connectionist_2006]
    * can train RNN without pre-segmenting training data and post-processing the output of the network
    * allow to automatically segment the output of MDLSTM RNN

These kind of network could be used on OMR directly on staff level.

* pro:
    * use of context information
    * automated segmentation
* cons:
    * can only segment one dimensional data
        * in OMR, we need the exact two dimensional position (x, y) of a symbol
    * they have to be trained on line of data like graphically annotated staff of music scores
        * currently, there is no database with graphically annotated music scores

## Localizing object in image with convolutional neural network

OMR is a hybrid domain between structured document recognition and image recognition.

In [@erhan_scalable_2014], use of Deep convolutional neural network for scalable object detection and localization.

* deep network : 
    * use multiple convolutional network
    * multiple max-pooling layer
    * soft-max layer as output
* in [@erhan_scalable_2014], layer can output a bounding box coupled with a confidence score
    * bounding box are not predefined
    * pros:
        * can output two dimensional graphical information
        * scalable bounding box, could be very useful in OMR where there are multiple representation of the same symbol but scaled differently
    * drawbacks:
        * they still have to be trained on data with graphical annotation which we don't have in OMR.

# Conclusion

* OMR is an hybrid domain between structured document recognition and image recognition
* difference step of OMR
    * preprocessing
    * staff removal
    * music symbols segmentation and recognition
    * reconstruction of the music score
* we want to improve the music symbols segmentation and recognition step by:
    * merging segmentation and recognition
    * use more context information
* avenue for research from OCR and speech recognition
    * using LSTM RNN for using context information
    * using CTC for automated segmentation
* avenue for research from pattern recognition
    * using CNN for generating two dimensional information like bounding boxes

# References
