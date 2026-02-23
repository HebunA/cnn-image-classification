#  Weather Image Classification using Convolutional Neural Networks (CNN)

---

##  Project Objective

This project aims to classify images using a **Convolutional Neural Network (CNN)** architecture. The training process, validation results, and test performance are thoroughly analyzed to evaluate the effectiveness of the model on a multi-class image classification task.

##  Dataset

The dataset used in this project is publicly available on Kaggle:

[5-Class Weather Status Image Classification - Kaggle](https://www.kaggle.com/datasets/ammaralfaifi/5class-weather-status-image-classification)

It consists of weather condition images categorized into multiple classes and is suitable for supervised deep learning tasks.

---

##  Project Structure & Model Details

### Data Loading & Preprocessing

* Images are loaded from `train/`, `val/`, and `test` directories.
* Pixel values are normalized to the **[0, 1] range** using `ImageDataGenerator`.
* Input image size (`target_size`) is set to **(64, 64)**.
* The dataset is prepared for multi-class classification.

### Model Architecture (Sequential CNN)

The model is built using a Sequential CNN architecture consisting of:

* `Conv2D` + `MaxPooling2D` layers for feature extraction
* `Flatten` layer for vectorization
* Fully connected `Dense` layers for classification
* `Dropout` layer to reduce overfitting
* `Softmax` activation function in the output layer for multi-class prediction

### Training Configuration

* **Epochs:** 100
* **Batch Size:** 128
* **Loss Function:** `categorical_crossentropy`
* **Optimizer:** Adam (`learning_rate = 0.0005`)
* **Evaluation Metric:** Accuracy

---

##  Performance Evaluation

After 100 epochs of training, the model achieved the following results:

* **Training Accuracy:** 86%
* **Validation Accuracy:** 85%
* **Test Accuracy:** 86%

These results indicate that the model generalizes well without significant overfitting.

---

##  Model Explainability – Grad-CAM

To improve interpretability, the **Grad-CAM (Gradient-weighted Class Activation Mapping)** technique is applied.
Grad-CAM visualizes which regions of an image the model focuses on during prediction by generating a heatmap.

 Example:

![Grad-CAM Visualization](gorseller/grad_cam_ornek.png)

In the visualization, **red regions** represent the areas that most strongly influence the model’s classification decision.

---

##  Usage

1. Install the required dependencies:

```bash
pip install tensorflow numpy pandas matplotlib scikit-learn
```

2. Organize your dataset into the following directory structure:

```
train/
val/
test/
```

(each folder should contain class-labeled subfolders)

3. Run the Jupyter Notebook:

* Use `model.fit()` for training
* Use `model.evaluate()` for evaluation
* Use `model.predict()` for inference

---

##  Future Improvements

* Apply **Data Augmentation** (rotation, zoom, flip, etc.) to increase dataset diversity
* Use **Transfer Learning** (e.g., VGG16, ResNet50) for higher accuracy
* Perform **Hyperparameter Optimization** (learning rate, batch size, architecture tuning)

---

##  License

This project is developed for educational and research purposes.
You can also refer to the related Kaggle notebook:

👉 https://www.kaggle.com/code/hebunartut/cnn-modeli
