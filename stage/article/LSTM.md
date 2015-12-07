# Long Short-Term Memory

Author :

* Sepp Hochreiter
* Jürgen Schmidhuber

## Abstract

Prob of back propagation alg is vanishing or explosion of gradient.
Cons is learning slow down.

New gradient-based alg to to address this prob.

Constant error flow.
Open or close multiplicative gate.
Computation complexity of LSTM is O(1).

# Introduction

RNN used for short-term memory.
slow learning alg, specially when time lag is big.

Problem

:   on BPTT, RTRL, error signals can :
    
    * blow up : introduce oscillation.
    * vanish : slow learning.

Solution

:   LSTM RNN and appropriate gradient-based learning algorithm.
    memory time intervals can excess 1000 steps.
    use of constant error.

## Previous Work

On s'en tape.

## Constant Error Backprop

### Exponentially Decaying Error

If derivative of activation function is > 1 : error grow exponentially.
Lead to oscillation.

If derivative of activation function is < 1 : error decrease exponentially.
With logistic sigmoid activation function, error tend to vanish.

### Constant Error Flow: Naive Approach

For a single unit.

Use of the Constant Error Carrousel.
Input weight conflict. Need the use of "more context-sensitive mechanism".
Use of "write operation" for input weights.
Output weight conflict.
Use of "Read operation" for output weights.

## Long Short-Term Memory

CEC used with :

* multiplicative input gate unit.
    * protect memory stored in the unit from irrelevant input.
    * need to learn which error to release.
* multiplicative output gate.
    * protect other units from irrelevant memory of the unit.
    * need to learn which error to keep.

This is called a *memory cell*.

Network Topology : 3 fully connected layer, input-hidden-output.

*Memory cell blocks* : S memory cells sharing same input and output gates.


