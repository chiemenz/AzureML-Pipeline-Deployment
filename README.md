## Udacity Project 

The Goal of this project was to find and deploy a well performing classification model which can predict the 
success of a marketing campaign based on customer input features. The features of an example customer are shown 
bellow. For the implementation have a look at the [AzureML Pipeline Deployment Notebook](https://github.com/chiemenz/AzureML-Pipeline-Deployment/blob/master/automl-example.ipynb)

 {
            "age": 48,
            "campaign": 1,
            "cons.conf.idx": -36.2,
            "cons.price.idx": 92.893,
            "contact": "cellular",
            "day_of_week": "mon",
            "default": "no",
            "duration": 971,
            "education": "university.degree",
            "emp.var.rate": -1.8,
            "euribor3m": 1.299,
            "housing": "no",
            "job": "blue-collar",
            "loan": "yes",
            "marital": "married",
            "month": "may",
            "nr.employed": 5099.1,
            "pdays": 999,
            "poutcome": "failure",
            "previous": 1
5

# Architecture of the Project 
Have a look at this diagram [ArchitectureDiagram](https://github.com/chiemenz/udacity_lab2/blob/master/ArchitectureDiagram.PNG)

# Steps of the Project

    1. Authentication
    2. Automated ML Experiment
    3. Deploy the best model
    4. Enable logging
    5. Swagger Documentation
    6. Consume model endpoints
    7. Create and publish a pipeline
    8. Documentation

## 1.) Authentication 
The user was granted the owner role by executing the **az workspace share** command with the credentials.

The Authentication Role Owner was granted via workspace share [Authentication Role](https://github.com/chiemenz/udacity_lab2/blob/master/AuthenticationRoleOwner.PNG)

## 2.) An Automated ML Experiment was executed to find a classifier for the success of a bank marketing campaign
The an optimal classifier for the success of a bank marketing campaign given the customer features is trained based on a registered dataset see:
Registered Bank Marketing Dataset [RegisteredBankMarketingSet](https://github.com/chiemenz/udacity_lab2/blob/master/RegisteredBankMarketingSet.PNG)

The best model was a **VotingEnsemble** classifier with a weighted area under the curve score **(weighted AUC) of 0.94794**
This model was deployed to a Container Instance with Authentication. 

The AutoML Experiment Run has been completed [AutoML completed](https://github.com/chiemenz/udacity_lab2/blob/master/AutoMLExpCompleted.PNG)

THe results of the AutoML run are enlisted here [Best Model Experiment](https://github.com/chiemenz/udacity_lab2/blob/master/BestModelExperiment.PNG)

## 3.) The best model was deployed 
For the best model you can see that it has been both registered and deployed [Best Deployed Model](https://github.com/chiemenz/udacity_lab2/blob/master/best_deployed_model.PNG)

## 4.) Logging via Application insights was enabled
Application Insights is enabled for the deployed marketingmodel[Application Insights Enabled](https://github.com/chiemenz/udacity_lab2/blob/master/ApplicationInsightsEnabled.PNG)

The logs.py output can be seen here [Log Outputs](https://github.com/chiemenz/udacity_lab2/blob/master/LogsOutput.PNG)

## 5.) The endpoint was documented via Swagger by using a python flask application 
A Swagger Container is running on Port 4030 [SwaggerContainerRunningOnPort4030](https://github.com/chiemenz/udacity_lab2/blob/master/SwaggerContainerRunningOnPort4030.PNG)

Since the default python commands for running a local Swagger container in combination with a python serving script were not succeeding a python flask app was created 
instead and the "swagger.json" was hosted by means of this flask swagger UI app instead (https://github.com/chiemenz/udacity_lab2/blob/master/app_project.zip)

The model POST and GET endpoints are documented with Swagger [Model Swagger Docu](https://github.com/chiemenz/udacity_lab2/blob/master/ModelSwaggerUI.PNG) & [Model Swagger Input Params](https://github.com/chiemenz/udacity_lab2/blob/master/ModelExampleSwaggerValues.PNG)

## 6.) The deployed model endpoint was consumed via HTTP POST requests
Result of **python endpoint.py** [Consume Endpoint Result](https://github.com/chiemenz/udacity_lab2/blob/master/ConsumeEndpointResult.PNG)

## 7.) A AutoML Pipeline is created and can be triggered via HTTP endpoint by publishing
A Pipeline was created [Pipeline Creation](https://github.com/chiemenz/udacity_lab2/blob/master/PipelineCreated.PNG)

The Pipeline was published [Pipeline Published](https://github.com/chiemenz/udacity_lab2/blob/master/PublishedPipeline.PNG)

The BankMarketingAutoML Pipeline Endpoint is active [ActivePipelineEndpoint](https://github.com/chiemenz/udacity_lab2/blob/master/ActivePipelineEndpoint.PNG)

An AutML pipeline has been started by HTTP post request of the Published pipeline [AutoML run by POST REQUEST](https://github.com/chiemenz/udacity_lab2/blob/master/AutoMLRunByPostRequest.PNG)

A pipeline has been scheduled with a 4 hour interval [Create Scheduled Pipeline](https://github.com/chiemenz/udacity_lab2/blob/master/CreateScheduledPipeline.PNG)

A queued Pipeline by Post request [QueuedPipelineRunByPostRequest](https://github.com/chiemenz/udacity_lab2/blob/master/QueuedPipelineRunByPostRequest.PNG)

Run details of the pipeline step [RunDetailsPipelineSteps](https://github.com/chiemenz/udacity_lab2/blob/master/RunDetailsPipelineSteps.PNG)

# Future improvements
* Automated deployment of the model after the AutoML pipeline has finished instead of manual deployment
* The AutoML pipeline should be automatically triggered if there are changes to the Bank Marketing Dataset alternatively a Pipeline should be 
 triggered via schedule depending on how quickly the customer dataset shifts (e.g. by monitoring how much the incoming customer features differ 
 from the existing training dataset) 
* Alternatively a pipeline which is not performing a whole AutoML run but just a retraining of the best existing model should be setup and maybe scheduled on
a regular basis
* The Swagger UI with the endpoint documentation should be hosted on a VM (not run on a local docker container)
 (also the Pipeline Endpoint documentation should be added there)
* The traffic to the model endpoint should be observed and maybe a more powerful compute cluster is needed for inference depending on the number of requests


# Video
Here is the link to the brief video showing:

* 1.) The deployed model endpoint
* 2.) How to consume the deployed model with the endpoint.py script
* 3.) The AutoML model ==> best selected model
* 4.) The Published Pipeline

[Link to Video](https://www.loom.com/share/19379c75f6bf4158a697814dd1465fbf)

# License
The content of this repository is licensed under a [MIT License](https://github.com/chiemenz/AzureML-Sentiment-Classification-and-Model-Deployment/blob/master/LICENSE.txt)
