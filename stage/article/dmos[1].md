# A Symbol Classifier Able to Reject Wrong Shapes for Document Recognition Systems

## Abstract

Classifiers able to deal with reject notions.

Developed classifiers properties :

* strong reliability
* good generalization

Used on OMR.

Method :

#. extract known symbols.
#. validate segmentation hypotheses

Validation on :

* musical symbols database
* digit symbols database

## Introduction

Symbol recognition is the heart of document recognition.
Using neural network symbol classifier.

Problem

:   classifiers train only on known classes shapes.
    But classfiers are presented with good and wrong shapes.

Solution

:   Implement a notion of reject.
    Specialize classifiers to groups of classes.
    Chain them produce robust and global identification.

Integrated solution on complete OMR.

## Integration of a Classifier in a Musical Score Recognition System

Symoblics

:   primitive shapes

Constructed

:   composed of primitives plus a set of assembly rules

Document recognition system method :

#. extract symbolics
    * precondition : image segmentation
    * recognize learn classes, reject others
#. syntactic or semantic segmentation
    * prob : bad segmentation
        * Touching symbolics
        * Over-segmented symbolics
    * solution
        * bring context in segmentation
        * make re-segmentation hypotheses
    * hypothesis validated with symbol classifiers

Musical scores recognition system developed.

## A Framework to Design Reliable Classifier

* RBF neural networks
* transparent classifier to deal with reject notion
* fuzzy clustering for a robust learning phase
* genetic algorithms for feature selection

## Conclusion

RBF neural network classifier able to deal with reject notion.
Classifier reliability is important on document recognition.
Fully understandable structure of the RBF,
permit to use GA to control reliability : reject and sensibility.

Good performance on OMR.
