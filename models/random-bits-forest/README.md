[RealityStream Models](../)


# RealityStream Models

## Random Bits Forest (RBF)

Predicting eye blinks. Hyperparameter Tuning identifies which brain voxels are the best predictors for blinks.  
In the **[target "y" column](https://github.com/ModelEarth/RealityStream/blob/main/models/random-bits-forest/blinks-input.csv)**, a `1` indicates a **blink**.

- **Testing Accuracy:**  **93% after tuning** (from 88% before tuning).  
- **Most important feature:** `X7` (*Occipital lobe - Vision processing*).  
- **Least important feature:** `X9` (*Parietal lobe - Sensory processing*).  

---

## About the Blinks Dataset  

The **EEG Eye State dataset** used in this project includes EEG data collected with the **Emotiv EEG Neuroheadset**.  
The dataset consists of **EEG electrode readings** mapped to various brain regions based on the **International 10-20 system**, a standard method for placing scalp electrodes during EEG recordings.

### **EEG Features Explained**
Each dataset attribute (e.g., `AF3`, `F7`, `F3`, etc.) corresponds to a **specific electrode placement on the scalp**, which measures electrical activity in different brain regions.

| **Electrode (Feature)** | **Brain Region** | **Function** |
|----------------|---------------------------|----------------------------------|
| **AF3 (X1), AF4 (X14)** | Prefrontal Cortex | Cognitive functions like decision-making and social behavior. |
| **F7 (X2), F3 (X3), F4 (X12), F8 (X13)** | Frontal Lobe | Reasoning, planning, speech, movement, emotions, and problem-solving. |
| **FC5 (X4), FC6 (X11)** | Frontal-Central | Motor function and high-level cognition. |
| **T7 (X5), T8 (X10)** | Temporal Lobe | Language processing, sensory input, emotional response. |
| **P7 (X6), P8 (X9)** | Parietal Lobe | Sensory information processing, numbers, and object manipulation. |
| **O1 (X7), O2 (X8)** | Occipital Lobe | Vision processing. |

###  **Target Variable**: `eyeDetection {0,1} (Y)`
- **0** → Eyes **open**  
- **1** → Eyes **closed**  
This was determined by **observing participants through a camera** during EEG recording.

### **Dataset Characteristics**
- **Chronological Order**: The values reflect continuous EEG recording over **117 seconds**.
- **[Dataset Link (Kaggle)](https://www.kaggle.com/)**  

---


Init virtual environment in RealityStream

	python3 -m venv env &&
	source env/bin/activate &&
	pip install numpy &&
	pip install pandas &&
	pip install scikit-learn

Run locally:

	python rbf.py blinks

[View Blinks Output](../../output/blinks/)

## Sparse Neural Network (with only 3 layers) 

 Random Bits Forest (RBF) performed better than seven other methods, including Nearest Neighbor regression.  

<img src="img/random-bits-forest.jpg" style="width:100%;max-width:864px;"><br><br>

### Random Bits Forest ML with tuning by Neural Network Deep Learning 

In 2016 Yi Wang further improved predications of eye blinks using the UC Irvine EEG dataset by preceding the random forest training with feature selection (tuning) using gradient boosting with a sparse neural network (with only 3 layers) to make decision tree splits that were less linear than random forest alone.

Wang, Y., Li, Y., Pu, W., Wen, K., Shugart, Y. Y., Xiong, M., & Jin, L. (2016). Random bits forest: a strong classifier/regressor for big data. Scientific reports, 6, 30086.

RBF Combines Machine Learning with sparse Neural Network (3 levels deep) [Paper](https://www.nature.com/articles/srep30086.pdf) | [Executable](http://sourceforge.net/projects/random-bits-forest/)


<!-- dscape/lab/brain -->

[EEG Eye State](https://archive.ics.uci.edu/ml/datasets/EEG+Eye+State)

[The Classification of Eye State](https://www.researchgate.net/profile/Kadir-Sabanci/publication/289685013_The_Classification_of_Eye_State_by_Using_kNN_and_MLP_Classification_Models_According_to_the_EEG_Signals/links/5aa992f5aca272d39cd5dde4/The-Classification-of-Eye-State-by-Using-kNN-and-MLP-Classification-Models-According-to-the-EEG-Signals.pdf) by Using kNN and MLP ClassificationModels According to the EEG Signals