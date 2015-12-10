# State of Art on Optical Music Recognition

Classical research field of Document Image Analysis and Recognition.

OMR started in 1966 with Pruslin [46].
big expansion in 80s.

High demand on OMR because composer still use "pen and paper"

## Problem Definition

Optical Music Recognition

:   `Recognition, representation and storage of musical scores in a machine-readable format. [@rebelo_optical_2012]`

Manual OMR is time consuming.

Graphical structure :

* text information
* graphical information
    * 2D structural rules

Hybride problem between OCR (contains symbols) and graphics recognition (contains graphics).

Multiple elements in a score : staff, Attributive symbols at the beginnings, Bar lines, Notes and rests, slurs, Dynamic and tempo markings, Lyrics ...

Music notation

:   visual manifestation of interrelated properties of musical sound such as pitch, dynamics, time, and timbre. [@rebelo_optical_2012].

The elements are written following a syntax and a semantic. Context information is important.

Main problem of OMR : high density, combination possibilities and variation of symbols.
Main challenge : correctly parse symbols in a score.

## Different stage of OMR

interesting figure in [@rebelo_optical_2012] Fig 1.

### Preprocessing

use of binarization, skew correction, noise removal, blurring, morphological operation.
not on the scope of the study.

### Staff removal

define vertical coordinates of pitches and horizontal direction of the time.
give size normalization.
Main challenge of OMR because it links all the symbol together.
multiple methods for staff removal :

* Projections and Run Lengths
* Candidates Assemblage and Contour Tracking
* Graph Path Search
* Hough transform
* No staff removal

+---------------------------+------------------+---------------+-------------+-------+
| Method                    | Works            | Overlapping   | Staff-lines | Speed |
|                           |                  | symbols-staff | grouping    |       |
+===========================+==================+===============+=============+=======+
| Projections, histograms   | [9, 34, 46],     | -             | ++          | ++    |
| and run lengths           | [26, 44, 50],    |               |             |       |
|                           | [11, 16, 33, 56] |               |             |       |
+---------------------------+------------------+---------------+-------------+-------+
| Candidates assemblage and | [20, 38, 53],    | +             | +           | +     |
| contour tracking          | [12, 43, 45]     |               |             |       |
+---------------------------+------------------+---------------+-------------+-------+
| Graph path search         | [8, 14, 35]      | ++            | +           | -     |
+---------------------------+------------------+---------------+-------------+-------+

: Analysis and Recognition of Music Scores

### Music Symbol Extraction and Classification

Main problems are segmentation and recognition of overlapping and broken symbols.

This is a symbol classification problem.
But some symbol can combine to form other symbol.
Classifier must be able to cope with this.

Most common method : hierarchical decomposition of the music image.

#### Template matching

Selection of good symbols comparing a region of the image with templates of music symbols.
Relative positions and mutual connections are used to correctly label a symbol.
Use of coherence checks for touching symbols.

cons :

* slow to compute
* low robustness

#### Simple Operations

Characterize a music symbol with a set of simple operations :

* analysis of bounding boxes
* projections
* morphological operations

Compare a region of the image with these property to deduce the class of a symbol.

#### Joining Graphical Primitives

Extraction of graphical primitives.
Combination of these primitives to make more complex music symbols.
Can use context or not.
Use of music notation by a set of rules.
Primitives are extracted as line, circular blobs, circles, arcs ...
Can use a classifiers like neural networks to recognize symbol with context constraints.

#### Statistical Approaches

classification methods for musical primitives :

* Neural networks
* SVM : works best
* k-NN : second best
* HMM

#### Symbol Descriptors

Use of symbol descriptors for recognition of music symbols.

decision methods :

* centroids
* Zernike moments
* decision trees
    * example : use of 278 basic features with PCA

#### Structural and Syntactical Approaches

set of method to use context to solve ambiguities.

* grammars
    * dmos system
* graphs
* fuzzy modeling
* ...

integrations of symbol recognition with validation.

+------------------------------+-------------------+------------+------------+-------+
| Method                       | Works             | Appearance | Noise      | Speed |
|                              |                   | robustness | robustness |       |
+==============================+===================+============+============+=======+
| Template matching            | [39, 46, 57]      | --         | --         | -     |
+------------------------------+-------------------+------------+------------+-------+
| Bouding box, projections     | [3, 9, 45],       | --         | --         | ++    |
| morphological operations     | [8, 34, 42]       |            |            |       |
+------------------------------+-------------------+------------+------------+-------+
| Joining graphical primitives | [38, 41, 53],     | +          | +          | +     |
|                              | [20, 33]          |            |            |       |
+------------------------------+-------------------+------------+------------+-------+
| Statistical                  | [47, 51]          | +          | ++         | -     |
+------------------------------+-------------------+------------+------------+-------+
| Symbol descriptors           | [17, 31] [18, 21] | ++         | ++         | +     |
+------------------------------+-------------------+------------+------------+-------+
| Syntactic and structural     | [50, 54, 55]      | ++         | ++         | -     |
+------------------------------+-------------------+------------+------------+-------+

### Syntactical Analysis and Validation

Interpret spatial relation between different primitives or symbol recognize.
* Reconstruct musical notation for primitives.
* Complex two dimensional structure.
* Positional information is very important.
* Context is very important


#### Grammars

grammars guide recognition.
grammars can correct recognition errors.

often only use at high-level for validation.
can be used to control the entire recognition process.

Techniques used:

* Rule based grammar
* Graph based grammar

#### Rules or Graph Grammars

can use *a priori* knowledge on music notations to predict symbol position.
also use rules to validate recognition at high-level.

top-down architecture :

* pixel
* primitives
* music symbols
* meaning
* context information

processing module

* primitive extraction
    * can recognize stems, beams, noteheads
* symbol synthesis
* symbol recognition
* semantic analysis

all have recognition and verification units.
Retro propagation of symbols to lower levels if higher levels rejects them.
One measure at a time.

Can also use a Graph grammars rules to specify syntactic and semantic rules.

## Printed Music Scores

OMR on printed scores is practically a closed subjects.
works very well.

## Old Hand Written Music Scores

Bainbridge, Carter et al.
removing staff lines with LAG.
classification with bounding-box size.
do not support overlapping or superimposed symbols.

Pinto et al.
cope with specific notation of ancient documents.
divide music sheet into staff line, bars and musical symbols.
removing staff line with horizontal projection.
bar line location with vertical projection.
recognition with a graph structure of classifiers.
reconstruction stage.
97% accuracy.

Fornés et al.
recognition of graphical primitives.
remove staff line with contour tracking.
dectect vertical line, bar lines, filled head notes using median filters.
suggestion of the use of a grammar.

Pugin.
use of HMM.
no staff removal, no segmentation.
avoid segmentation problem.
use techniques of speech recognition for music score : sliding windows, feature extractions.
number of states of HMM match width of windows.
Baum-Welch algorithm.
training phase, each staff used once.
good recognition rate.

## Modern Handwritten Music Scores

Ng.
staff removal.
segmentation and segregation to low-level graphical primitives.
classification with k-NN classifier.
use of syntactical rules for reconstructions.
intermediate stage with heuristic, musical syntax and conventions.
no recognition rate.

Rebelo et al.
test of performance of

* NN
* SVM
* k-NN
* HMM

SVM and k-NN give better results.

## OnLine Music Scores

rising sector.

George.
use of NN : MLP.
80% of recog.

Macé et al.
online system.
pen-based interaction.
formalism with context-free grammar : time, space and composition structure.
handwritten stoke parser for segmentation.
recog with heuristics of NN.
framework accept or reject hypothesis from recognizers.
no recog rate.

Miyao and Maruyama.
online symbol recognition system.
recog with time-series data and hand-drawn image features.
Use of SVM for recognition.
multiple possibility of stroke for a symbol.
98% recog rate.

# Conclusion

* music notation
* history of OMR
* main approach in each stage of OMR
    * preprocessing
    * staff removal
    * symbol recognition validation
* recognition of old music scores
* handwritten music scores
    * off-line
    * on-line
* mature state on printed score
* open problems in old score and handwritten of music scores and complex music scores.
    * hard to recognize complex symbols.
* system not applicable for productive use.
* promising approach
    * use of context information
    * structure of music score
    * music notation
* grammar is a good choice
* learning based approach
    * HMM
    * NN
    * cope with variability of handwritten music score

