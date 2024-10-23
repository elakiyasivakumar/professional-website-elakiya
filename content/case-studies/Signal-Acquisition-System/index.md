---
title: EEG Signal Acquisition IoT and Event Detection using DL 
summary: IoT signal acquistion system 
date: 2021-10-24
math: true
authors:
  - admin
  - SSN College of Engineering
  - Drexel University 
tags:
  - Signal Acquisition System
  - Biomedical Engineering
  - Markdown
image:
  filename: cover.png
 
---

### Goal 

To Design a Signal Acquisition System with AD620 

1. Designing Filter systems 
![Designing a Mu band aquisition Circuit](design1.png)
![Designing a Mu band aquisition Circuit](design2.png)

### 10-20 Electrode System 

The 10-20 system is an internationally recognized method for placing electrodes on the scalp during EEG exams, sleep studies, and research. It ensures standardized and reproducible results by aligning electrode placement with specific brain regions.
Key Features:
- Standardization: The system uses anatomical landmarks to ensure consistent electrode placement across different subjects and studies.
- Electrode Spacing: The "10" and "20" refer to the percentage distances between electrodes relative to the total front-back or right-left skull measurements.
- Anatomical Landmarks: Measurements are taken from points like the nasion to inion (front-back) and preauricular points (right-left).
- Electrode Labels: Letters represent brain regions (e.g., Fp for frontal pole, F for frontal), while numbers indicate distance from the midline (odd for left hemisphere, even for right)

![Ten Twenty Electrode System](ten-twen.png)

### Circuit Components

D620: 
- Low noise performance: 9 nV/√Hz at 1 kHz, crucial for detecting small biosignals accurately.
- High precision: 40 ppm maximum nonlinearity, ensuring accurate amplification.
- Low power consumption: 1.3 mA max supply current, ideal for portable devices.
- High common-mode rejection ratio (CMRR): 100 dB min at gain = 10, rejecting common-mode interference.
- Adjustable gain: 1 to 10,000 with a single external resistor, providing flexibility for various biosignals.
- Low input bias current: 1.0 nA max, suitable for high-impedance biosignal sources.
Wide power supply range: ±2.3 V to ±18 V, allowing flexible power supply design.


AD822ARMZ
- Dual independent instrumentation amplifiers in a single package
- Adjustable gain from 1 to 10,000 using a single external resistor per channel
- High precision and low noise performance
- Suitable for applications requiring multiple signal conditioning channels
- Efficient for simultaneous amplification and conditioning of multiple inputs
- Ideal for precision measurement and signal conditioning tasks


### Data Cleaning: Using MATLAB ToolKit 
- Artifact removal:
    - EOG (eye movement and blinks)
    - EMG (muscle activity)
    - ECG (heart activity)
- Noise Reduction: Wavelet based deNoising  
- Bad Channel Interpretation 


### Event/Task Identification using Muu Band

Definition: Mu rhythm is an EEG oscillation in the 8-13 Hz range, recorded from electrodes over sensorimotor cortex (typically C3, Cz, C4).
Significance: Mu suppression is often interpreted as an indicator of mirror neuron system (MNS) activity.

Occurrence: Mu suppression is observed during:
- Execution of motor actions
- Observation of actions performed by others
- Motor imagery

Interpretation: 
- Decreased mu power is thought to reflect increased cortical activation in sensorimotor areas.
- Mu suppression occurs before task. 

### Study Set Up 

rest/baseline EEG: monitored during rest or no activity
Event: measured before, during and after event for total of 10s
Repeated for 10 different tasks for 8 subjects  


### EEG Data Analysis 

Step 1: Clean and process data in 8s bits using [MATLAB EEGLAB](https://www.mathworks.com/matlabcentral/fileexchange/56415-eeglab)
Step 2: Using [PyWavelets](https://pywavelets.readthedocs.io/en/latest/) to get wavelet transform of time variant EEG signals
Step 4: Prep Data for Deep Learning - Dataset is divided into training and test 
Consists of patients - signal - meta data includes baseline Mu power band 

Step 3: Use a sing 4 Layer CNN 1D to perform Binomial classification of the data into rest and action using the wavelet transformed input 
Step 4: Analyze results 

Output: checkpoint of trained signal, performance of the model 

Kaggle Notebook for sample 1D CNN: [https://www.kaggle.com/elakiyasivakumar/cnn1d](https://www.kaggle.com/elakiyasivakumar/cnn1d)

I am not able to publish code/dataset here due to the sensitive nature of the project! 

### IoT Application using AWS 

Using AWS IoT for data storage, data processing and understanding analytics. 
1. Remote data access: IoT enables real-time transmission of EEG data to healthcare professionals, allowing for remote monitoring and analysis. This is particularly valuable for continuous monitoring of patients outside of clinical settings.
2. Cloud-based data storage: IoT facilitates secure storage of large volumes of EEG data in the cloud. This allows for long-term data retention, easy access from multiple locations, and improved data backup and recovery.
3. Advanced analytics:Cloud-based storage enables the application of advanced analytics tools, including machine learning algorithms, to large datasets. This can help in identifying patterns, predicting outcomes, and personalizing treatment plans.
5. Connected medical device:The IoT-enabled EEG system becomes part of a larger ecosystem of connected medical devices, potentially integrating with other health monitoring systems for a more comprehensive patient   overview.
6. Improved patient care:
Real-time monitoring and data-driven insights can lead to faster interventions, more accurate diagnoses, and personalized treatment strategies, ultimately improving patient outcomes.
7. Enhanced research capabilities: The ability to collect and analyze large volumes of EEG data from diverse populations can accelerate neurological research and the development of new treatments.





