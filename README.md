# EmerGNN
The code of EmerGNN, which is designed for predicting interactions between emerging and existing drugs.


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
