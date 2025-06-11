# 🧪 Random Forest
Random Forest is a type of supervised learning and an ensemble method that builds many decision trees. It aggregates predictions of each tree to make a final decision. In **random forest classifier**, each tree votes for a class label, and the final decision is made by the majority vote. In **random forest regressor**, the prediction is made with the averaged value across all trees.

Individual decision trees are weak learners, and random forest makes them stronger by combining their predictions. Therefore, the variance is reduced and the results are generalized better with random forest.

---

## 🧠 Gradient Boosting



---

## 📊 Dataset

- **Dataset:** [MNIST Handwritten Digits](http://yann.lecun.com/exdb/mnist/)
- **Description:** 60,000 training images and 10,000 test images of handwritten digits (0–9), each image is 28x28 pixels in grayscale.

---

## 🧪 Experiments

The following model configurations were tested:

- **Hidden units:** 1, 2, 8, 16, 32, 64, 128, 256
- **Feature Selection:** PCA, Random Forest Classifier
- **Activation functions:** ReLU, Softmax 
- **Optimizers:** root mean squared propagation (rmsprop)
- **Batch sizes:** 32
- **Epochs:** Up to 50 (with early stopping)

Each configuration was evaluated based on validation accuracy and test accuracy.

---

## 🧰 Tools & Libraries

- Python 3.13.3
- TensorFlow / Keras  
- NumPy, Matplotlib for visualization  

---

## 📈 Results Summary

- Best performance achieved with:
  - **256 hidden neurons**
  - **ReLU activation**
  - **rmsprop optimizer**
  - **Batch size of 32**
  - **Full 784 Features**

> Final test accuracy: **0.9699**

Visualizations include training/validation accuracy plots and confusion matrix of final predictions.

---

---

## 🚀 How to Run

You can run the notebook directly in **[Google Colab](https://colab.research.google.com/)** or locally:

1. Clone the repo  
   `git clone https://github.com/yourusername/MNST-Classification.git`

2. Open `DNN_MNST_Classification.ipynb` in Jupyter or Colab

3. Run all cells to train the model

---

## 📌 Learnings

- Importance of tuning hidden units and optimizers for faster convergence
- Impact of activation functions on performance and training stability
- How batch size affects noise vs. convergence speed

---

## 🧠 Author

**Minjeoung Neev**  
Graduate student passionate about deep learning & data science  
📧 laminjon@gmail.com

---

## 📜 License

This project is under the MIT License. Feel free to fork and experiment!

