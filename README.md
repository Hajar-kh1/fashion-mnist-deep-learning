# Fashion-MNIST Deep Learning Classification

This project develops and evaluates a deep neural network using TensorFlow and Keras to classify Fashion-MNIST images into ten clothing categories.

## Project Objective

The objective is to achieve at least 88% test accuracy while controlling overfitting. A baseline model and three controlled experiments were implemented and compared.

## Dataset

The Fashion-MNIST dataset contains:

- 55,000 training images
- 5,000 validation images
- 10,000 test images
- 10 clothing categories
- 28 × 28 grayscale images

Pixel values were normalized to the range `[0, 1]`. The official test set was isolated until the final evaluation.

## Models and Experiments

### Baseline

- One hidden Dense layer with 128 ReLU units
- Adam optimizer
- Learning rate: `0.001`
- Parameters: `101,770`

### Experiment 1: Architecture Capacity

- Three hidden Dense layers: 256, 128, and 64 units
- ReLU activations
- Parameters: `242,762`

### Experiment 2: Dropout Regularization

- Same architecture as Experiment 1
- Dropout rate of `0.1` after each hidden layer
- Parameters: `242,762`

### Experiment 3: Learning Rate

- Same regularized architecture as Experiment 2
- Adam learning rate reduced from `0.001` to `0.0005`
- Selected as the final model

## Model Comparison

| Model | Parameters | Validation Loss | Validation Accuracy | Generalization Gap |
|---|---:|---:|---:|---:|
| Baseline | 101,770 | 0.2994 | 89.46% | 1.84% |
| Experiment 1 | 242,762 | 0.2908 | 89.54% | 1.95% |
| Experiment 2 | 242,762 | 0.2883 | 89.76% | -0.04% |
| Experiment 3 | 242,762 | 0.2716 | 90.02% | 0.29% |

Experiment 3 was selected because it achieved the highest validation accuracy and the lowest validation loss while maintaining a small generalization gap.

## Final Test Results

The selected model achieved:

- Test accuracy: **88.68%**
- Macro precision: **88.73%**
- Macro recall: **88.68%**
- Macro F1-score: **88.69%**
- Test loss: **0.3220**

The final accuracy exceeds the required target of 88%.

## Error Analysis

Shirt was the most difficult class, with an F1-score of `0.7067`. The primary errors occurred among visually similar upper-body garments, including:

- Shirt
- T-shirt/top
- Pullover
- Coat

These classes have similar silhouettes and limited fine detail in the 28 × 28 grayscale images.


## Running the Project

1. Open `DL_Project.ipynb` in Google Colab or Jupyter Notebook.
2. Install the required packages if necessary.
3. Run the notebook cells in order.
4. The Fashion-MNIST dataset will be downloaded automatically by TensorFlow.

## Requirements

```text
tensorflow
numpy
pandas
matplotlib
scikit-learn
pydot
```
