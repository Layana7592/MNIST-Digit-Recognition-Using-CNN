# MNIST Digit Recognition Using CNN

A handwritten digit recognition project using a Convolutional Neural Network (CNN) built with TensorFlow/Keras and the MNIST dataset. The notebooks run in Google Colab and demonstrate training, evaluating, saving, and reloading a trained model using Google Drive.

## Project Overview

The goal is to classify grayscale images of handwritten digits into one of 10 classes (`0`–`9`). Each MNIST image is 28 × 28 pixels.

This repository contains two parts:

1. **CNN training and model saving** – loads and preprocesses MNIST, builds and trains a CNN for 5 epochs, evaluates it, and saves the trained model as `mnist_model.keras` in Google Drive.
2. **Loading and prediction in a new session** – mounts Google Drive, loads the saved model without training it again, and predicts a digit from the MNIST test set.

## Notebooks

| Notebook | Purpose |
|---|---|
| `MNIST_Digit_Recognition_CNN_Training_and_Model_Saving.ipynb` | Train and evaluate the CNN, then save the model to Google Drive. |
| `New_Session_MNIST_Digit_Recognition_Using_CNN.ipynb` | Load the saved model in a separate Colab session and make a prediction. |

Open the `.ipynb` files in this repository with **Google Colab** using GitHub's **Open in Colab** option, or download them and upload them to Colab.

## Dataset

The project uses the MNIST handwritten digit dataset provided by `tf.keras.datasets.mnist`. TensorFlow downloads the dataset when the notebook runs.

- Training images and labels: `x_train`, `y_train`
- Test images and labels: `x_test`, `y_test`
- Image dimensions: `28 × 28` pixels
- Number of classes: `10` (digits 0 through 9)

## Model Architecture

The notebook defines this sequential CNN:

1. Input layer: `(28, 28, 1)`
2. `Conv2D`: 32 filters, 3 × 3 kernel, ReLU activation
3. `MaxPooling2D`: 2 × 2 pool
4. `Flatten`
5. `Dense`: 128 units, ReLU activation
6. Output `Dense`: 10 units, softmax activation

The model is compiled with the Adam optimizer, sparse categorical cross-entropy loss, and accuracy as a metric. It is trained for 5 epochs.

## Workflow

### 1. Train and save the model

1. Open the training notebook in Google Colab.
2. Run the cells in order.
3. Authorize the Google Drive mount when prompted.
4. The notebook loads MNIST, scales pixel values to the range 0–1, and reshapes the images to `(28, 28, 1)`.
5. It builds and trains the CNN, then evaluates it on the MNIST test data.
6. The trained model is saved to:

   `MyDrive/mnist_model.keras`

### 2. Load the model in a new session

1. Open the second notebook in a new Google Colab session.
2. Make sure you use the same Google account and that `mnist_model.keras` exists in the root of your Google Drive.
3. Run the cells in order and authorize Google Drive access.
4. The notebook loads the saved model with `tf.keras.models.load_model(...)`.
5. It predicts the digit for test image index `700` and displays the predicted digit alongside the actual label.

**Important:** The second notebook loads the saved model; it does not train the model again.

## Technologies Used

- Python
- Google Colab
- TensorFlow / Keras
- NumPy
- Matplotlib
- Google Drive

## Installation / Requirements

The notebooks are designed to run in Google Colab. The training notebook installs TensorFlow. The main Python packages used are:

```bash
pip install tensorflow numpy matplotlib
```

Google Drive access is provided through the Google Colab environment.

## Results

The training notebook prints the test loss and test accuracy after evaluation. The prediction notebook prints the predicted digit and actual label for the selected test image and displays that image.

No fixed accuracy value is stated here because the result should be taken from the output produced when the notebook is run.

## Repository Structure

```text
MNIST-Digit-Recognition-Using-CNN/
├── MNIST_Digit_Recognition_CNN_Training_and_Model_Saving.ipynb
├── New_Session_MNIST_Digit_Recognition_Using_CNN.ipynb
├── README.md
├── .gitignore
└── LICENSE
```

## Notes

- Run the training notebook before running the model-loading notebook.
- Keep `mnist_model.keras` in the root of Google Drive, or update the model path in the loading notebook to match its actual location.
- The training notebook uses `x_test` as `validation_data` and also evaluates on `x_test`. For a more rigorous model-selection workflow, use a separate validation set and reserve the test set for final evaluation.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
