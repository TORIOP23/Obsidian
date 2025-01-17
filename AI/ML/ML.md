- Chuyển độ phức tạp chương trình sang phức tạp dữ liệu
- Learning takes many forms, depending on the nature of the agent, the component to be improved, and the available feedback
## Supervised learning

- Decision Trees
	- Information gain
- Linear regression
	- Gradient descent
- A linear classifier with a hard threshold—also known as a **perceptron**—can be trained by a simple weight update rule to fit data that are linearly separable. In other cases, the rule fails to converge.
- **Logistic regression** replaces the perceptron’s hard threshold with a soft threshold defined by a logistic function. Gradient descent works well even for noisy data that are not linearly separable.
- **Nonparametric models** use all the data to make each prediction, rather than trying to summarize the data with a few parameters. Examples include **nearest neighbors** and **locally weighted regression**. 
- **Support vector machines** find linear separators with **maximum margin** to improve the generalization performance of the classifier. **Kernel methods** implicitly transform the input data into a high-dimensional space where a linear separator may exist, even if the original data are nonseparable
- Ensemble methods such as **bagging** and **boosting** often perform better than individual methods. In online learning we can aggregate the opinions of experts to come arbitrarily close to the best expert’s performance, even when the distribution of the data are constantly shifting
## Unsupervised learning
## Reinforcement learning

Learning Probabilistic Models
- **Bayesian learning** methods formulate learning as a form of probabilistic inference, using the observations to update a prior distribution over hypotheses. This approach provides a good way to implement Ockham’s razor, but quickly becomes intractable for complex hypothesis spaces
- **Maximum a posteriori** (MAP) learning selects a single most likely hypothesis given the data. The hypothesis prior is still used and the method is often more tractable than full Bayesian learning
- 
Deep Learning
Reinforcement Learning

# Reference
- [[AIMA.pdf]]
- [[book_ML_color.pdf]]
- [machinelearningcoban](https://machinelearningcoban.com/)
