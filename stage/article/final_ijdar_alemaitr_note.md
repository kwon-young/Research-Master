# Multiresolution Cooperation Makes Easier Document Structure Recognition

## Abstract

* imitation of human perceptive vision
* improve recognition of ancient, noisy and low structured documents

* perceptive vision
  * global vision process
  * focus on interesting elements

* use of a generic method
* to apply on various document

* cooperation between multi resolution vision
* cooperation is led by Domain Specific Knowledge

* validated work

## Introduction

* perceptive vision consists of :
  * global vision of a document
  * focuses on points that attracts the eye interest
* work on damaged and low structure documents
  * large variety of structure
  * irregular printing or writing, noise, ink bleed ...
* perceptive vision useful for low structured documents
* in global vision, noise is reduced
  * noise doesn't disturb the study of the organization of elements
* context DMOS
  * EPF
  * associated parser automatically produced by compilation
  * separation of knowledge from recognition system
  * can implement multiresolution vision in a generic way
  * cooperation is guided only by knowledge

## Related work

### Interest of perceptive vision for image processing

* Bajcsy and Rosenthal [2]
  * people focus their attention on interest points
  * visual hierarchy
    * different sized images
  * conceptual hierarchy
    * knowledge varies according to the level of analysis
  * control structure manage interaction between them
  * work only applied for dedicated images
* Burt : Pyramid Vision Machine [4]
  * fine-to-coarse algorithm : ?? how does he do a pyramid with fine-to-coarse alg ??
    * dense triangulation, then join adjacent triangle
  * to generate a Gaussian pyramid of images
  * then coarse-to-fine algorithm to rapidly locates objects within a scene
  * high level mechanism
    * guide data gathering
  * used in smart surveillance and mechanisms of alerting
* Dyer [12]
  * synthesize key points of multi resolution analysis
  * persistence of a property over a range of scales
  * coarse-to-fine search for a given feature
  * detect global content with operation as
    * coarse scales
    * hierarchical organization linked with perception
  * used in model-based object recognition
* Silberg : framework for multi resolution vision of object [20]
  * data structure : Multiresolution Symbolic Pixel Array
    * pixel properties
    * object properties
    * object spatial relationship for each resolution
  * interpretation
    * make hypothesis about the presence of an element on each resolution
    * interpretation on the smallest resolution
    * successive focusing confirm or not the hypothesis
  * not a generic method
* Jolion and Rosenfeld [13]
  * overview of framework for multi resolution computer vision
  * no high level knowledge

### Usage of multi resolution in document structure recognition

* Bloomberg [3]
  * multi scale approach
  * to detect shapes and textures
  * morphological tools : ?? what is it ??
  * used on font style identification
  * low level processing
* Dynamic Local Connectivity Map : DLCM [19]
  * varying connectivity threshold
  * used on segmentation of column blocks and graphics in journals, magazine and books
  * difficult to include special knowledge for complex document
* Déforge and Barba [11]
  * at a certain resolution
    * text lines appear as regular stokes
  * pyramid of image to detect line of text
  * used in postal documents
  * no cooperation between levels
* Cantoni et al. [5]
  * pyramidal representation of images
  * four feature maps :
    * average, variance, threshold and the median
  * each feature map built on four resolution
  * three fixed processes
    * background analysis
    * graphics analysis
    * text analysis
    * based on the content of feature maps
  * no direct cooperation between resolution
* [7] used on newspaper
  * high level analysis
    * extract logical decomposition of documents
  * two steps
    * blocks extraction using global vision
    * detail each block at low resolution
  * specialized only for newspaper
* [6] Bayesian approach
  * used on magazine page
  * segmentation into blocks
  * classifications
  * model has to be trained
  * difficult to insert specific knowledge

### Position of our approach

* use a cooperation between resolutions
* guided by high level knowledge on the structure
* inject this mechanism into a generic method
* apply to various kind of documents

* combine several points from litterature
  * visual and conceptual hierarchies [2]
  * pyramid of images built with fine-to-coarse [4]
  * high level analysis : introduction of a larger knowledge
* implementation independent of the document
* global approach to indifferently treat handwritten or printed documents
* various structures

## Intuitive need of multiresolution vision

### Low structured documents

* no line or regular block
* example : handwritten mail documents
  * extract text blocks
    * sender details
    * address details
    * date, place, ...
  * not always present, various disposition
  * perceptive vision give global vision
    * detect text lines and blocks
  * task to classify these blocks
  * logical segmentation depends on classification
  * generic system
    * introduce specific knowledge for each language

### Noisy printed and handwritten documents

* noise : information outside the recognition system vocab
  * bleed through ink, overlapping text lines, spotty documents
  * connected component biased by noise
  * use of global vision to decrease influence of noise
* used on naturalization decree registers
  * no structure lines, but structure stable
  * goal : detect decomposition into successive acts
  * presence of both printed and handwritten text in global vision
  * noise and damaged paper
    * use of perceptive vision to treat equally printed and handwritten text
    * cooperation of global vision
      * to detect structure
    * and accurate view
      * to treat text

### Search of absent headline

* element only perceptible on low resolution
* second step : find exact position of el on high resolution
* used on Bangla document
  * complex due to large number of characters combinations
  * detect headline in global vision
  * global slope of each text line in perceptive vision
  * determine exact vertical position of headline using focus

## General DMOS method

### Principle of the method

* DMOS
  * EPF grammar
  * associated parser able to deal with noise
    * bi-dimensional parser
    * changing the parsed structure during parsing for contextual segmentation
    * detect next element to parse using AT operator
    * dealing with noise
    * try all combinations until one succeeds
  * digital level analysis extract feature
    * called terminals in the grammar
    * connected components
    * line extractor : Kalman filtering
      * ability to deal with dotted lines, curvature and skew, line segments running into each other
  * symbolic level
    * EPF grammar

## Multiresolution cooperation

* improved existing digital level to multi resolution digital level
* digital features from images at various resolutions
* each level of resolution
  * image
  * associated cmp and line segments
  * multi resolution terminals of the grammar
* cooperation on two axes :
  * changing point of view
    * during analysis
    * *Changing point of view* operators
  * positioning elements
    * *Positioning* tool

### Multiresolution digital features

* can use as many resolutions as required
* low-pass filtering for building different resolution
* low-pass filter imitate human eyes
* for each chosen resolution
  * apply feature extractors (cmp or line)
* all features are represented on the same imae
  * simplify cooperation between resolution
* cmp vary with resolution
  * few noise detection on low resolution
* line detected mostly on low resolution
* experimentally notice
  * inside a set of documents
  * perceived feature are stable for a given resolution
  * minimum step of four between resolution levels
* minimum use of two resolution

### Control of multi resolution

* cooperation on digital features
* change level of analysis freely

#### Changing point of view

FOCUSING ON FOR operator

```Prolog
textLine::=
    lineSegment &&
    AT(lineSegmentZone) &&
    FOCUSING ON(upperResolution)
        FOR(groupOfComponents).
```

* powerful text line recognition
* recursive navigation between resolution levels
  * combination of features coming from different resolutions

1. Detect text lines as line segments
2. Deduce the position of the margin
  1. Focus at original resolution in margin
    * find registration number as succ of cc
  2. go back to low resolution
    * find text line in body, in front of the previous number
  3. Focus at original resolution
    * on previous text line, detail component ...

* succ navigation between resolutions = perceptive vision

#### Positioning

* difficult to link
  * text line
  * corresponding cc of the text line
* tool to transfer low resolution segment on high resolution
  * POSITIONING\_LINE LineSegment ResolutionName Position

# Conclusion

* cooperation between multi resolution visions
* for structured documents
  * large vision to detect the structure of the document
    * reduce noise
  * close vision to give precise details of elements
* cooperation between resolution is led by grammar
* coop bidirectionnal
* multiresolution cooperation improve recognition and divide execution time
* use of global vision to detect structure of document
* digital positioning when strong precision is asked

* multiresolution approach
* generic method
* large scale of various document
* multiresolution cooperation
  * more reliable on noisy document
  * decreases running time
  * improve recognition rate
