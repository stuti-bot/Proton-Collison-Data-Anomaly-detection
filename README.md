# Unsupervised Anomaly Detection in High-Energy Physics

<img width="274" height="184" alt="image" src="https://github.com/user-attachments/assets/67a9c65f-f1bf-4569-874e-60f515214f8b" />


A Jupyter Notebook performing Exploratory Data Analysis (EDA) and unsupervised anomaly detection on the CERN 2010 MultiJet dataset. An `IsolationForest` model is used to identify rare collision events relevant to new physics searches, successfully flagging events with high mass (MR), imbalance (Rsq), and missing energy (MET).

## Project Overview

This project demonstrates a model-agnostic approach to searching for new physics in unlabeled particle collision data. By applying an unsupervised machine learning model (`IsolationForest`), we can identify statistically rare events without any prior assumptions about a signal. The analysis shows that the model autonomously learns to flag events with the same key characteristics that physicists traditionally use in searches for phenomena like Supersymmetry (SUSY).

## Dataset

The dataset used is the **MultiJet Primary Dataset from the 2010 Run B** at CERN. It contains kinematic variables for events selected by a multi-jet trigger. The key variables for this analysis are the "Razor" variables `MR` (approximating the mass scale) and `Rsq` (related to event imbalance), along with other event properties like `HT` (total energy) and `MET` (missing transverse energy).

## Methodology

1.  **Exploratory Data Analysis (EDA):** The notebook begins with a thorough exploration of the dataset's features, focusing on the distributions of the key kinematic variables and their correlations.
2.  **Feature Engineering:** New, physically-motivated features such as `MET_over_HT` and `pt_ratio` are created to provide the model with more information.
3.  **Unsupervised Anomaly Detection:** An `IsolationForest` model is trained on the kinematic features. This model learns the distribution of "normal" background events and assigns an anomaly score to each event. Events that are easily isolated are considered anomalous.

## Key Results & Visualizations

The analysis successfully identifies a small fraction of events (5%) that are highly anomalous. These events are the most promising candidates for new physics.

### The Razor Plane

The majority of events cluster at low `MR` and low `Rsq`. The goal of a physics search is to investigate the sparse "tail" region at high `MR` and high `Rsq`.

<img width="1019" height="403" alt="image" src="https://github.com/user-attachments/assets/960df94f-80aa-4638-85c3-a652747cff40" />


### Anomaly Detection Results

The `IsolationForest` model assigns a continuous anomaly score to each event (lower is more anomalous). The visualization clearly shows that the most anomalous events are concentrated in the high-`MR` and high-`Rsq` region of the razor plane, validating the approach.

<img width="1022" height="429" alt="image" src="https://github.com/user-attachments/assets/b21e9007-ed15-49d9-8e9e-82a2954127c3" />



### Anomaly Characteristics

A statistical comparison confirms that the flagged anomalies are not random. On average, they have significantly higher energy, mass, and imbalance compared to normal events. The most dramatic difference is in Missing Transverse Energy (`MET`), which is **2.3 times higher** in anomalous events.

<img width="1020" height="541" alt="image" src="https://github.com/user-attachments/assets/479ad963-fed0-49cb-9e33-f09bb86f6420" />


## Conclusion

Without any prior labels or physics-based rules, the `IsolationForest` model independently learned to identify the key features that physicists use when searching for new phenomena. It successfully created a ranked list of candidate events characterized by:

1.  **High Mass** (`MR`)
2.  **High Energy** (`HT`, `pT`)
3.  **Large Missing Energy** (`MET`) and **Imbalance** (`Rsq`)

This project serves as a powerful demonstration of how unsupervised machine learning can be used as a tool for model-agnostic discovery in high-energy physics.

## How to Run

1.  Clone the repository.
2.  Install the required dependencies from `requirements.txt` (if provided) or install them manually.
3.  Launch Jupyter Notebook or JupyterLab and open `01_eda_proton_multijet.ipynb`.
4.  Run the cells sequentially.

## Dependencies

*   `pandas`
*   `numpy`
*   `matplotlib`
*   `seaborn`
*   `scikit-learn`
