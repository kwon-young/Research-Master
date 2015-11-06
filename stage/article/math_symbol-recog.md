# Using Off-line Features and Synthetic Data for On-line Handwritten Math Symbol Recognition

## Abstract

* using on-line recog with off-line recog feature
* synthetic data generation
  * generate new set of data with elastic distorsion
* validation by comparison
  * AdaBoost.M1 with C4.5 decision trees
  * Random Forests
  * Support-Vector Machines
    * linear kernel
    * Gaussian kernels
* don't use timing information
* feature set based on *shape description*
  * greater tolerance to variations
* data set CROHME
* using elasting distortion model to improve recog rate
* test system using MathBrush dataset
  * 89.87% of accuracy

## Introduction

* automatic recognition of math expression is hard
  * more hard if handwritten
* two mode
  * on-line
    * tracing info available
  * off-line
    * tracing info not available
    * final image provided
* goal : adapt off-line feature to on-line feature
* training dataset biased because few class in dataset
  * reduce disparity with generating synthetic data with elastic distortion
* tested with
  * AdaBoost.M1 alg using C4.5 decision trees
  * Random Forests
  * SVM with linear and Gaussian kernel
* input : simple features describing shapes of each symbol
* dataset from CROHME 2012 and 2013
* benchmarked the system using MathBrush database
* specific problem of isolated on-line math symbol recog
* _important_ : set of features used to describe each symbol
* in Yang et al. [11]
  * feature extraction based on
  * timing or drawing info on on-line symbol recognition
  * shape description should be more robust
    * _multiple way to draw a shape_
* _important_ : good training data
* to improve quality of training data
  * generate synthetic data from the existent
  * Simard et al. [18] used elastic distortion model
  * Plamondon et al. [19] used Sigma-lognormal model of the kinematic theory of rapid human movement
    * produce realistic synthetic on-line signature and handwritten gestures
* _important_ : balanced representation of classes in dataset
  * choose good data generation strategy
* multiple class for a single feature

## Strategy for Data Generation

* bad generation of synthetic data could lower accuracies of classifiers
* here, data generation strategy only to balance class representation in training set
* data generation strategy
  * all classes should have min nbr of samples





