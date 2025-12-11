# Back Propagation

## Overview

This project implements a simple fully connected feed-forward neural network with sigmoid activations. The model supports forward propagation, binary prediction, gradient computation via backpropagation, and weight updates via gradient descent. All logic is contained in a single file: `nn.py`.

## Objectives

* Implement feed-forward prediction.
* Implement gradient computation using back-propagation.
* Train the network using gradient descent.
* Ensure all functionality passes the provided tests in `test_nn.py`.

## File Structure

* `nn.py` — core implementation.
* `nn.ipynb` — notebook version used for development.
* `nn.html` — exported HTML for grading.
* `test_nn.py` — provided test script (not modified).

## Requirements

* Python 3.8+
* numpy
* scipy
* pytest

Install dependencies:

```bash
pip install numpy scipy pytest
```

## Implementation Summary

### 1. Network Initialization

`SimpleNetwork` accepts a sequence of weight matrices. Layers are determined by the shapes of these matrices.

### 2. Forward Propagation

`predict()` computes:

```
a(l+1) = sigmoid(a(l) × W(l))
```

where activation uses `scipy.special.expit`.

### 3. Binary Output Prediction

`predict_zero_one()` applies a 0.5 threshold to forward-propagated outputs.

### 4. Back-Propagation

`gradients()` performs:

* Forward pass storing activations.
* Backward pass computing:

  * Output error: `h_L − y`
  * Layer deltas: `delta = error ⊙ sigmoid'(z)`
  * Gradients: `(h(l)^T × delta) / N`
  * Error propagation: `delta × W(l)^T`

Gradients are returned in a list aligned with weight ordering.

### 5. Training

`train()` repeatedly:

```
grads = self.gradients(...)
weights = weights − lr × grads
```

The update runs for `iterations` steps.

## Running Tests

Execute in the directory containing `test_nn.py`:

```bash
pytest
```

Success state:

```
5 passed
```

## Workflow

1. Copy template into a new notebook named `nn.ipynb`.
2. Fill in all functions as required.
3. Export:

   * `nn.ipynb`
   * `nn.html`
   * `nn.py`
4. Use `nn.py` for testing via pytest.

## Expected Behavior

* Forward propagation returns values strictly between 0 and 1.
* Zero-one predictions return integer 0/1 outputs.
* Gradients match analytic expectations and pass numerical tests.
* Training decreases prediction error on provided samples.

## Notes

* Only sigmoid activations are used.
* Matrix operations rely on `numpy.dot`.
* No extra files are added.
