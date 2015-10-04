#Neural Nets
[note taken from](https://www.youtube.com/watch?v=q0pm3BrIUFo)

###Introduction
* computer learning : imitate the brain

###Naive neurobiology
####Neurone is composed of :
* Axon  
  Sometimes subdivide
* dendritic tree  
  End of axons comes connecting into dendrite
* Spike

####Naive observation
1. Synaptic weights
2. Cumulative stimulus
3. All or none

####Model of a neuron
* Input box (0, 1)
  * Output1 = Input1 * Weight1
  * Output2 = Input2 * Weight2
  * …
  * OutputN = InputN * WeightN

* Summation Box
  * Output = Input1 + Input2 + … + InputN

* Thresholding box
  * step function

####Neural Net model
* Input x1, …, xn
* Summation boxes
* Threshold boxes z1, …, zn
* Z_v = f(x_v, w_v)

* Training sample
  * d_v = g(x_v)

####We need some few additional things
* How well we are doing
  * P(d_v, z_v) = -0.5*abs(d_v - z_v)²
    * we try to maximize the performance function


