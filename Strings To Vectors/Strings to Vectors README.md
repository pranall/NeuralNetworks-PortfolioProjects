# String-to-Vectors (STV); an Index Class Implementation

This repository contains the implementation for the **String-to-Vectors (STV)** assignment. The project focuses on constructing a robust mapping system between arbitrary vocabulary items and numerical representations such as index vectors, binary vectors, index matrices, and binary matrices. This work is guided by automated testing similar to real-world ML workflow validation.

## Overview

The goal of this project is to implement an `Index` class that provides:

* **Bidirectional mapping** between vocabulary objects and integer indices.
* **Token-to-index encoding** with out-of-vocabulary handling.
* **Binary vector and matrix representations** of token sequences.
* **Index vector and matrix generation** with padding based on a configurable starting index.

This implementation is validated using an industry-style test suite (`test_nn.py`), ensuring correctness across edge cases such as:

* Duplicates in vocabulary
* Out-of-vocabulary symbols
* Ragged sequences
* Start-index shifting
* Large Unicode vocabularies

---

## Features Implemented

### 1. **Vocabulary Normalization**

* Removes duplicate vocabulary items while preserving order.
* Assigns indices starting from a configurable `start` value.

### 2. **Object-to-Index Encoding**

* Converts sequences of objects into index arrays.
* Unrecognized tokens are encoded as `start - 1` (OOV value), matching the test suite.

### 3. **Index-to-Object Decoding**

* Converts index arrays back into object sequences.
* Ignores OOV indices during decoding.

### 4. **Binary Vector Representation**

* One-hot style binary representation of object presence.
* Supports `start` shifting by expanding the vector length accordingly.

### 5. **Binary Matrix Representation**

* Produces a binary vector for every sequence in a batch.

### 6. **Index Matrix Representation**

* Handles ragged sequences by padding with OOV values.
* Ensures proper alignment with start-offset indexing.

---

## Instructions

The implementation follows the exact assignment guidelines:

1. Code written inside `stv_nn.ipynb`.
2. Exported as `.ipynb`, `.html`, and `.py` (`stv_nn.py`).
3. `test_nn.py` executed in a separate notebook without modification.
4. All functionality validated using the provided test suite.
5. Errors encountered during testing (e.g., JSON upload errors, OOV mismatches) were resolved by refining implementation.

---

## Troubleshooting Notes

During development, several common issues were resolved:

### **1. Invalid JSON Upload Errors**

Occurs when uploading a `.py` file generated incorrectly from a notebook.
Solved by properly exporting the `.py` file directly from `File → Download .py` in Colab.

### **2. Out-of-Bounds Index Errors**

Happened when `start` shifting wasn't accounted for.
Fixed by computing binary vector length based on `max(self.obj_to_idx.values())`.

### **3. OOV Handling Mismatches**

Tests expect OOV value = `start - 1`.
Implementation adjusted accordingly.

---

## Testing

All functionality validated using the provided `test_nn.py` file containing 8 unit tests:

* Vocabulary deduplication
* Bi-directional mapping
* Binary encoding/decoding
* Ragged input handling
* OOV behavior
* Unicode coverage

To run:

```bash
pytest test_nn.py
```

---


## Conclusion

This project demonstrates the construction of a vocabulary-indexing system validated using automated unit tests.
The final implementation aligns fully with the specifications and handles all required edge cases.

