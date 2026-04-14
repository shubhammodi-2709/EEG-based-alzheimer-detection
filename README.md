# EEG-Based Alzheimer’s Disease Detection using Signal Processing and Deep Learning

## Overview
This project presents an automated approach to detect Alzheimer’s disease using EEG (Electroencephalogram) signals. By combining signal preprocessing techniques with deep learning, the model learns patterns in brain activity and classifies subjects as Alzheimer (AD) or Normal.

---

## Objective
- Detect Alzheimer’s disease using EEG signals  
- Apply signal preprocessing to improve signal quality  
- Use deep learning (CNN) for classification  
- Build a reproducible and interpretable pipeline  

---

## Dataset
- Source: Mendeley Data  
- Link: https://data.mendeley.com/datasets/sgzbgwjfkr/5  
- Format: `.mat` (MATLAB files)  

### Files Used
- `AD.mat` → Alzheimer patients  
- `normal.mat` → Healthy controls  

### Data Structure
- MATLAB structured arrays  
- Key field: `epoch`  

### Hierarchy

subjects → epochs → EEG signals


### Challenges
- Nested MATLAB structure  
- Variable-length EEG signals  

---

## Data Preprocessing

### Bandpass Filter (1–40 Hz)
Removes low-frequency drift and high-frequency noise while preserving relevant brainwave frequencies.

### Notch Filter (50 Hz)
Eliminates powerline interference commonly present in EEG recordings.

### Normalization
Standardizes signals to zero mean and unit variance for stable training.

### Handling Variable Length
All EEG samples are cropped to a uniform minimum length to ensure consistent input size.

---

## Feature Extraction

### FFT (Fast Fourier Transform)
- Converts EEG signals from time domain to frequency domain  
- Used as a baseline for frequency analysis  

### Spectrogram
- Converts signals into time-frequency representation  
- Produces 2D input suitable for CNN  
- Preserves both temporal and frequency information  

---

## Model Architecture

### Convolutional Neural Network (CNN)
- Input: Spectrogram  

#### Layers:
- Conv2D (32 filters, 2×2 kernel, ReLU)  
- Conv2D (64 filters, 2×2 kernel, ReLU)  
- Flatten  
- Dense (64 units, ReLU)  
- Output Dense (1 unit, Sigmoid)  

### Classification
- Alzheimer (AD) → 1  
- Normal → 0  

---

## Training Details
- Train-Test Split: 80-20  
- Loss Function: Binary Crossentropy  
- Optimizer: Adam  
- Epochs: 10  

---

## Results
- Test Accuracy: ~84.8%  
- Consistent training and validation performance  
- No significant overfitting observed  

---

## Performance Metrics
- Accuracy  
- Loss  
- Validation Accuracy  

---

## Visualizations
- Loss vs Epochs  
- Accuracy vs Epochs  
- Learning Rate vs Loss  

---

## Final Data Shape

### After preprocessing
Each sample: (59,)

### After spectrogram
Each sample: (9, 6)


### Final model input
X: (4800, 9, 6, 1)
y: (4800,)


---

## Tools and Libraries
- Python (Google Colab)  
- NumPy  
- SciPy  
- Scikit-learn  
- TensorFlow / Keras  
- Matplotlib  

---

## Challenges Faced
- Handling nested `.mat` file structure  
- Managing variable-length EEG signals  
- Generating correct spectrogram dimensions  
- Resolving CNN input shape issues  

---

## Future Work
- Improve accuracy with better feature extraction  
- Use larger datasets  
- Explore advanced architectures:
  - LSTM  
  - Transformer  

---

## Contributors
- Shubham Modi

---

## Conclusion
This project demonstrates that combining signal processing techniques with deep learning can effectively detect Alzheimer’s disease from EEG signals, achieving reliable performance (~85% accuracy).
