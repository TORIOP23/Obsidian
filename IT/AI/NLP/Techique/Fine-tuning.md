![[fine-tuning.png]]
- While transfer learning involves freezing the pre-trained model’s weights and only training the new layers, fine-tuning takes it a step further by allowing the pre-trained layers to be updated. This additional step is beneficial when the new dataset is large enough and similar to the original dataset on which the pre-trained model was trained.

Fine-tuning involves the following steps:
_**Feature Extraction:**_ Similar to transfer learning, we use the pre-trained model as a feature extractor. We replace the final classification layers with new layers specific to our task and freeze the weights of the pre-trained layers.  
_**Fine-Tuning:**_ In this step, we unfreeze some of the pre-trained layers and allow them to be updated during training. This process enables the model to learn more task-specific features while preserving the general knowledge acquired from the original dataset.

# Reference
https://dev.to/luxacademy/understanding-the-differences-fine-tuning-vs-transfer-learning-370