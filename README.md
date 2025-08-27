# EEG-Based Schizophrenia Detection Using Image Encoding and Genetic Algorithm Machine Learning Models

OVERVIEW 

Schizophrenia is a chronic and severe mental disorder that affects how a person thinks, feels, and behaves. It often leads to hallucinations, delusions, disorganized speech, and cognitive difficulties. According to the WHO, schizophrenia affects approximately 24 million people worldwide, and early diagnosis plays a crucial role in effective treatment and improving quality of life.
Traditionally, diagnosis relies on clinical interviews, behavioral assessments, and neuropsychological tests, which can sometimes be subjective and time-consuming. With advancements in Artificial Intelligence (AI) and Machine Learning (ML), analyzing EEG (Electroencephalogram) signals offers an objective and non-invasive approach to support clinicians in early detection.
This project explores the use of EEG signals, image encoding techniques, and machine learning models to build an automated system that can distinguish between healthy individuals and schizophrenia patients.

PROJECT GOAL

The main goal of this project is to build a machine learning pipeline that:
-> Processes raw EEG signals.
-> Converts signals into spectrogram images.
-> Extracts deep features using pre-trained CNNs.
-> Applies optimization using a Genetic Algorithm.
-> Classifies patients vs. healthy individuals using ML classifiers.
This contributes to the development of AI-driven clinical decision support systems for early, reliable, and cost-effective schizophrenia detection.

DATASET DESCRIPTION

Subjects: 84 total → 39 Healthy Controls (HC), 45 Schizophrenic Patients (SZ).
EEG Recording:
-> 16 scalp electrodes.
-> 128 Hz sampling rate.
-> 1-minute duration per subject.
Data Size: 7680 samples per electrode per subject.
Processed Dataset: 12,096 spectrogram images (144 per subject).

METHODOLOGY

1. Signal Preprocessing
   
   Applied 2nd-order Butterworth bandpass filter (2–45 Hz).
   Removed muscle noise,eye blinks (<2 Hz) & high-frequency artifacts (>45 Hz).
   Preserved physiological EEG rhythms: theta, alpha, beta, gamma, delta.
   Cleaned 1D EEG signals were transformed using Fast Continuous Wavelet Transform (FCWT) obtained from GitHub for faster computation chosen over traditional CWT.
   
2. Image Encoding
 
   FCWT spectrograms converted each filtered EEG signal into 2D RGB images.
   Each subject contributed 144 images (16 channels × 9 segments due to sliding window of 20 sec with 15 sec overlap), totalling 12,096 spectral images.
   
3. Feature Engineering (Deep Feature Extraction)

   Used pretrained CNNs: EfficientNet-B3 and DenseNet-169 via transfer learning.
   Each FCWT image was passed through both networks to extract high-level spatial-frequency features.
   Resulting vectors were concatenated giving a 3200-dimensional hybrid feature descriptor.
   
4. Feature Engineering (Feature Selection)

   Genetic Algorithm (GA) optimized features.
   Reduced redundancy & noise.

5. Classification

   Training/Test Split -
   Stratified ~80/20 split at subject level to avoid data leakage.
   Training: 9,360 images (4,464 HC & 4,896 SZ → 31 HC / 34 SZ subjects).
   Testing: 2,736 images (1152 HC & 1,584 SZ → 8 HC / 11 SZ subjects).

6. Models

   Applied KNN, RandomForest, XGBoost and received better results in XGBoost algorithm.

RESULTS

Implemented a pipeline combining EEG → Image Encoding (FCWT) → CNN Feature Extraction → GA Optimization → ML Classification Models.
The system was able to differentiate between schizophrenia patients and healthy controls, but the results were not highly accurate due to dataset limitations and model overfitting.
The project primarily demonstrates the feasibility and workflow for EEG-based schizophrenia detection using ML/DL techniques.
More advanced classifiers, larger datasets, and regularization techniques are required to improve performance.

CONTRIBUTIONS

Contributions are welcome! 
If you’d like to improve this project or add new features, feel free to fork the repository and submit a pull request.
I’ll be truly obliged for any contributions that help take this work further.
