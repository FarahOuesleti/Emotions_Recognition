# 5_Emotions_Recognition

This project includes the following phases :
- Pre-processing & Data Augmentation
- Feature extraction
- Classification

The dataset used :    
- In the wild data provided
- Small dataset showcasing micro expressions in high quality : The objective of this addition is not merely having more data to train on, it's mainly to introduce real facial expressions showing micro expressions*1 that would not be visible in the first dataset.

1* *Micro expressions* : Facial expressions that last **less than 0.5s** and are therefore hard to detect. They can serve to distiguish between real emotion and fake or lab made expressions.

#Details :

### - Data Augmentation
- Color shift
  - YCbCr
  - YES
  --> compare separate training results between (YCbCr - YES - original (greyscale))

### - Feature extraction

0. Relevant features (Based on Business understanding) :
  - mouth ratio to face
  - nb of face curves
  - curves around eyes
  - curves around mouth
  - curves around nose
  - upper lip position relative to down lip : size of vertical distance between the two (relative to one lip length)
  - eyebrows pente relative to horizontal axis


1. Edge Detection (for curves)
  - Prewitt
  - Sobel is to consider

2. Filters (Optional part : for optimization)
  - Gabor filter
  - Local Binary Pattern (LBP)



### - Add microexpressions data & perform same pre-processing

The following choices of techniques adopted in this project (Edge detection filters, noise reducers...) are relative to the Business, in other words;
Emotions and facial expressions studies show that :     
- vertical wrinkles around the nose, a small upward tilt of the upper lip, small frowning ==> associated with disgust
- slight upwaard tilt on the sides of the mouth demonstrated with wrinkles + small wrinkles on the exterior sides of the eyes ==> indcator of genuine happiness.
- slight upward tilt on the sides of the mouth demonstrated with wrinkles + various degrees of frowning ==> associated with sadness.
- etc.
