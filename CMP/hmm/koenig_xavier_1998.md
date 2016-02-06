# Xavier: A Robot Navigation Architecture Based on Partially Observable Markov Decision Process Models

## Abstract

* Autonomous mobile robots.
    * Need navigation capabilities.
    * For operate autonomously for long period.
* Use POMDPs : Partially Observable Markov Process Models.
    * Explicitly model navigation uncertainty.
        * Actuator : motors, ...
        * Sensors.
    * Approximate env knowledge.
* Maintain probability distribution of its current pose.
* Doesn't know exactly where he is.
* Never completely lost.
* Use for pose estimation, path planning, robot control, learning.
* Robust navigation

## Introduction

* Autonomous mobile robots.
* Perform delivery tasks.
* Indoor environments.
* Needs robust corridor navigation.

* Use of POMDP.
* Explicitly model uncertainty:
    * actuation uncertainty
    * sensing and sensor data
    * uncertainty in initial pose (position and orientation)
    * environment uncertainty (corridor length, blockage like closed doors)
* no single estimate, use a probability distribution of its current pose.
* Rarely knows where he is exactly.
* The robot has some belief of his actual pose.
* Thus, never completely lost.
* Update belief by using sensors information: landmarks sensed and distance traveled.

* POMDP-based navigation architecture for everyday use.
* Architecture shows property of long-term autonomy robustness in indoor environment

* Compiler directly generate POMDP from topological maps, actuator and sensor models and uncertain knowledge of env.
* POMDP seamlessly integrate metric and topology.
* Use reinforcement learning algorithm to improve the models

* Use POMDP for:
    * pose estimation
    * path planning : when, where, what
    * control during navigation
    * learning
* can be used with task planners

POMDPs

* seamlessly integrate topological information and approximate metric information
* use motion and sensors reports to determine pose distribution
* similar to Bayesian network
* lookahead is unlimited

## An Introduction to POMDPs

POMDPs constituted:

* a set of finite states S
* finite set of observations 0
* initial state distribution $\pi$
* each state has a finite set of actions A
* transition function $p$
    * $p(s'|s,a)$ transition probability that the system transition from state $s$ to state $s'$ when action $a$ is executed
* observation function $q$
    * $q(o|s)$ observation probability of observing $o$ in state $s$

POMDP *process*: stream of (state, observation, action, immediate reward) quadruples.

A process flow:

* first pick a state: $p(s1 = s) = \pi (s)$
* pick an observation from the choosen state: $p(ot = o) = q(o|st)$
* decision maker chooses an action $at$ from $A(st)$ for execution.
* decision maker receive immediate reward: $rt = r(st, at)$
* change state: $p(st+1 = s) = p(s|st, at)$
* repeat from the beginning.

Probabilities of the state $st+1$ only depends on $st$: *Marokv property*

