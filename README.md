# DCASE2020-Anomly-Detection
This repo is actually taken from "https://github.com/parth2170/DCASE2020-Task2" and the issues related to the library versions are resolved.

# MODULATION SPECTRAL SIGNAL REPRESENTATIONAND I-VECTORS FOR ANOMALOUS SOUND DETECTION

This repository can be used to reproduce our submissions for **DCASE Challenge 2020 Task 2** - <em>Unsupervised Detection of Anomalous Sounds for Machine Condition Monitoring</em>


#### Abstract
This report summarizes our submission for Task-2 of the DCASE 2020 Challenge. We propose two different anomalous sound detection systems, one based on features extracted from a modula- tion spectral signal representation and the other based on i-vectors extracted from mel-band features. The first system uses a nearest neighbour graph to construct clusters which capture local variations in the training data. Anomalies are then identified based on their distance from the cluster centroids. The second system uses i-vectors extracted from mel-band spectra for training a Gaussian Mixture Model. Anomalies are then identified using their negative log likelihood. Both these methods show significant improvement over the DCASE Challenge baseline AUC scores, with an average improvement of 6% across all machines. An ensemble of the two systems is shown to further improve the average performance by 11% over the baseline.


**Requirements**

```
conda create -n <env-name> python==3.8
conda activate <env-name>
git clone https://github.com/jfsantos/SRMRpy.git
cd SRMRpy/
python setup.py install
pip install -r requirements.txt
```

## Usage

#### 1. Clone this repository
#### 2. Download datasets
- Datasets are available [here](https://zenodo.org/record/3678171)
- Datasets for all machines can be downloaded and unzipped by running
    - `sh download_dev_data.sh` for development data
    - `sh download_eval_data.sh` for evaluation data

#### 3. Running System 1
- `cd bin/modspec_graph/`
- `python graph_anom_detection.py d` - for running on development data
    - Modulation Spectrums for each machine-id will be stored in `npy` files in `saved/` in the same directory
    - The results for development data are stored in `modspec_graph_dev_data_results.csv` in the same directory
- `python graph_anom_detection.py e` - for running on evaluation data
    - The results for evaluation data are stored in the submission format in the directory `task2`

#### 3. Running System 2
- i-Vectors for both development and evaluation have been provided in the zip file -  `saved_iVectors/ivector_mfcc_100.zip`
- Unzip `ivector_mfcc_100.zip` in the same directory
    - Code for extracting i-Vectors will be added soon
- `cd bin/iVectors_gmm/`
- `python gmm.py d` - for running on development data
    - The results for development data are stored in `iVectors_gmm_dev_data_results.csv` in the same directory
- `python gmm.py e` - for running on evaluation data
    - The results for evaluation data are stored in the submission format in the directory `task2`


    
