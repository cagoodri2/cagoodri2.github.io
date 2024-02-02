---
layout: default
---

### Predicting LSST Data with Keras Tuner & Recurrent Neural Networks ###
***
__Overview__

Recurrent Neural Networks (RNN) have a distinct capacity for processing sequential data thanks to their memory and backpropagation through time (BPTT). This project utilized RNN's to predict target variables from the Large Synoptic Survey Telescope (LSST) dataset. The LSST dataset is a time series dataset containing light curve measurements for different astronomical objects. The dataset used for the project was an adaptation by Dr. Noriko Tomuro (DePaul University) of the 2018 PLAsTiCC Astronomical Classification competition from Kaggle.com (https://www.kaggle.com/c/PLAsTiCC-2018). 

__Problem Summary__

Classify Large Synoptic Survey Telescope (LSST) data by developing a reccurent neural network. 

__Solution Summary__

Simple RNN, LSTM, GRU & Conv1D Keras TensorFlow networks were iteratively tested
with growing complexity.

Simple RNN - 

LSTM - 

GRU - 

Conv1D - 

Normalization was applied within the network through NEEDED layers. Network accuracy and loss for both training/validation sets was used to guide determine additional layers. These metrics were also used to determine which network would go through hyperparameter tuning. Hybrid networks NEEDED

__Conclusions & Future Work__
Combining hybrid networks with Keras Tuner ultimately did create a more robust, generalizable network. The best network had the following structure: NEDED. A hybrid network was better able to capture short term patterns
as well as long term trends present within the time series data. Future work could explore NEEDED

[View Sample Code in Google Colab](https://colab.research.google.com/drive/1Omal3X0fSY9rjPrzb3GDtFtpzwWer8hy?usp=sharing)

[View Sample Code in GitHub](/notebooks/sample_rnn.ipynb)

[All Projects](/index.html)
