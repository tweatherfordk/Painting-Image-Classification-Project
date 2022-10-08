# Art Style Image Classification Project

![Painting Example](https://user-images.githubusercontent.com/110851861/194657326-a9be4d6a-d7f5-42e0-bb7c-98ef1f63bcbc.jpg)

## Overview

This project aims to create an image classification model without using a neural network. The data contains photopgrahs of two different art styles, Paintings and Iconography, which is a distinctive style of religious art found especially within Eastern Orthodox Christianity.Starting from a folder of photos, the data was created by converting each photograph as a multidimensional numpy array, which were used to create 13 custom features. Once these features were created, multiple classification models were evaluated on test data, with the best model being a Tuned Random Forest. This model yield accruacy, recall, precision, and F1 scores equal to 0.92 with low instance of both type 1 and type 2 errors.

## Business Understanding

Need a thorough way to sift through thousands of art pieces and sort them based on style? The human eye can naturally detect patterns and draw conclusions to differentiate between types of art. While the human eye is quite adept in this task, for a large set of images, it may become impractical to manually sort through them all. This model does exactly that, but automates the process by translating an image's visual representation (the displayed photo) to a numeric representation (an array of its pixels).

This model, while trained on art styles, could be applied to any supervised learning image dataset. Using features derived straight from each image's pixel values themselves over Red, Green, and Blue color channels, this project can accurately classify different art styles. Given a different collection of iamge, it could easily be retrained to perform any number of different image classificaion tasks.

## Data Understanding and Analysis
![Iconography_example](https://user-images.githubusercontent.com/110851861/194676952-78114393-aa45-49f7-9377-c05847ef59fb.png)

Close to 4500 images were used to construct the model, with the number of Painting and Iconogrpaphy types creating a balanced dataset. After each image was converted to a 3 dimensional numpy array, each image was scaled and split into it's three respective color channels as well as it's original form. Certain features, like HOG and SIFT, required the image to be converted into grayscale. After this preprocessing was constructed, 13 features were contructed and collected in a dataframe to be used for modeling.

Histogram of Oriented Gradients (HOG) is a feature descriptor commonly used in object detection. Effectively it computes the gradient of the image. This model used the X-direction derivatives and the Y-direction dervatives of the image separately instead of using the combined gradient metric. Once these derivatives were calculated, the mean and variance was calculated for each image.

Directional Derivates of Example Image:
![Directional_HOG](https://user-images.githubusercontent.com/110851861/194676976-51f958ea-ec12-458a-8ca9-d054ebed388c.png)

Scale Invariant Feature Transform (SIFT) is used in image processing for feature detection and matching. The algorithm effectively selects the features it detetcs as most important, the keypoints of an image. Similarly the HOG features, mean and variance were calculated for each image.

SIFT Keypoints on Example Image:
![SIFT](https://user-images.githubusercontent.com/110851861/194677050-792bd033-10cb-431d-a91b-0fea083698b1.png)

Entropy (an information theory metric that measures the impurity or uncertainty in a group of observations) was calculated on the full color image, while Kurtosis (the sharpness of the peak of a frequency-distribution curve) and Skew (distortion or asymmetry that deviates from symmetrical normal distribution, for each image's array of pixels) were calculated for each of the image's 3 color channels.

## Model Conclusions:

Example Decision Tree within Final Model:
![rf_individualtree](https://user-images.githubusercontent.com/110851861/194677042-bfc9c641-ee68-48d5-91d6-9b4fabd9dc6a.png)

A Random Forest model with a maximum depth of 24 nodes and 40 estimator trees yielded the best model, which produced accuracy, precision, recall, and F1 scores of 0.92. Effectively, the model can detect whether the image is either in the Iconogrpahy or Painting style 92% of the time, which improves along the baseline Logisitic Regression model which classified correctly 81% of the time. The most important features for prediction were Red Channel Skew, Y HOG Variance, X HOG Variance, Green Channel Skew, and Red Channel Kurtosis.

## Future Work
 
One further step to improve the model would be to calculate metrics such as HOG or entropy not on the image as a whole, but on subdivisions of the image itself. For example, a mask could be used to segment each image into quandrants, and then the features could be calculated on each subdivison of the image.
This zooming in on specific spatial portions of the data would likely improve the model's ability to predict the correct art style as their are noticeable visual trends that are generally specific to a location in the photo (e.g. a halo around the central figure is often present in the top quadrants of an Iconography example. Additionally, more art styles could be introduced as classifiers, such as Sculpture, so that the model can be applied to a broader range of images.
