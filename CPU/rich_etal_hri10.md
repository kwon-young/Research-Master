# Recognizing Engagement in Human-Robot Interaction

## Abstract

engagement process between humans.
computational model for recognizing engagement between human and robot.
four types of connection events:

* directed gaze
* mutual gaze
* conversational adjacency pairs
* backchannels

integrated in ROS.
implemented in pointing-game.

## Introduction

Engagement

:   the process by which two (or more) participants establish, maintain and end their perceived connection during interactions they jointly undertake.

#. Engagement process between 2 humans
    * directed gaze
    * mutual gaze
    * conversational adjacency pairs
    * backchannels
#. engagement recognition in robot architecture.
#. implementation in ROS

### Motivation

Engagement crucial in human interactions.
humanoid robots should have some too.
Reusable engagement module without having specific task implementation mixed up.

### Related Work

failure to attend to another person gaze: lack of interest and attention.
gesture and gaze.

## Human Engagement Study

study engagement by making canapés.
videotaped sessions.
looked for engagement maintenance process.
no study of initiation or termination of engagement.

* where each person was looking
* pointed at a specific object or objects
* beginning and end of each person's speaking turn

*connections events*:

* directed gaze
* mutual gaze
* conversational adjacency pairs
* backchannels

maintaining engagement require the use of these events at some frequency.

### Connection Event Types

Directed Gaze:

* initiator : looks (optionally point) at some object
* responder : looks at the same objects
* to make the object(s) more salient in the interaction
* reference of objects in speech
* responder direct his gaze to show his cooperation, desire to continue the interaction
* pointing behavior start after looking
* several configurations of the hand in pointing
* initiator after looks at the responder face for feedback
* period of shared gaze

Mutual facial gaze:

* similar to directed gaze
* do not involve pointing
* initiator : look at the responder's face
* responder : look at the initiator's face after a delay
* start of the mutual facial gaze
* delay can be null
* intention to maintain the engagement process
* typical to establish mutual facial gaze at the end of a speaking turn
* "making eye contact"
* gaze roams around the other person's face

Adjacency Pair:

* two utterances, first utterance provokes the second.
* question answer
* generalize to verbal, gestural and gaze
* initiator : *first turn*
* delay or overlap
* responder : *second turn*
* initiator : *third trun* repairs responder's misunderstanding

Backchannel:

* responder: brief verbal or gestural communication back to initiator
* indicate comprehension, or lack of it, desire to continue ...
* no concept of delay

### Summary Statistics

nine minutes of engagement maintenance.
pace of an interaction: mean time between connection events.
the faster the pace, the less time between connection events.
increase of MTBCE indicates weakening of engagement.

large proportion of failed mutual gaze and adjacency pair events.
70 second maximum time between connection events.
indicates missing factors.
explication: non-responder is busy.

## Human-Robot Architecture

reusable component: settings, "division of labor"

### Human-Robot setting

mirror setting of the human engagement study.
robot or human can be responder and initiator.
no mobility, manipulation of the objects or changes in stance.

behavior possible:

* look at the other's face, objects on the table or "away"
* point at objects on the table
* nod the head (up and down)
* shake the head (side to side)

speech generation but no speech recognition.
only recognize begin and end of sentences.

### Information Flow

information flow via message passing.
robot architecture vague for more reusability.
cloud architecture:

* sensor processing
    * computer vision
    * speech recognition
* cognition
    * planning
    * natural language understanding
* actuators
    * control robot arm, head, eyes

important to know what information the robot architecture can give:

* where the human is looking and pointing
    * detect human-initiated events
        * directed gaze
        * mutual facial gaze
* notified of human's head nods and shakes
    * detect backchannel
    * human gestural turns in adjacency pair events
* where the robot is looking, pointing, nods or shakes
    * decisions are on cognitive components of the robot
* robot engagement goals trigger engagement recognition modules
    * start to wait for human response
    * for robot-intiated event
        * no backchannel
* *floor* primary person currently speaking
    * support recognitino of adjacency pair events
    * robot architecture decide when
        * human start/end
        * robot start/end

* engagement recognition module provide
    * notification of the start of human-initiated connection events
    * real-time feedback on state of completion of robot-initiated connection events
    * provide on-going statistics
        * robot can gauge the health of the engagement process

### Engagement Recognition Module

internal architecture.
four recognition modules in parallel.
fed into an integrator.
state-machine for each recognition modules.
multiple recognizers can be active simultaneously: overlapping events.
only one event at a time.

subset of information are fed into recognitizers.

recognizers report:

* start time
* end time
* delay duration
* successful
* failed (delay timeout)

integrator incrementally calculates:

* mean, max of delays and time between connection events.
* number of failed events per unit time
* over
    * recent time window
    * whole interaction
* estimate current strength of engagement.

## Human-Robot implementation

Each recognizer is a finite state machine.
outsider point of view.j
symmetric state machine: either robot or human can be initiator.

robot point of view : asymmetric state machine.

### premliminary validation

pointing game.
used to tune delays.

positive preliminary validation.

## Future work

larger, controlled human-robot, making canapé.
more variation on delays.
objective measure, subjective questions.

*generation* of engagement behaviors.

