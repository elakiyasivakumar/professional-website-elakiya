---
title: Data Augmentation methods using Generative-AI
authors:
  - admin
  - Dr K Nirmala, SSN Biomedical Engineering
  - Anjana Anand
tags:
  - Gen AI
  - Medical Images
  - Markdown
image:
  filename: epoch-op.png
---
### Aim

Deep Learning methods require large datasets to overcome overfitting and class generalization problems.
Well-annotated and sufficient datasets are expensive economically and computationally to produce and store - problem is especially aggravated in the biomedical field. 

Our main aim to do this project came from trying to apply segmentation techniques to medical image datasets but realizing we simply did not have enough data to train the models with! 

We decided to then focus on augmentation techniques for medical image datasets! 

![Problems in Dataset](mot1.png)
![Problems in Dataset](mot2.png)

### Dataset - VinDr SpineXR Dataset

- Large-scale annotated medical image dataset for spinal lesion detection and classification from radiographs. 
- Contains 10,466 spine X-ray images from 5,000 studies, each of which is manually annotated with 13 types of abnormalities by an experienced radiologist.
Lesion types: (1) Ankylosis, (2) Disc space narrowing, (3) Enthesophytes, (4) Foraminal stenosis, (5) Fracture, (6) Osteophytes, (7) Sclerotic lesion, (8) Spondylolysthesis, (9) Subchondral sclerosis, (10) Surgical implant, (11) Vertebral collapse, (12) Foreign body, and (13) Other lesions.

We mainly selected the dataset because of the significant class variance and class imbalance. There is about 13 different types of diseases and all the disease-types have only 100-200 images each.

### Test Networks 

We selected popular deep learning networks used in image classification to study their performance with different augmentation techniques. 
      - VGG16: VGG16 is a convolutional neural network architecture developed by researchers at the Visual Geometry Group (VGG) of the University of Oxford. It is renowned for its simplicity and effectiveness in image classification and object recognition tasks. 
      - Inception Net: also known as GoogLeNet, is a groundbreaking convolutional neural network architecture introduced by researchers at Google in 2014. It represented a significant advancement in deep learning for computer vision tasks, particularly in image classification and object recognition.


### Basic Augmentation Techniques 

We implemented the following augmentation techniques using the PIL package: 
- 45° Rotation
- 270° Rotation
- Horizontal Flip
- Vertical Flip
- Cropping - ((2, 5, 500, 1000))
- Zooming (crop - resize (500,500))
- Shearing - 30 radians

![Results of Individual Manual Augmentation](results-aug-1.png)


### Image Quality Metrics 

It's important to define tangible metrics to understand the quality of the data generated so we used popular image quality metrics in Biomedical Engineering for this. 

![Image-Metrics](Quality-Metrics.png)
![Image-Metrics](metrics-op.png)

