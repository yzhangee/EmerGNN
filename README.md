# EmerGNN
The code of EmerGNN, which is designed for predicting interactions between emerging and existing drugs.

## Installation
This section describes the installation process based on PyTorch. Firstly, you need to install PyTorch and CUDA. After that, you can proceed to install the necessary requirements. The running environment is a Linux server with Ubuntu and an NVIDIA GeForce RTX 3090 GPU. The CUDA version is 11.3.1. We provide the exact versions of packages we use to run this code as follows. Note that other versions may also work. Thanks for their contribution!
```
# Create conda environment
conda create -n emergnn python==3.8
# Install pytorch
conda install pytorch==1.10.1 torchvision==0.11.2 torchaudio==0.10.1 cudatoolkit=11.3 -c pytorch -c conda-forge
pip install torch-scatter torch-sparse torch-cluster torch-spline-conv torch-geometric -f https://data.pyg.org/whl/torch-1.10.1+cu113.html
# Install nvcc
conda install https://anaconda.org/conda-forge/cudatoolkit-dev/11.3.1/download/linux-64/cudatoolkit-dev-11.3.1-py38h497a2fe_0.tar.bz2
# Install other necessary requirements 
pip install -r requirements.txt
```

## Running scripts
To tune hyperparameters or reproduce the results, firstly cd into the corresponding directory, i.e., DrugBank or TWOSIDES, then run the following scripts:

Hyperparameter tuning:
```
python -W ignore tune_hyperms.py --dataset=emerging --n_epoch=20 --epoch_per_test=2 --gpu=0
```

Evaluation:
```
python -W ignore evaluate.py --dataset=emerging --n_epoch=40 --epoch_per_test=2 --gpu=0
```

The emerging file contains datasets used for prediction between emerging and existing drugs, while the existing file contains datasets used in SumGNN (Yu et. al. 2021) for prediction between existing drugs.

In our environment, results of both datasets in one round can be obtained within 1 day. Running on TWOSIDES can be faster than DrugBank since TWOSIDES is smaller.
