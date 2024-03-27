# Image Caption Generator

## Introduction

This project aims to create an image caption generator that can provide a concise, one-phrase description of an image, describing the objects within and the context of their existence. Such a tool has numerous applications, notably aiding people with vision impairments by offering descriptions of images and facilitating multilingual communication by describing objects in different languages.

## Dataset

The model was trained on the Flickr8k dataset, which includes 8091 images accompanied by five captions each. To prepare this data for training, captions were first cleaned of punctuation and tokenized. Words occurring fewer than five times were ignored to simplify the model's vocabulary. A word-to-token dictionary was created for numerical representation, and a special class was used for translating between tokens and words. Additionally, captions were padded to equal length for batch processing.

## Model Architecture and Training

The model follows a sequence-to-sequence architecture, featuring an encoder-decoder design. The encoder employs a pretrained ResNext model from PyTorch, with its final layer adapted for the project's needs. The decoder comprises an embedding layer, an LSTM block for handling sequential data, a fully connected layer, and a dropout layer for regularization during training.

Training was conducted over 50 epochs with a batch size of 200, using the Adam optimizer and Cross-Entropy Loss function. The learning rate was set to 5e-5. Model checkpoints were saved after each epoch to track progress and facilitate model evaluation.

## Results

The trained model demonstrates strong performance in identifying images of dogs, with reasonable accuracy for images of people but struggles with vehicles and buildings. This variance in performance is attributed to the dataset's composition, highlighting the importance of diverse training data.

## Conclusion and Future Work

While effective for certain types of images, the model's performance can be enhanced by training on a more extensive and varied dataset. Incorporating attention mechanisms could also improve accuracy by allowing the model to focus on specific subjects within an image.
