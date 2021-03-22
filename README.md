# Microsoft-Azure-Machine-Learning-Engineer-Capstone-Project-Udacity-Final-Solution-Submission
Microsoft Azure Machine Learning Capstone Project for Udacity Nanodegree Program - Final Solution and Submission. Repository for Udacity Solution. 

## Overview
This project is part of the Udacity Microsoft Azure Machine Learning Engineer Nanodegree Program. During this project we performed an AutoML run on the Kaggle heart_failure_clinical_records_dataset.csv dataset, deployed the best model obtained from the AutoML as a RESTful API Webservice, consumed endpoints to interact with the deployed model in Microsoft Azure Machine Learning Studio. This project requires expertise in the Azure Machine Learning Studio Cloud and learning associated / ancillary technologies. This is the final project in the Nanodegree Program for Microsoft Azure Machine Learning Engineer. 

## Project Set up and Installation
**1. This project requires the creation of a compute instance in order to run a Jupyter Notebook & compute cluster to run the Machine Learning Experiments.**
**2. The dataset has to be manually selected.**
**3. Two experiments were run using AutoML & HyperDrive
**4. The Best Model Run, Metrics and a deployed model which consumes a RESTful API Webservice in order to interact with the deployed model.**

## Kaggle Dataset
Name: heart_failure_clinical_records_dataset.csv

This dataset contains the following features: age, anaemia, creatinine, diabetes, ejection_fraction, high_blood_pressure, platelets, serum_creatinine, sex, smoking and time. The target is DEATH_EVENT. 

## Heart Failure Overview
Heart Failure occures when the heart cannot pump enough blood in order to meet the needs of the body. This dataset was created from electronic medical records of patients with qualifying symptoms, body features, and clinical laboratory test values. These values were used to perform biostatistical analysis aimed at highlighting patterns and correlations otherwise undetectable by medical doctors. Machine Learning can help predict a patients' survival based on data from within their medical records. 

## Project
This is a classification problem where I will try to predict if the symptoms will cause death in a patient. The target variable is "DEATH_EVENT".

Thirteen (13) clinical features:

age: age of the patient (years)
anaemia: decrease of red blood cells or hemoglobin (boolean)
high blood pressure: if the patient has hypertension (boolean)
creatinine phosphokinase (CPK): level of the CPK enzyme in the blood (mcg/L)
diabetes: if the patient has diabetes (boolean)
ejection fraction: percentage of blood leaving the heart at each contraction (percentage)
platelets: platelets in the blood (kiloplatelets/mL)
sex: woman or man (binary)
serum creatinine: level of serum creatinine in the blood (mg/dL)
serum sodium: level of serum sodium in the blood (mEq/L)
smoking: if the patient smokes or not (boolean)
time: follow-up period (days)
[target] death event: if the patient deceased during the follow-up period (boolean)

## Key Steps
**1. Authentication**
This steps plays an important role in maintaining an uninterrupted flow of operations. Human intervention slows down the process - therefore authentication along with automation is considered an ideal scenario. A Service Principal is one of the examples of authentication where the user role is defined with user specific permissions.

**2. Automated Machine Learning Experiment to Determine the Best Model:**
We create an AutoML experiment when we first login to the AzureML portal and create a new compute instance for the new experiment. The virtual machine size chosen for the compute cluster is the Standard_DS2_V2 with one node as the minimum number of nodes. The experiment can take between 20 minutes and up to an hour to run with a concurrency of 10. This project did not time out on me - due to the fact that I utilized the Actual Azure Environment as opposed to the Udacity Virtual Machine (VM). I completed this project in approximately 5 hours. 

**3. Deploy the Best Model:**
The deployment of a model is the delivery of the best trained model into production so that i can be consumed by others. The best model obtained in the AutoML run is the VotingEnsemble with the highest accuracy of 0.8973. Deploying the model we configured the deployment settings by enabling authentication and using Azure Container Instance (ACI) [Docker] as it quickly deploys compute instances to deploy models. It is also very simple to utilize.

***4. Enable Logging:**
Enabling logging is a crucial step in the process vis a vis Enabling Application Insights. Application insights is a tool that helps in detecting anomalies and visualizing performance. It can be enabled before or after the deployment and can be modified with the SDK. In this project, we enable application insights after deploying by adding specific commands to the python SDK. The modified python script displaying logs.

**5. Swagger Documentation:**
Swagger is a great tool that helps us build, document and consume RESTful API webservices deployed in Azure Machine Learning Studio. It further explains what types of HTTP requests an API can consume, in this case like Post, Get and Update. A swagger.json is provided in the endpoints section of Azure that is used to create a website. This localhost website documents the HTTP endpoint for a deployed model. After running the swagger.sh and serve.py scripts, the webpage idsplays the contents of the API for the best model along with different HTTP requests supported.

**6. Consume Model Endpoints:**
Lastly, the deployed service is consumed via an HTTP API. We initiate an inpute request, in this case via an HTTP Post request method to submit data. The HTTP GET request is another request method to retrieve information from a web server. This creates a bi-directional flow of allowed information in Azure. In order to consume deployed services, we modify the URI and key to match the primary key for our service and RESTful URI is generated after deployment. The execution of the endpoint.py script after modification gives the output. Proof that we consumed the endpoint created a data.json file which is in the GitHub Repository. 

### Architecture Diagram<img src="/images/Slide36.PNG">
### HyperDrive - Hyperparameter Tuning - Login / Credentials / Workspace<img src="/images/Slide1.PNG">
### Microsoft Azure Login<img src="/images/Slide2.PNG">
### HyperDrive - Run Details<img src="/images/Slide3.PNG">
### HyperDrive - Run Details Widget<img src="/images/Slide4.PNG">
### HyperDrive - Run Details - Run is Completed<img src="/images/Slide5.PNG">
### HyperDrive - Best Model / Run ID / Accuraccy<img src="/images/Slide6.PNG">
### HyperDrive - Proof of Runs<img src="/images/Slide7.PNG">
### HyperDrive - Child Runs<img src="/images/Slide8.PNG">
### AutoML - Running on Remote<img src="/images/Slide9.PNG">
### AutoML - Run3 Completion<img src="/images/Slide10.PNG">
### AutoML - Endpoints / Deployment<img src="/images/Slide11.PNG">
### AutoML - Endpoints / Consume<img src="/images/Slide12.PNG">
### AutoML - Endpoints / Deploy / Healthy Status<img src="/images/Slide13.PNG">
### AutoML - Endpoints / Model ID / Deployment / Swagger URI / Application Insights<img src="/images/Slide14.PNG">
### AutoML - Endpoints / Deployment Logs<img src="/images/Slide15.PNG">
### AutoML - Endpoints / Deployment Logs 2<img src="/images/Slide16.PNG">
### AutoML - Run Details Widget<img src="/images/Slide17.PNG">
### AutoML - Run Details - Best Model Run / VotingEnsemble<img src="/images/Slide18.PNG">
### AutoML - Run Details - Completed<img src="/images/Slide19.PNG">
### AutoML - Run Details - Completed 2<img src="/images/Slide20.PNG">
### AutoML - Best Model Metrics<img src="/images/Slide21.PNG">
### AutoML - Run Experiment Status / Model Deployment / Model Registration<img src="/images/Slide22.PNG">
### HyperDrive - Run Details Widget / Hyperparameters Tuned / Best Model ID & Accuracy / Run Status<img src="/images/Slide23.PNG">
### AutoML - Run Details - Status / Model Deployment / Model Registration<img src="/images/Slide24.PNG">
### AutoML - Model Deployment - Writing amlscore.py / Best Run Metrics<img src="/images/Slide25.PNG">
### AutoML - Model Deployment / Best Run Metrics - All<img src="/images/Slide26.PNG">
### AutoML - AciServiceDeployment / Configuration Object / Pipeline<img src="/images/Slide27.PNG">
### AutoML - Model Deployment / Best Run / Get Tags<img src="/images/Slide28.PNG">
### AutoML - Model Deployment / Register Environment / Image / Deployment / Checking Deployment / Deployment Status = "Succeeded"<img src="/images/Slide29.PNG">
### AutoML - Model Deployment / Get Logs<img src="/images/Slide30.PNG">
### AutoML - Model Deployment / URI Scoring / Healthy Status / Output & Status Confirmation = 200 = Success<img src="/images/Slide31.PNG">
### AutoML - Service Logs<img src="/images/Slide32.PNG">
### AutoML - Endpoints / Deployed Endpoints<img src="/images/Slide33.PNG">
### AutoML - Endpoints / Deployed Endpoints / Healthy Status<img src="/images/Slide34.PNG">
### AutoML - Endpoint "automl-final" deployment Completed Proof<img src="/images/Slide35.PNG">

## Future Improvements
Benchmarking can be done using Apache Benchmark command-line tool to keep the performance of the model in check and above a standard level. It is used to determine the response time in seconds for the model that is deployed. Additionally, you could try different models to get the best possible one. If we reduced the duration of the experiment or increased the number of processes running in parallel then the experiment will be fast and time can be save - however resource costs may increase. The use of the Kubernetes service can be helpful in case we add more data to the existing dataset. Lastly, the exploration of possibly using Deep Learning to get to a more accurate model. Lastly, it would be even better if we could get more data records from electronic health records. This project took approximately 5 hours to complete.

## Video Link

[Video Link](https://www.dropbox.com/s/af4nk34mvo3jyn6/Recording%20%239.mp4?dl=0)



