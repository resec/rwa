# This fork is trying to patch the RWA model, gaining more implementational flexibility
The patched RWA model is in 'rwa_patch_model' folder under the problem folder. 
The main goal is to let RWA model to start off with 'zero states'. The changed parts are:

* The a_max is initialized as zero vector.
* Let h to be initialized as zero state.
* The s0 vector is added to n/d before the actvation of h.

(This is a ongoing work)

## Description

This repository holds the code to a new kind of RNN model for processing sequential data. The model computes a recurrent weighted average (RWA) over every previous processing step. With this approach, the model can form direct connections anywhere along a sequence. This stands in contrast to traditional RNN architectures that only use the previous processing step. A detailed description of the RWA model has been published in a manuscript at [https://arxiv.org/pdf/1703.01253.pdf](https://arxiv.org/pdf/1703.01253.pdf).

![alt text](artwork/figure.png "Comparison of RNN architectures")

Because the RWA can be computed as a running average, it does not need to be completely recomputed with each processing step. The numerator and denominator can be saved from the previous step. Consequently, the model scales like that of other RNN models such as the LSTM model.

In each folder, the RWA model is evaluated on a different task. The performance of the RWA model is compared against a LSTM model. The RWA is found to train considerably faster on most tasks by at least a factor of five. As the sequences become longer, the RWA model scales even better. See the manuscript listed above for the details about each result.

## Download

* Download: [zip](https://github.com/jostmey/rwa/zipball/master)
* Git: `git clone https://github.com/jostmey/rwa`

## Requirements

The code is written in Python3. The scripts have been upgraded to run using version 1.0 of TensorFlow.

## Alternative Implementations

 * [RWA model as TensorFlow RNNCell (with customizable attention spans)](https://github.com/jostmey/cas/blob/master/RWACell.py) (Unstable branch - Work in progess)
 * [RWA model in Pytorch (with learnable attention span)](https://github.com/bzcheeseman/pytorch-rwa) (Unstable branch - Work in progess)
 * [RWA model in Keras](https://gist.github.com/shamatar/55b804cf62b8ee0fa23efdb3ea5a4701) (Not yet tested)
 * [RWA model in Go](https://github.com/unixpickle/rwa)

## Acknowledgements

Thanks [Alex Nichol](https://github.com/unixpickle) for correcting the equations for numerical stability.

