# EfficientNet-Siamese-Network

## Introduction
This project is put forth to implement and evaluate the working of a Siamese Neural Network backed by EfficientNet-B0 on tasks of image similarity. The main aim will be to learn an embedding space in which pictures similar to one another are closer to each other, while those that don't are far away from one another. Used a dataset of images of different people; therefore, this implementation would be relevant to applications such as facial recognition and clustering. Applied several margin values in contrastive loss in order to train the best performance in SNN.

![image](https://github.com/user-attachments/assets/ce686b14-052b-4f98-8683-bd2cbbb2a184)
|:-:|
|How Siamese networks work

## Data Preparation
Filtered a dataset of images consisting of different people and organized them. Each image was labeled according to its filename, and a Pandas Data Frame was created to store the image paths and labels correspondingly. Applied standard transformations so that it can be fed into the model.
A custom dataset class was designed for loading images and their transformations. In this regard, a custom function was utilized in generating pairs for both similar and dissimilar image pairs. These are the keys to training the Siamese Network by Contrastive Loss.
The Siamese Neural Network is constructed from two identical sub-networks, each processing one of the input images and returning an embedding vector. An EfficientNet-B0 will be used as the backbone but modified to have an output size that will return embeddings of a specified size. Finally, the network outputs two embeddings, which are compared using a contrastive loss function.
It measures distances between embeddings, and then updates model weights as a function of those measured distances to bring similar images closer together, but push dissimilar images further apart in the embedding space.

![image](https://github.com/user-attachments/assets/a3d20d5f-1ebf-42cb-b618-e8c38010ccff)
|:-:|
|Siamese Neural Network Architecture

## Hyperparameters and Training
Several important hyperparameters, including embedding dimension, learning rate, and the number of epochs, were configured for model training. The contrastive loss function would be used, while optimization would be controlled using an Adam optimizer. A learning rate scheduler was applied in order to dynamically adjust the learning rate during the training process.
The training losses and validation losses were tracked through every epoch, and model performance evaluation was continuous. Models at the best validation loss were saved for further analysis at the end.

![image](https://github.com/user-attachments/assets/24335a50-61e8-45a5-8aeb-07d437939241)
|:-:|
|Training and Validation Loss

## Evaluation Metrics
Evaluation metrics supplicated in the model included true positive rate and false positive rate at different threshold levels. The receiver operating characteristic curve was drawn to visualize the tradeoff between TPR and FPR.
A utility function was also developed which returned the 10 most similar images to a given query image, demonstrating in practice the applicability of the learned embedding space.

![Screenshot 2024-07-23 165519](https://github.com/user-attachments/assets/403c110d-3c15-44b8-a788-fcfe57107131)
|:-:|
|10 most similar images to a given query image

## Results
In the study, training and validation losses were evaluated while changing the TPR and FPR at varying thresholds. The resulting ROC curve showed how well this model could distinguish between similar and non-similar images.
Results of Training and Evaluation Impact of Margin Values The performance for different margin values was tested. This chosen margin value created the separation criterion between similar and dissimilar pairs in the embedding space. A lower margin tightens the clustering for similar images; a higher margin, on the other hand, improves separation with respect to the dissimilar images. Conclusion It has been shown that contrastive loss works especially well in image similarity tasks with Siamese Neural Networks, particularly against datasets of different people. In this work, EfficientNet-B0 was used as a back-bone model for efficiently extracting features and generating embeddings. Different margin values were explored, underpinning the importance of hyperparameter tuning in metric learning tasks. Overall, the trained model was very precious to applications like face recognition and image retrieval by visual similarity.

