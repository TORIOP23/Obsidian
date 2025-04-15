- Generalization, Overfitting and Underfitting
- Training set, Validation set, and Test set
- **_K_-fold cross-validation**
- Early stopping
### Feature Engineering
- [Binning](https://scikit-learn.org/stable/modules/preprocessing.html#preprocessing-discretization): Grouping data into buckets. For example, you could bin age data into groups such as 0-10, 11-20, 21-30, etc.
- Normalization: [Scaling](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.StandardScaler.html) data to be between 0 and 1 (as neural networks usually work better with normalized data).
- [One-hot encoding](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.OneHotEncoder.html): Converting categorical data into multiple binary columns.
### Loss Functions and Metrics
- For example, a neural network for a classification problem may be trained with the [backpropagation](https://en.wikipedia.org/wiki/Backpropagation) algorithm to minimize the [cross-entropy loss function](https://machinelearningmastery.com/cross-entropy-for-machine-learning/).
- Some [common metrics for classification models](https://en.wikipedia.org/wiki/Evaluation_of_binary_classifiers) are accuracy, precision, recall, and the F1-score (i.e. the harmonic mean of precision and recall). Another common metric is the area under the receiver operating characteristic curve (AUC), which measures the ability of the model to discriminate between positive and negative cases.
- Some [common metrics for regression models](https://machinelearningmastery.com/regression-metrics-for-machine-learning/) are the Mean Squared Error (**MSE**), Root Mean Squared Error (**RMSE**), and Mean Absolute Error (**MAE**).