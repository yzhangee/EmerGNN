# EmerGNN
The code of EmerGNN, which is designed for predicting interactions between emerging and existing drugs.

## Requirements

The running environment is a Linux server with CentOS, NVIDIA GeForce 3090 GPU. The cuda version is 11.4 and Nvidia Driver version is 470.57.02. We provide the exact versions of packages we use to run this code as following. The other versions may also work. Thanks to their contribution!
- pytorch: 1.10.2+cu111
- torch_scatter: 2.0.9
- torchdrug: 0.1.3
- hyperopt: 0.2.7
- sklearn: 1.0.2
- scipy: 1.7.3

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
