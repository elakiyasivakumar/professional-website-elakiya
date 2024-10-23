---
title: Data Augmentation methods using Generative-AI
summary: Making more well annotated datasets!
date: 2022-05-24
math: true
authors:
  - admin
  - Dr K Nirmala, SSN Biomedical Engineering
  - Anjana Anand
tags:
  - Gen AI
  - Medical Images
  - Markdown
image:
  filename: GAN-arch.png
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

### Genrative Adversial Network Based augmentation 

Generative adverserial networks consist of 2 AI networks that compete against each other to minimize loss. 

The generative network "looks" at real world examples and generate images which is then passed to the adverserial network which then classifies the image as "fake" or "real". 

The learning is then back-propgated through both networks and the generative network creates better "fake" images. 

![GAN-Example](GAN-arch.png)

We study 2 types of GANs in this project: 

- Deep Convolution GAN (DCGAN)
- Wasserstein GAN (WGAN)

The difference is in the network architechture and the loss function. 

#### DC GAN 

DCGAN is an extension of the original GAN architecture that incorporates convolutional layers for improved image generation.
Key features:
- Uses convolutional and convolutional-transpose layers in the discriminator and generator
- Employs batch normalization in both networks
- Uses ReLU activation in the generator and LeakyReLU in the discriminator
- Eliminates fully connected layers for deeper architectures
- Uses strided convolutions instead of pooling layers
Advantages:
- Improved training stability
- Better quality image generation
- Learns a hierarchy of representations from object parts to scenes
Disadvantages:
- DCGAN model is unable to generalize to the data because the data consists of both skull-neck and lumbar spine sections. Since the image representation of both are different, the model learns and unlearns the pixel distribution.
- This occurs due to instability during training- the generator and discriminator minimize or maintain their performance based on the error provided by the other. This can cause the network to stop learning before the optimal point.
- Furthemore hyperparameters such as batch normalization, dropout, have to be defined after much trial and error.
- The maximum image size created is of size 64, 64-  GPU memory issues for bigger images during training.
- It takes the model 2-3 hrs to train for 200 epochs- and hence is time consuming. 

![DCGAN Output](DCGAN-op.png)

#### WGAN 

WGAN is an alternative to traditional GANs that uses the Wasserstein distance (also known as Earth Mover's distance) as its loss function.
Key features:
- Replaces the discriminator with a critic that estimates the Wasserstein distance
- Uses weight clipping to enforce Lipschitz continuity
- Employs a different loss function based on the Wasserstein distance
Advantages:
- More stable training process
- Meaningful loss metric that correlates with image quality
- Reduces mode collapse
- Less sensitive to architecture choices and hyperparameters

![WGAN Algorithm](wgan-alg.png)
![WGAN Performance](wgan-perf.png)
![WGAN Output](epoch-op.png)



### Analyzing Test Networks performance with WGAN output 

![Network Performance with WGAN Output](op-vn-gan.png)

### Hybrid Augmentation method 

We propose a novel hybrid augmentation technique that involves combination of "best performing" basic augmentation techniques followed by WGAN 

![Case-1 Data Split](case-1.png)
![Case-1 Data Augmentation](case-1-tbl.png)
![Case-1 VGG16 Output](vgg16.png)
![Case-1Inception Net Output](nception.png)


### Conclusion from the Study 

We observe that the best performing basic augmentation techniques combined give better accuracies than combining the worst performing strategies (for Case- 1: best performing techniques combined resulted in an accuracy of ~88% and ~83% for VGG-16 and InceptionNet in comparison to worst performing techniques combined which resulted in ~81% and ~80% accuracy for VGG-16 and InceptionNet respectively). 

After analysing individual augmentation strategies for two more spine abnormalities subsets, the best performing basic augmentation techniques for the VinDr spine dataset are Rotation 45, Rotation 270, and Shearing.

The proposed hybrid augmentation was employed by combining WGAN image generation and the three best performing basic augmentation strategies. The hybrid augmentation strategy allowed for more dataset volume available for deep learning classification, and resulted in accuracies of 98-99% across all three spine abnormalities cases for VGG-16 and InceptionNet classifiers. The hybrid technique performed better than basic augmentation alone or WGAN image generation alone.


