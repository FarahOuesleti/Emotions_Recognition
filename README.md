# 5_Emotions_Recognition

## I. General Presentation & Objectives:
Our aim is to have a model that predicts human emotions based on facial expressions accurately from the 7 basic emotions. We have chosen a unique approach to accomplish this purpose.

Our base input dataset is a set of low quality images in grayscale featuring the 7 emotions. The data is labeled. We chose a supervised learning approach.

## II. Project Approach:
Since the data is of relatively low quality, we opted for a Gaussian deblurring effect. 
Research papers show that the following color spaces help the models detect facial expressions features more distinctly : 
- YES color space
- YCbCr color space

Hence we have performed data transformations of our initial grayscale dataset to these two color spaces, obtaining two additional datasets each for one color space.
In addition to that, we have applied a set of filters for Edge detection, and ended up with a 3rd dataset of edge filtered images with distinct edges.

Followed by that, we have implemented a CNN model, that we finetuned on the original grayscale datato reach optimal performance. After that, we have tested the model's performance on the three other transformed datasets ( YES dataset, YCbCr dataset, Edge detection dataset) and evaluated the model's performance for each of them to determine which helps the model detect facial expressions more accurately.

After performing those tests on the CNN implemented model, we decided to make use of transfer learning to end uo with a model that predicts best results for all emotions.

For that, a scientific research models' architectures review, frow our choices of the following 3 models to test : 
- ResNet
- VGG
- InceptionV3 (was attempted)

We have tested each of these models separately on our datasets, determined that some of them perform better for certain emotions, where some other models fail, and excel at other emotions. In other words, we have found that our CNN model, and some of the pretrained models are complementary, therefore, we decided to concatenate them to end with a model that has optimal accuracy for all 7 emotions.

Further choices explanations of the filters choices, color spaces, models, are all present in the presentation (pages 14 to 23 & Page 30) and in the Data_PreProcessing_Emotions_Recognition.

## III. Results and Interpretations:
### 1. Results of comparison of color spaces Datasets:
#### a. Grayscale:
  - Gives good results for fear and very good results for happy
  - Tends to have high fear recall, many emotions are mistakenly classified as fear.

#### b. YcrCb:
  - Gives good results for neutral
  - Tends to mistake some neutral for sad or happy.
    
#### c. YES:
  - Mistakes Angry for Happy
  - Gives good results for angry dataset overall
  
==> For the same base model, different image treatements with color shift makes te model better at identifying a certain emotion, therefore, including the whole modified dataset as input even to a single model, should give a complete result with good accuracy.

### 2. Results of comparison of Models (separately):
After finetuning, VGG performs better than ResNet, especially on 'Surprise' emotion. (Further details can be found in the notebooks)

The comparison of several finetuned concatenated models, resulted in the choice of the following concatenation: 
**Base finetuned CNN model + Vgg finetuned**


## IV. Further Details:
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


