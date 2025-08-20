# Detecting Cardiac Anomalies from Echocardiogram Videos

## Overview
This project implements signal processing and machine learning methods to detect structural and functional heart anomalies from echocardiogram (echo) videos.  
It combines frequency-domain analysis, spatial coherence assessment, and clustering techniques to identify abnormalities such as:
- Tachycardia & Bradycardia (abnormal heart rates)
- Cardiomyopathy (irregular or weak contractions)
- Valve Disease (spectral murmurs, turbulence)
- Abnormal Wall Motion (asynchronous or dyskinetic motion)

The system leverages Short-Time Fourier Transform (STFT), Power Spectral Density (PSD), phase coherence, and clustering to provide interpretable clinical insights.  

---

## Motivation
Cardiovascular diseases are the leading cause of death worldwide (≈17.9M deaths annually, WHO). Many structural and rhythm abnormalities progress silently and are only diagnosed after severe damage.  
This project aims to:  
- Detect anomalies earlier  
- Support clinicians with quantitative, interpretable metrics  
- Provide a foundation for real-time, non-invasive diagnostic tools  

---

## Dataset
We used the EchoNet-Dynamic dataset ([link](https://echonet.github.io/dynamic)), which provides labeled echocardiogram videos.  

Each video is preprocessed by:
1. Extracting grayscale frames  
2. Segmenting into regional blocks  
3. Filtering pixel intensity signals using a bandpass filter (0.5–3.0 Hz)  
4. Computing STFT and PSD to capture temporal and spatial variations  

---

## Methodology

### Method 1: Frequency-Based Rhythm Analysis
- Extract temporal signals per block  
- Apply bandpass filtering  
- Perform STFT and compute spectrograms  
- Detect heart rate (BPM)  
- Classify into Bradycardia (<60 BPM), Normal (60–100 BPM), or Tachycardia (>100 BPM)  

### Method 2: Structural & Regional Analysis
- Compute dominant frequencies, phase coherence, spectral energy, and kurtosis for each region  
- Detect:  
  - Cardiomyopathy → High frequency & phase variation  
  - Valve Disease → Murmur-like spectral signatures, harmonic abnormalities  
  - Abnormal Motion → K-means clustering of regions, spatial incoherence  

---

## Results

- **Normal Heart:** Stable dominant frequency ≈70 BPM, high coherence, strong contractility  
- **Tachycardia:** Peak frequency >120 BPM, scattered phase patterns, reduced ejection fraction  
- **Cardiomyopathy:** High frequency/energy variation, low regional synchronization  
- **Valve Abnormalities:** Harmonic distortions, high spectral flatness (murmurs)  

Visualization outputs include:
- Frequency distribution maps  
- Phase coherence heatmaps  
- Regional energy maps  
- Clinical interpretation text reports  

---


