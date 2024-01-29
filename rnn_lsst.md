---
layout: default
---

## Predicting LSST Data with Keras Tuner & Recurrent Neural Networks ##
_Executive Summary_

__Overview__

Recurrent Neural Networks (RNN) have a distinct capacity for processing sequential
data, like time series, thanks to their memory and backpropagation through time (BPTT). This
project utilized RNNs to predict target variables from the Large Synoptic Survey Telescope
(LSST) dataset. The LSST dataset is a time series dataset containing light curve measurements
for different astronomical objects and an adaptation by Dr. Noriko Tomuro (DePaul University) of the PLAsTiCC Astronomical Classification competition from Kaggle.com (https://www.kaggle.com/c/PLAsTiCC-2018)

__Problem Summary__
Classify LSST data with a reccurent neural network developed from scratch. 

__Solution Summary__
Simple RNN, LSTM, GRU & Conv1D Keras TensorFlow networks were iteratively tested
with growing complexity. Normalization was applied within the network. Network accuracy and loss for both
training/validation sets was used to guide determine additional layers. These metrics were also
used to determine which network would go through hyperparameter tuning

__Conclusions & Future Work__
Combining hybrid networks with Keras Tuner ultimately did create a more robust, generalizable network. The best network had 2
SimpleRNN layers, 1 Conv1D layer, 2 dropout layers, 2 dense layers and 1 flatten layer.  For time series data, the hybrid network was better able to capture short term patterns
as well as long term trends.

[Sample of Techincal Report](./)

[Sample Python Code](./)

[All Projects](./)
