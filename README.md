# Operationalizing Machine Learning

This project is part of the Udacity Azure ML Nanodegree. It demonstrates how to configure, deploy, and consume a machine learning model in a cloud-based Azure environment. The project also includes steps to create, publish, and consume a machine learning pipeline.

## Project Overview
This project focuses on a bank marketing campaign, where a model is trained using Azure's AutoML. The trained model is then consumed through a REST endpoint, allowing for easy integration and testing with real-world data. Additionally, a pipeline is created to automate the workflow, which is essential for streamlining model retraining and deployment, ensuring consistency and efficiency in the production environment.

## Architectural Diagram
Here is the architectual diagram of the project
![00.1_architectual_diagram.png](/images/00.1_architectual_diagram.png)

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

#### Registered Dataset
Successfully registered the dataset for use in the AutoML process.
![01_registered_dataset.png](/images/01_registered_dataset.png)

#### Completed AutoML Experiment
Image showing that the AutoML experiment has completed successfully.
![02.1_completed_automl_experiment.png](/images/02.1_completed_automl_experiment.png)
![02.1_completed_automl_experiment_2.png](/images/02.1_completed_automl_experiment_2.png)

#### Best Model
Images showing the best model, Voting Ensemble, selected from the AutoML experiment.
![02.2_best_model.png](/images/02.2_best_model.png)
![02.3_best_model.png](/images/02.3_best_model.png)

### Deploy the Model
Deployed the best model (Voting Ensemble) using Azure Container Instance (ACI) with authentication enabled for secure access.
Image showing the deployment of the model with the Deploy state Healthy and Operation state is Succeeded.
![03_deloy_the_model.png](/images/03_deloy_the_model.png)

### Enable Logging
Application Insights was enabled to track and log model usage, ensuring we can monitor performance and debug as needed. Additionally, a logging script was run to verify the setup.

#### Run Logs File
Image showing the logging script being executed.
![04.1_run_logs_file.png](/images/04.1_run_logs_file.png)
![04.1_run_logs_file_2.png](/images/04.1_run_logs_file_2.png)

#### Application Insights Enabled
Screenshot showing that Application Insights enabled is true.
![04.2_application_insight_running.png](/images/04.2_application_insight_running.png)

### Swagger Documentation
To facilitate model consumption, Swagger documentation was configured. The `swagger.json` file was downloaded, and `swagger.sh` and `serve.py` scripts were run to launch Swagger, providing an interactive API documentation.

#### Swagger Page
Screenshot showing the Swagger interface, which allows us to test the model API.
![05_swagger_page.png](/images/05_swagger_page.png)

### Consume Model Endpoints
The `endpoint.py` script was updated with the `scoring_uri` and authentication key, enabling interaction with the deployed model for testing and inference.

#### Interact with Endpoint
Screenshot showing the interaction with the model endpoint.
![06.1_interact_with_endpoint.png](/images/06.1_interact_with_endpoint.png)

### Benchmark
The `benchmark.sh` script was executed to evaluate the model's performance under load, using Apache Benchmark to test response times and reliability.
Images showing the benchmark testing process.
![06.2_benchmark_run.png](/images/06.2_benchmark_run.png)

### Create and Publish a Pipeline
Using a Jupyter notebook, a pipeline was created, published, and configured to automate the model workflow with the dataset. This pipeline ensures that data flows and model training processes are automated and repeatable.

#### Create Pipeline
Screenshot of the pipeline creation process completed.
![07.7_pipeline_in_job_section_with_completed_status.png](/images/07.7_pipeline_in_job_section_with_completed_status.png)
![07.1_completed_pipeline_experiment.png](/images/07.1_completed_pipeline_experiment.png)

#### Pipeline Status and REST Endpoint
Screenshot showing that the pipeline is active and a REST endpoint has been created.
![07.2_pipeline_endpoint_active.png](/images/07.2_pipeline_endpoint_active.png)
The image show the Pipeline Endpoint in Pipeline section of Azure ML Studio
![07.6_pipeline_active_page.png](/images/07.6_pipeline_active_page.png)

#### Dataset and AutoML in Pipeline
Image showing the dataset and AutoML model in the pipeline.
![07.3_dataset_and_automl_in_pipeline.png](/images/07.3_dataset_and_automl_in_pipeline.png)

#### DetailRun Widget in notebook
Image showing the DetailRun Widget in notebook with information about the pipeline run.
![07.4_rundetails_widget_0.png](/images/07.4_rundetails_widget_0.png)
![07.4_rundetails_widget.png](/images/07.4_rundetails_widget.png)

## Screen Recording
Link youtube to the screencast: [Watch on YouTube](https://youtu.be/qFy1EYhARgw)


## Standout Suggestions
*Optional*: This section highlights additional, unique improvements made to enhance the project.

### Suggestions Implemented
- **Advanced Logging and Monitoring**: Integrated enhanced logging features using Azure Monitor, allowing for more detailed tracking of model performance metrics and request-response times.
- **Custom Model Metrics**: Configured custom metrics for model evaluation, such as F1 score and precision, to ensure the model meets project-specific requirements.
- **Pipeline Optimization**: Implemented optimizations in the pipeline for faster runtime, such as caching intermediate steps and selecting a high-performance compute cluster.

These adjustments help improve model transparency, efficiency, and reliability in the production environment.


