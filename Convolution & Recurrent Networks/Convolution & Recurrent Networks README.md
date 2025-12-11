# Convolution and Recurrent Networks

This project focused on implementing and evaluating multiple neural network architectures using TensorFlow and Keras. The objective was to construct models that satisfied strict structural and behavioral requirements defined through automated tests. All evaluations were performed through the provided `test_nn.py` script, which remained unmodified throughout the process.

---

## Overview

The project implemented four core model builders:

* A recurrent neural network for a synthetic toy sequence problem.
* A convolutional neural network for MNIST image classification.
* A recurrent neural network for YouTube comment sentiment classification.
* A convolutional neural network for the same YouTube comment task.

The tests validated model architecture constraints, correct output activations, appropriate loss functions, and model performance thresholds.

---

## Final Test Results

All models met the required performance criteria.

* Toy RNN reached 1.5 RMSE
* CNN for MNIST reached 93.0 percent accuracy
* RNN for YouTube comments reached 87.3 percent accuracy
* CNN for YouTube comments reached 84.9 percent accuracy

These results confirmed that each model was structured correctly and trained to the expected performance level.

---

## Implemented Models

### RNN for Toy Problem

This model processed a sequence-to-sequence regression task.
The test required:

* A recurrent layer such as LSTM or GRU
* No convolutional layers
* Linear output activation
* A regression-appropriate loss containing the substring "mean"

The final model passed with an RMSE of 1.5.

---

### CNN for MNIST Classification

This model processed 28x28 grayscale images for multi-class classification.
Required characteristics:

* Convolutional layers
* A softmax output layer
* Categorical cross-entropy loss

The model reached 93.0 percent accuracy on the test sample.

---

### RNN for YouTube Comment Classification

This model processed tokenized text sequences.
Structural requirements included:

* At least one recurrent layer
* No convolutional layers
* A final sigmoid or softmax activation based on the label format

The model achieved 87.3 percent accuracy.

---

### CNN for YouTube Comment Classification

This model applied convolution over token embeddings for text classification.
Expected properties:

* At least one Conv1D layer
* No recurrent layers
* A classification-appropriate output layer and loss

The model reached 84.9 percent accuracy.

---

## Technologies Used

* Python 3.11
* TensorFlow and Keras
* NumPy
* PyTest for automated validation
* Google Colab environment (Linux-based)

---

## Key Concepts Demonstrated

* Construction of RNN, GRU, LSTM, and CNN architectures
* Handling different data modalities: sequences and images
* Using Keras functional and sequential APIs
* Managing loss functions, optimizers, and training configurations
* Adhering to strict model constraints verified through automated tests

---

## Summary

The project successfully produced working neural network models that conformed to structural expectations and met target performance metrics. All tests were passed without modifying the evaluation script, confirming correct design, configuration, and model behavior across all tasks.
