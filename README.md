# 5_Emotions_Recognition

## I. General Presentation & Objectives:
Our aim is to have a model that predicts human emotions based on facial expressions accurately from the 7 basic emotions. We have chosen a unique approach to accomplish this purpose.

Our base input dataset is a set of low quality images in grayscale featuring the 7 emotions. The data is labeled. We chose a supervised learning approach.

## II. Project Approach:
Research papers show that the following color spaces help the models detect facial expressions features more distinctly : 
- YES color space
- YCbCr color space

Hence we have performed data transformations of our initial grayscale dataset to these two color spaces, obtaining two additional datasets each for one color space.
In addition to that, we have applied a set of filter for Edge detection, and ended up with a 3rd dataset of edge filtered images with distinct edges.

Followed by that, we have implemented a CNN model, that we finetuned on the original grayscale datato reach optimal performance. After that, we have tested the model's performance on the three other transformed datasets ( YES dataset, YCbCr dataset, Edge detection dataset) and evaluated the model's performance for each of them to determine which helps the model detect facial expressions more accurately.

After performing those tests on the CNN implemented model, we decided to make use of transfer learning to end uo with a model that predicts best results for all emotions.

For that, a scientific research models' architectures review, frow our choices of the following three models to test : 
- ResNet
- VGG
- j

We have tested each of these models separately on our datasets, determined that some of them perform better for certain emotions, where some other models fail, and excel at other emotions. In other words, we have found that our CNN model, and some of the pretrained models are complementary, therefore, we decided to concatenate them to end with a model that has optimal accuracy for all 7 emotions.

The filters choices, color spaces, models, are all explained in the notebooks featuring our work.

## III. Further Details:
- Feature extraction
Based on the businees understanding:

- Relevant features:
  - Mouth ratio to face
  - Number of face curves
  - Curves around eyes
  - Curves around mouth
  - Curves around nose
  - Upper lip position relative to down lip : size of vertical distance between the two (relative to one lip length)
  - Eyebrows slope relative to horizontal axis

- Emotions and facial expressions studies show that :     
  - Vertical wrinkles around the nose, a small upward tilt of the upper lip, small frowning ==> associated with disgust
  - Slight upwaard tilt on the sides of the mouth demonstrated with wrinkles + small wrinkles on the exterior sides of the eyes ==> indicator of genuine happiness.
  - Slight upward tilt on the sides of the mouth demonstrated with wrinkles + various degrees of frowning ==> associated with sadness.
  - etc.

In order to detect them by the models, amongst the techniques available:

1. Edge Detection (for curves) choices:
  - Prewitt
  - Sobel is to consider

2. Filters choices:
  - Gabor filter
  - Local Binary Pattern (LBP)


