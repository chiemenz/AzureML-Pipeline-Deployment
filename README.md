## Udacity Project 

The Goal of this project was to find and deploy a well performing classification model which can predict the 
success of a marketing campaign based on customer input features. The features of an example customer are shown 
bellow:

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

The best model was a VotingEnsemble classifier with a weighted area under the curve score (weighted AUC) of 0.94794.
This model was deployed to a Container Instance with Authentication. 



In this project, you will following the below steps:

    Authentication
    Automated ML Experiment
    Deploy the best model
    Enable logging
    Swagger Documentation
    Consume model endpoints
    Create and publish a pipeline
    Documentation
,



Here is the link to the brief video showing:

* 1.) The deployed model endpoint
* 2.) How to consume the deployed model with the endpoint.py script
* 3.) The AutoML model ==> best selected model
* 4.) The Published Pipeline

[Link to Video](https://www.loom.com/share/19379c75f6bf4158a697814dd1465fbf)
