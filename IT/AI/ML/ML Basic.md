- Generalization, Overfitting and Underfitting
- Training set, Validation set, and Test set
- Early stopping
### Data Leakage
- Mô hình biết trước dữ liệu test
- Hoặc train có cả nhãn
### K-fold cross-validation
Ví dụ k = 5
![[cross-validation.png]]
## [[Data preprocess]]
## [[Data Visualization]]
## [[Feature Engineering]]




- Normalization: [Scaling](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.StandardScaler.html) data to be between 0 and 1 (as neural networks usually work better with normalized data).

### Loss Functions and Metrics
- For example, a neural network for a classification problem may be trained with the [backpropagation](https://en.wikipedia.org/wiki/Backpropagation) algorithm to minimize the [cross-entropy loss function](https://machinelearningmastery.com/cross-entropy-for-machine-learning/).
- Some [common metrics for classification models](https://en.wikipedia.org/wiki/Evaluation_of_binary_classifiers) are accuracy, precision, recall, and the F1-score (i.e. the harmonic mean of precision and recall). Another common metric is the area under the receiver operating characteristic curve (AUC), which measures the ability of the model to discriminate between positive and negative cases.
- Some [common metrics for regression models](https://machinelearningmastery.com/regression-metrics-for-machine-learning/) are the Mean Squared Error (**MSE**), Root Mean Squared Error (**RMSE**), and Mean Absolute Error (**MAE**).
## Reduce dimension
- [[SVD]]
- PCA
- UMAP
- t-SNE
- Auto encoder