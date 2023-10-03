# Deploying an end-to-end MLOps solution with AzureML - Udacity ML Engineer with Azure Nanodegree

In this project I have demonstrated my ability to create an end-to-end ML solution, including training a ML model using Azure AutoML, deploying the best performing model as a REST endpoint for inference, and publishing the training pipeline as an endpoint as well in order to retrain the model if needed.

## Architectural Diagram
![Alt text](https://github.com/dleston/nd00333_AZMLND_C2/blob/master/screenshots/architecture.png?raw=true)

## Key Steps

- The first step required me to register the bank marketing dataset that has been used as a toy dataset.
![Alt text](https://github.com/dleston/nd00333_AZMLND_C2/blob/master/screenshots/registered_dataset.png?raw=true)
- I created a new AutoML experiment that would run in a compute cluster that I created for that purpose.
![Alt text](https://github.com/dleston/nd00333_AZMLND_C2/blob/master/screenshots/automl_experiment_complete.png?raw=true)
- I then selected the best performing model, in this case a weighted average of several models, and deployed it as a REST endpoint using an Azure Container Instance (ACI).
![Alt text](https://github.com/dleston/nd00333_AZMLND_C2/blob/master/screenshots/best_automl_model.png?raw=true)
- I enabled Application Insights once the deployment was healthy through the python SDK in order to retrieve logs.
![Alt text](https://github.com/dleston/nd00333_AZMLND_C2/blob/master/screenshots/application_insights_enabled.png?raw=true)
![Alt text](https://github.com/dleston/nd00333_AZMLND_C2/blob/master/screenshots/logs.png?raw=true)
- I deployed locally a swagger container and started a python server for the swagger UI to access the swagger.json file. I was then able to access and fiddle with the deployment's REST API docs.
![Alt text](https://github.com/dleston/nd00333_AZMLND_C2/blob/master/screenshots/swagger.png?raw=true)
- I used a python script to consume the model endpoint by launching inference requests and parsing the json output to retrieve the inference result.
![Alt text](https://github.com/dleston/nd00333_AZMLND_C2/blob/master/screenshots/endpoint_output.png?raw=true)
- I published the training pipeline to the workspace, and activated its endpoint so that we can trigger a pipeline run request
![Alt text](https://github.com/dleston/nd00333_AZMLND_C2/blob/master/screenshots/pipeline_endpoint_created.png?raw=true)
- Finally, we executed the pipeline and check that it had been succesfully re-run.
![Alt text](https://github.com/dleston/nd00333_AZMLND_C2/blob/master/screenshots/pipeline_endpoint_complete.png?raw=true)
![Alt text](https://github.com/dleston/nd00333_AZMLND_C2/blob/master/screenshots/rundetails_widget.png?raw=true)


## Screen Recording
[https://youtu.be/IKeApCYjE4M](https://youtu.be/IKeApCYjE4M)

## Standout Suggestions
- We could probably improve the training step. The goal of this module was to learn MLOps and we thus disregarded crucial steps in model training, such as controlling the perfomance of the model over external sets, or using a validation set.
- I would have liked to explore different flavors of deployment, such as using AKS, real-time and batch deployments...
- Finally, something I'd also like to checkout is the usage of rules for automatic retraining rather than a scheduled retrain. Also monitoring for dataset drift, and other crucial steps of MLOps. The fact that the dataset is static is also something that would be great to change. Make it dynamic, expandable... as any dataset tends to be once we gather extra data!
