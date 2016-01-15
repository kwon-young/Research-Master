# Offline Handwriting Recognition with Multidimensional Recurrent Neural Networks

OCR : combines computer vision and sequence learning

use of MD RNN and CTC

no alphabet specific preprocessing

can be used unchanged for any language

outperform all other system on arabic recog

## Introduction

Offline harder than Online.

problem of HMM : long-term dependency (feature choosed for a specific alphabet)

system proposed 

* works on raw pixels
* alphabet-independant
* globally trainable
* image features optimised with the classifier

offline case is not one-dimensional data (INTERESTING !)

MDRNN : special case of acyclic graph networks

* provide recurrent connection to all spatio-temporal direction
* robust to local distorsion
* use of LSTM for long range context

Transform 2D images into 1D sequences by a hierarchical MDRNN layers.
Incrementally collapse 2D images to 1D sequences.
Complex features built up in stages.

When using convolutional network, input should be presegmented.

## Method

### MD RNN

replace single recurrent connection with connection to all spatio-temporal connection.
Create flexible internal representation of surrounding context.
Robust to local distortion.

Different to bi-dimensional RNN, that are 1D RNN and is used to deal with past and future dependency.

2D networks has 4 layers that scan from each corner of the image.
Single output layers, that have context from each directions.

MDRNN is trained with backpropagation alg generalized to n dimensions.

### LSTM

designed for long term dependency.

LSTM layer :

* recurrently connected *memory cells*
* activations controlled by 3 multiplicative gain units
    * input gate
    * forget gate
    * output gate
* gates are used to do store and retrieve action : possibility of long term dependency

standard LSTM are 1D :

* single recurrent connection
* single forget gate for activation

generalization to ND :

* N recurrent connections
* N forget gates

### CTC

output layer.

designed for sequence labelling.

trains the network to estimate the conditional probabilities of the possible labellings.

CTC output layers contains N+1 units for alphabet of size N.
output normalized with softmax function.
0 to N units estimates the prob of obs of corresponding label
N+1 unit estimates the blank

Operator B used to removes repetition.

Objective function : negative log prob

Once trained, take the highest conditional probabilities.

### Network Hierarchy

Hierarchical approach for feature extraction.

Allow complex visual properties to be built.

* use subsampling : decrease resolution
* more feature at higher levels

Hierarchical structure : interleaves MDLSTM layers with feedforward network.
Activation of MDLSTM layers are gathered into blocks, therefore allowing subsampling.

purpose of blocks

* local contextual information
* reduce the area of the activation arrays : reduce 2D image to 1D sequences
    * subsampling

Commonly, three layers of MDLSTM/Feedforward gives the best results for OCR.
*Inverted pyramid structure* : small layer at the bottom and large at the top.

## Experiment

ICDAR competition : arabic handwritten recognition

Identify Tunisian postcodes

## Conclusion

Can be used on any supervised sequence labelling task

