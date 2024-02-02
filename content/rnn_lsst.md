---
layout: default
---

### Predicting LSST Data with Keras Tuner & Recurrent Neural Networks ###
***
__Overview__

Recurrent Neural Networks (RNN) have a distinct capacity for processing sequential data thanks to their memory and backpropagation through time (BPTT). This project utilized RNNs to predict target variables from the Large Synoptic Survey Telescope (LSST) dataset. The LSST dataset is a time series dataset containing light curve measurements for different astronomical objects. The dataset used for the project was an adaptation by Dr. Noriko Tomuro (DePaul University) of the 2018 PLAsTiCC Astronomical Classification competition from Kaggle.com (https://www.kaggle.com/c/PLAsTiCC-2018).  

__Problem Summary__

Classify Large Synoptic Survey Telescope (LSST) data by developing a reccurent neural network. 

__Solution Summary__

Simple RNN, LSTM, GRU & Conv1D Keras TensorFlow networks were iteratively tested with growing complexity. Normalization was applied within the network. Network accuracy and loss for both training/validation sets was used to guide determine additional layers. These metrics were also used to determine which network would go through hyperparameter tuning using Keras.tuner

Simple RNN - Basic form of a recurrent neural networks. Retains information from the prior time step to process sequences of data. 

LSTM (Long Short Term Memory)- More sophisticated RNN layer designed to combat the vanishing gradient often the problem with SimpleRNN layers alone. Computationally expensive. 

GRU (Gated Recurrent Unit) - Balanced between Simple RNN & LSTM, has an update gate to inform the network. 

Conv1D (One Dimensional Convoluted Layer) - Capture local patterns in the input sequence, allowing the model to learn hierarchical representations of the data.

Normalization was applied within the network. If a network appeared to be underfitting (high loss, low accuracy) additional RNN layers were introduced. If a network appeared to be overfitting (low loss/high
accuracy for training set, high loss/low accuracy for testing set) dropout layers in varying positions were tested, as well as BatchNormalization and Maxpooling. These metrics were also used to determine which network would go through hyperparameter tuning using Keras.tuner. 

__Conclusions & Future Work__
Combining hybrid networks with Keras Tuner ultimately did create a more robust, generalizable network. The best network had the following structure: 3 SimpleRNN layers, 1 Conv1D layer, 2 Dropout layers, 2 dense Layers, 1 Flatten.. A hybrid network was better able to capture short term patterns as well as long term trends present within the time series data. 

[View Sample Code in Google Colab](https://colab.research.google.com/drive/1Omal3X0fSY9rjPrzb3GDtFtpzwWer8hy?usp=sharing)

[All Projects](/index.html)
