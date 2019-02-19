# DEVELOPING & DEPLOYING MACHINE LEARNING MODELS ON AZURE MACHINE LEARNING SERVICE (AMLS) & DATABRICKS

## BACKGROUND

This sample project demonstrates the development and deployment of a non-trivial machine learning model using AMLS. We will be using Databricks as the development environment. This repository consists of three Databricks notebooks:

`pumps-local.pnyb` demonstrates training models locally on Databricks in a notebook  
`pumps-train-amls.pnyb` covers training a model on AMLS with HyperDriver (hyperparameter grid search) and finally registering a model image on AMLS  
`pumps-deploy-amls.pnyb` covers how to deploy the model we built in the previous notebook on [tbd] cluster using [tbd] service.

#### NOTE: 
`pumps-deploy-amls.pnyb` is still a work in progress. 


## APPROACH:

While training, we will use `HyperDrive` to iterate over and find the best model hyperparameters via gridsearch. Each iteration will be logged as an experiment. We wil also use data transformers to label and one-hot encode data. These transformers will be saved and utilized along with the model file itself.

These are the steps that need to be followed to train and deploy models on AMLS:

#### TRAINING
1. Configure the development environment
2. Upload your data to blob storage
3. Create a training script called `train.py`
4. Submit the job
5. Register the final model

#### DEPLOYMENT
1. Configure the development environment
2. Test the model locally
3. Create an execution script called `score.py`
4. Configure a cluster image
5. Deploy the cluster
6. Test the web service

## DEPENDENCIES
The following packages were used in both the Databricks as well as the AMLS compute resources.Use the 'Libraries' section in the Databricks cluster to install these on the Databricks cluster. The configuration scripts for AMLS already has these packages specified in the notebook.  

```
azureml-sdk[databricks]
category-encoders==1.3.0
numpy==1.15.0
pandas==0.24.1
scikit-learn==0.20.2
```
In addition, here are some additional Databricks environment configs:   
Databricks Runtime: 5.2  
Python Version: 3

