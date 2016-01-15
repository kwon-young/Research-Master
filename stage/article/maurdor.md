# The A2iA Multi-lingual Text Recognition System at the second Maurdor Evaluation

## Abstract

Maurdor : database of multilingual text used on OCR evaluation

System proposed:

* recurrent neural network
* weighted finite state transducers
* bot printed and handwritten recog
* French, English, Arabic
* Multiple text line segmentation

Automatic procedure for training the system.

Scored first in maurdor evaluation

## Introduction

## Maurdor Challenge

Complete document processing chain :

* document layout analysis
* write type identification
* language identification
* text recognition
* logical organization
* information extraction

## Optical Model

input : paragraph of text

### Training data preparation

Automatic system for alignment of annotation and line images.

### MD LSTM RNN

work directly on pixel value
[9]
4 LSTM layers in parallel for 4 directions
one RNN for each task : 3 languages handwritten and printed
trained using CTC[10] because no explicit character segmentation.
[13] for arabic

Changed sub-sampling filter size
tuned hidden layer sizes for the dataset

Using dropout [14]

used stochastic gradient descent
Used of pretrained network on clean dataset for better and faster convergence.

Intermediate layers are marked as Convolution, but in Graves uses Feedforward layer

### Language model

Choose a character set.

