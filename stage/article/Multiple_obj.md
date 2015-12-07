# Multiple Object Recognition with Visual Attention

adapted from human vision

deep recurrent neural network

process multi-resolution image = glimpse

update internal representation input and output

predict possible next object in sequence

continue until model decide there is no more

train alg: reinforcement learning

can localize and recognize multiple objects purely from label sequences

## Deep Recurrent visual Attention Model

Sequential process of N steps

saccade and glimpse

for each step n:
  new location ln
  new glimpse xn at ln
  update internal state
  outputs ln+1

model with sub-component,
each sub-component is a neural network :

* glimpse network
    * Gimage(xn|Wimage) = convolutional layer
    * Gloc(ln|Wloc) = fully connected layer
    * gn = Gimage*Gloc
* recurrent network
    * 2 recurrent layer
    * LSTM
* emission network
    * fully connected hidden layer
* context layer
    * compute initial glimpse from whole low resolution image
* classification network
    * output a prediction from 1st RNN layer
    * fully connected hidden layer + softmax

