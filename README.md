# Art Style Image Classification Project

![Painting Example](https://user-images.githubusercontent.com/110851861/194657326-a9be4d6a-d7f5-42e0-bb7c-98ef1f63bcbc.jpg)

## Overview

The goal of this project was to create an image classification model without using a neural network. The data contains photopgrahs of two different art styles, Paintings and Iconography, which is a distinctive style of religious art found especially within Eastern Orthodox Christianity.Starting from a folder of photos, the data was created by converting each photograph as a multidimensional numpy array, which were used to create 13 custom features. Once these features were created, multiple classification models were evaluated on test data, with the best model being a Tuned Random Forest. This model yield accruacy, recall, precision, and F1 scores equal to 0.92 with low instance of both type 1 and type 2 errors.

