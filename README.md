[arXiv]XXX  |  [Paper] XXX

# Brute-force-PDF-modelling

This script provides a brute-force modelling approach to predict the Mono-Metallic Nanoparticle (MMNP) from a Pair Distribution Function (PDF).

![alt text](images/bruteforce-figure.png "bruteforce-figure")

Currently the script is limited to MMNPs with up to 200 atoms of the 7 different structure types: Cubic (sc), body-centered cubic (bcc), face-centered cubic (fcc), hexagonal closed packed (hcp), decahedral, icosahedral and octahedral.

1. [DeepStruc](#deepstruc)
2. [Getting started (with Colab)](#getting-started-with-colab)
3. [Getting started (own computer)](#getting-started-own-computer)
3.1. [Install requirements](#install-requirements)
3.2. [Train model](#train-model)
3.3. [Predict](#predict)
4. [Simulate data](#simulate-data)
5. [Author](#author)
6. [Cite](#cite)
7. [Acknowledgments](#Acknowledgments)
8. [License](#license)  

# Getting started (own computer)
Follow these step if you want to use the brute-force modelling approach locally on your own computer.

## Install requirements
See the [install](/install) folder. 

## Train model
To train your own DeepStruc model simply run:
```
python train.py
```
A list of possible arguments or run the '--help' argument for additional information.  
If you are intersted in changing the architecture of the model go to __train.py__ and change the _model_arch_ dictionary. 
 
| Arg | Description | Example |  
| --- | --- |  --- |  
| `-h` or `--help` | Prints help message. |    
| `-d` or `--data_dir` | Directory containing graph training, validation and test data. __str__| `-d ./data/graphs`  |  
| `-s` or `--save_dir` | Directory where models will be saved. This is also used for loading a learner. __str__ | `-s bst_model`  |   
| `-r` or `--resume_model` | If 'True' the save_dir model is loaded and training is continued. __bool__| `-r True`  |
| `-e` or `--epochs` | Number of maximum epochs. __int__| `-e 100`  |  
| `-b` or `--batch_size` | Number of graphs in each batch. __int__| `-b 20`  |  
| `-l` or `--learning_rate` | Learning rate. __float__| `-l 1e-4`  |  
| `-B` or `--beta` | Initial beta value for scaling KLD. __float__| `-B 0.1`  |  
| `-i` or `--beta_increase` | Increments of beta when the threshold is met. __float__| `-i 0.1`  |  
| `-x` or `--beta_max` | Highst value beta can increase to. __float__| `-x 5`  |  
| `-t` or `--reconstruction_th` | Reconstruction threshold required before beta is increased. __float__| `-t 0.001`  |  
| `-n` or `--num_files` | Total number of files loaded. Files will be split 60/20/20. If 'None' then all files are loaded. __int__| `-n 500`  |  
| `-c` or `--compute` | Train model on CPU or GPU. Choices: 'cpu', 'gpu16', 'gpu32' and 'gpu64'. __str__| `-c gpu32`  |  
| `-L` or `--latent_dim` | Number of latent space dimensions. __int__| `-L 3`  |  

## Predict
To predict a MMNP using DeepStruc or your own model on a PDF:
```
python predict.py
```
A list of possible arguments or run the '--help' argument for additional information.  
 
| Arg | Description | Example |  
| --- | --- |  --- |  
| `-h` or `--help` | Prints help message. |    
| `-d` or `--data` | Path to data or data directory. If pointing to data directory all datasets must have same format. __str__| `-d data/experimental_PDFs/JQ_S1.gr`  |  
| `-m` or `--model` | Path to model. If 'None' GUI will open. __str__ | `-m ./models/DeepStruc`  |   
| `-n` or `--num_samples` | Number of samples/structures generated for each unique PDF. __int__| `-n 10`  |
| `-s` or `--sigma` | Sample to '-s' sigma in the normal distribution. __float__| `-s 7`  |  
| `-p` or `--plot_sampling` | Plots sampled structures on top of DeepStruc training data. Model must be DeepStruc. __bool__| `-p True`  |  
| `-g` or `--save_path` | Path to directory where predictions will be saved. __bool__| `-g ./best_preds`  |  


## Simulate data
See the [data](/data) folder. 

# Authors
__Andy S. Anker__<sup>1</sup>   
__Emil T. S. Kjær__<sup>1</sup>  
__Marcus N. Weng__<sup>1</sup>  
__Simon J. L. Billinge__<sup>2, 3</sup>     
__Raghavendra Selvan__<sup>4, 5</sup>  
__Kirsten M. Ø. Jensen__<sup>1</sup>    
 
<sup>1</sup> Department of Chemistry and Nano-Science Center, University of Copenhagen, 2100 Copenhagen Ø, Denmark.   
<sup>2</sup> Department of Applied Physics and Applied Mathematics Science, Columbia University, New York, NY 10027, USA.   
<sup>3</sup> Condensed Matter Physics and Materials Science Department, Brookhaven National Laboratory, Upton, NY 11973, USA.    
<sup>4</sup> Department of Computer Science, University of Copenhagen, 2100 Copenhagen Ø, Denmark.   
<sup>5</sup> Department of Neuroscience, University of Copenhagen, 2200, Copenhagen N.    

Should there be any question, desired improvement or bugs please contact us on GitHub or 
through email: __andy@chem.ku.dk__ or __etsk@chem.ku.dk__.

# Cite
If you use our code or our results, please consider citing our paper. Thanks in advance!
```
@article{kjær2022DeepStruc,
title={DeepStruc: Towards structure solution from pair distribution function data using deep generative models},
author={Emil T. S. Kjær, Andy S. Anker, Marcus N. Weng1, Simon J. L. Billinge, Raghavendra Selvan, Kirsten M. Ø. Jensen},
year={2022}}
```

# Acknowledgments
Our code is developed based on the the following approach presented in the publication:
```
@article{Banerjee:lk5048,
author = {Banerjee, Soham and Liu, Chia-Hao and Jensen, Kirsten M. Ø. and Juhás, Pavol and Lee, Jennifer D. and Tofanelli, Marcus and Ackerson, Christopher J. and Murray, Christopher B. and Billinge, Simon J. L.},
title = {Cluster-mining: an approach for determining core structures of metallic nanoparticles from atomic pair distribution function data},
year = {2020}}
```

# License
This project is licensed under the GNU GENERAL PUBLIC LICENSE Version 3 - see the [LICENSE.md](LICENSE.md) file for details.





