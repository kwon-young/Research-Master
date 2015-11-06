# Machine learning and estimation theory

## Why statistical modeling

we're moving to inferential statistics

* generalize
* decide

* summarize data using a parametric model
* estimate the parameters of a model
* decision, discrimination, classification
* prediction

*Summarize all the data available in a model* for witch the number of
parameters is small with respect to the amount of data

* compare values, models
* take decisions
* classify
* predict

parametric vs. non parametric

## Why mixture model

* can approximate any weird distribution

## Mixture model - definition

* a mixture model is a weighted sum of laws
* f(x) = sum(pii,fi(x))
* sum(pii) = 1
* fi() can be any density and the fi()'s need not be from the same family
* f() is a density since Integral(f(x)dx, -00, 00) = 1

## Examples of mixture model densities

* the weight are also parameters of the model
* weights are crucial and can change drastically the shape of the model

## mulstivariate gaussian mixture model

* each component of the mixture is a multivariate gaussian density
* parameters of the model
  * weights of each component
  * mean vectors
  * covariance matrices
  * typical value of K is 60 to 300
  * huge number of variable
* in practice, we often assume diagonal covariance matrices
  * much less parameters
  * much less computation
  * can be compensated with more components
  * ellipse following x axis or y axis

## mixture models from the generative viewpoint

a sample is drawn according to the law of the component fi() of the mixture probability pii

practically, sampling is a two step process

* randomly choose a component i of the mixture according to the discrete law defined by the weights wj
* draw a sample according to the law fi()

* there is a great deal behind this thing
* we know the link between data point and the mixture model

* Interpretation (from a generative point of view
  * for each point, i know from witch distribution it come from

## mixture models and hidden variables

* the law of x is the marginal over the hidden variable Z
* indicator variable Z
* conditional density
* joint density
* marginal density

##maximum likelihood with complete data

* the set of training samples x is incomplete
* assume for each sample xi, we know the component indicator function zi
* the set {x1, z1, ..., xN, zN} is known as complete data
* maximum likelihood estimates can be obtained from the complete data
* => but the variables zj are not known !!!!

## the expectation-maximization principle

* the expectation-maximization (EM) principle compensates for missing (aka latent) data, replacing them by their expectations
  * estimate the missing variables given a current estimate of the parameters
  * estimate new parameters given the 

## the auxiliary function

* the em algorithm aims at maximizing an auxiliary function
* estimation step
maximization step

people.irisa.fr/Guillaume.Gravier/ADM/
