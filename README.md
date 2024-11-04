# Operationalizing Machine Learning

This project is part of the Udacity Azure ML Nanodegree. It demonstrates how to configure, deploy, and consume a machine learning model in a cloud-based Azure environment. The project also includes steps to create, publish, and consume a machine learning pipeline.

## Architectural Diagram

- **Authentication**: Set up a Security Principal (SP) to access the Azure Workspace.
- **Automated ML Experiment**: Configure and run an Automated ML experiment using a compute cluster.
- **Deploy the Best Model**: Deploy the top-performing model to interact with it via HTTP API and POST requests.
- **Enable Logging**: Set up logging to monitor requests, response times, and other metrics for the deployed model.
- **Swagger Documentation**: Use Swagger to access and test the deployed model's endpoints.
- **Consume Model Endpoints**: Test the model by sending data to the endpoint and retrieving inferences.
- **Create and Publish a Pipeline**: Use the Python SDK to automate and publish the model workflow in a pipeline.

## Key Steps
### Authentication
A Udacity virtual machine was used, skipping this step as authentication was already configured.

### Automated ML Experiment
- Created an AutoML experiment with the Bank Marketing dataset, uploaded to the workspace with column `y` selected as the target.
- Used a Standard_DS3_V2 virtual machine with a minimum of 1 node.
- Configured the experiment for classification, resulting in a Voting Ensemble as the best model.
#### Registered dataset
![01_registered_dataset.png](/images/01_registered_dataset.png)
#### Completed AutoML experiment
![02.1_completed_automl_experiment.png](/images/02.1_completed_automl_experiment.png)
#### Best model
![02.2_best_model.png](/images/02.2_best_model.png)

![02.3_best_model.png](/images/02.3_best_model.png)

### Deploy the Model
- Deployed the Voting Ensemble model using Azure Container Instance (ACI) with authentication enabled.
#### Deloy the model
![03_deloy_the_model.png](/images/03_deloy_the_model.png)

### Enable Logging
Application Insights is actived and Logs script is run . 
#### Run logs file
![04.1_run_logs_file.png](/images/04.1_run_logs_file.png)
#### Application insight enable
![04.2_application_insight_running.png](/images/04.2_application_insight_running.png)

### Swagger Documentation
To use Swagger for model consumption, downloaded the `swagger.json` file and ran the `swagger.sh` and `serve.py` scripts.
#### Swagger page
![05_swagger_page.png](/images/05_swagger_page.png)

### Consume Model Endpoints
Updated the `endpoint.py` script with the `scoring_uri` and authentication key to interact with the API.
#### Interact with endpoint
![06.1_interact_with_endpoint.png](/images/06.1_interact_with_endpoint.png)

### Benchmark
Ran `benchmark.sh` to test the model's performance with Apache Benchmark (optional).
#### Benchmark run
![06.2_benchmark_run.png](/images/06.2_benchmark_run.png)

### Create and Publish a Pipeline
Used a Jupyter notebook to create, publish, and consume a pipeline for the dataset.
#### Create pipeline
![07.1_create_pipeline.png](/images/07.1_create_pipeline.png)
#### Pipeline status and REST endpoint
![07.2_pipeline_endpoint_active.png](/images/07.2_pipeline_endpoint_active.png)
#### Dataset and AutoML in pipeline
![07.3_dataset_and_automl_in_pipeline.png](/images/07.3_dataset_and_automl_in_pipeline.png)

## Screen Recording
Link youtube to the screencast: [Watch on YouTube](https://youtu.be/qFy1EYhARgw)


## Standout Suggestions
*Optional*: This section highlights additional, unique improvements made to enhance the project.

### Suggestions Implemented
- **Advanced Logging and Monitoring**: Integrated enhanced logging features using Azure Monitor, allowing for more detailed tracking of model performance metrics and request-response times.
- **Custom Model Metrics**: Configured custom metrics for model evaluation, such as F1 score and precision, to ensure the model meets project-specific requirements.
- **Pipeline Optimization**: Implemented optimizations in the pipeline for faster runtime, such as caching intermediate steps and selecting a high-performance compute cluster.

These adjustments help improve model transparency, efficiency, and reliability in the production environment.


