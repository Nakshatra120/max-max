# Combining Physics-Based Protein–DNA Energetics with Machine Learning to Predict Interpretable Max–Max Transcription Factor–DNA Binding

This repository contains data, code, and analysis scripts for predicting transcription factor (TF) binding affinities using physically meaningful energy features derived from **Molecular Mechanics-Generalized Born Surface Area (MMGBSA)** calculations and **machine learning (ML)**.
We specifically focus on the **Max/Max homodimer** transcription factor system, extending and adapting the methodology from Carmen Al Masri’s [Myc/Max study](https://github.com/calmasri7/ML-Protein-DNA-Binding-Affinity).

## Project Structure

```
Max-Max_scripts/
├── process_gcPBM.ipynb
└── process_results.ipynb
```

## Directory Descriptions

### gcPBM

Experimental datasets, including genomic-context protein-binding microarray (gcPBM) data and universal PBM (uPBM) 8-mer binding affinity scores.
Load input data (uPBM and gcPBM) from https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSM2746660 and https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSM2579596 respectively.
Clean the max-max gcPBM data from GSM2579596_Max_rawdata.txt to only have rows corresponding to actual gene sequences. Get rid of rows with 'DarkCorner' or 'GE_BrightCorner' for example.
Then separate this max-max gcPBM dataset into a probe_sequences file and a normalized_intensity file. The script to perform this data cleaning is provided in /scripts/gcPBM_cleaning.ipynb 

### scripts

Data processing and analysis scripts:

* **[`process_gcPBM.ipynb`](scripts/process_gcPBM.ipynb)**: Prepares balanced datasets and labels for ML modeling.

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/Nakshatra120/max-max.git
cd max-max
```

### 2. Setup environment

**Prerequisites**

* Python 3.9
* Conda (recommended) or pip

**Conda installation**

```bash
conda env create -f environment.yml
conda activate mmgbsa_ml
```

**Alternative pip installation**

```bash
pip install numpy==1.20.0 pandas==1.3.5 scipy==1.7.3 scikit-learn==1.1.3 \
matplotlib==3.7.3 seaborn==0.13.2 plotly==5.17.0 shap==0.44.1 \
joblib==1.4.2 selenium==4.27.1 webdriver-manager==4.0.2 \
MDAnalysis==2.4.3 hyperopt==0.2.7 pyspark==3.5.4
```

### 3. Run analyses and ML models

Execute notebooks in the `scripts/` directory in this order:

1. `process_gcPBM.ipynb`
2. ...

For further details, refer to individual directory READMEs.

## Software Versions

| Package           | Version |
| ----------------- | ------- |
| numpy             | 1.20.0  |
| pandas            | 1.3.5   |
| scipy             | 1.7.3   |
| scikit-learn      | 1.1.3   |
| matplotlib        | 3.7.3   |
| seaborn           | 0.13.2  |
| plotly            | 5.17.0  |
| shap              | 0.44.1  |
| joblib            | 1.4.2   |
| selenium          | 4.27.1  |
| webdriver-manager | 4.0.2   |
| MDAnalysis        | 2.4.3   |
| hyperopt          | 0.2.7   |
| pyspark           | 3.5.4   |
| AmberTools        | 21.12   |
| GROMACS           | 2022.1  |
| jupyterlab        | 4.2.1   |

## environment.yml

```yaml
name: mmgbsa_ml
channels:
  - conda-forge
  - defaults
dependencies:
  - python=3.9          
  - numpy>=1.24,<1.27  
  - pandas=1.3.5
  - scipy=1.10         
  - scikit-learn=1.3   
  - shap=0.47.2        
  - matplotlib=3.7.3
  - seaborn=0.13.2
  - plotly=5.17.0
  - joblib=1.4.2
  - selenium=4.27.1
  - webdriver-manager=4.0.2
  - mdanalysis=2.4.3
  - hyperopt=0.2.7
  - pyspark=3.5.4
  - ambertools=21.12
  - gromacs=2022.1
  - jupyterlab=4.2
```

NACCESS also needs to be installed, available on http://www.bioinf.manchester.ac.uk/naccess/

## Contact

For questions, contact Nakshatra Bansal ([nabansal@ucsd.edu](mailto:nabansal@ucsd.edu)).
