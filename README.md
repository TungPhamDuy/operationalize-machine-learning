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
The dataset was successfully registered to ensure it can be easily accessed and reused throughout the AutoML process. This step is crucial for maintaining data version control and making the dataset available across different experiments and models within Azure ML.
![01_registered_dataset.png](/images/01_registered_dataset.png)

#### Completed AutoML Experiment
This image shows that the AutoML experiment has completed successfully. Completing this step allows us to automatically test multiple machine learning models and hyperparameters, optimizing performance without manually tuning each parameter.
![02.1_completed_automl_experiment.png](/images/02.1_completed_automl_experiment.png)
![02.1_completed_automl_experiment_2.png](/images/02.1_completed_automl_experiment_2.png)

#### Best Model
The best-performing model, Voting Ensemble, was selected from the AutoML experiment. This model was chosen based on AUC weighted that indicate it outperformed others.
![02.2_best_model.png](/images/02.2_best_model.png)
![02.3_best_model.png](/images/02.3_best_model.png)

#### Deploy the Model
The best model (Voting Ensemble) was deployed using Azure Container Instance (ACI) with authentication enabled to ensure secure access. This deployment step enables real-time predictions by creating an endpoint that applications can call.
![03_deloy_the_model.png](/images/03_deloy_the_model.png)

#### Enable Logging
Application Insights was enabled to track and log model usage, which is essential for monitoring model performance and debugging issues. Additionally, a logging script was executed to confirm that logging was correctly set up.
![04.1_run_logs_file.png](/images/04.1_run_logs_file.png)
![04.1_run_logs_file_2.png](/images/04.1_run_logs_file_2.png)

#### Application Insights Enabled
This screenshot confirms that Application Insights is running, ensuring continuous tracking of the model’s health and usage statistics.
![04.2_application_insight_running.png](/images/04.2_application_insight_running.png)

#### Swagger Documentation
Swagger documentation was configured to facilitate the consumption of the model’s API. The `swagger.json` file was downloaded, and the Swagger interface was launched, providing interactive API documentation for testing model requests and responses.
![05_swagger_page.png](/images/05_swagger_page.png)

#### Consume Model Endpoints
The `endpoint.py` script was updated with the `scoring_uri` and authentication key to enable interaction with the deployed model. This step makes it possible to perform inference by sending requests to the model endpoint.
![06.1_interact_with_endpoint.png](/images/06.1_interact_with_endpoint.png)

#### Benchmark
The `benchmark.sh` script was executed to evaluate the model's performance under simulated load. This process uses Apache Benchmark to test response times and reliability, ensuring the model can handle real-world traffic and requests efficiently.
![06.2_benchmark_run.png](/images/06.2_benchmark_run.png)

#### Create and Publish a Pipeline
A pipeline was created, published, and configured within a Jupyter notebook to automate the workflow for dataset handling and model training. This pipeline supports automation, making data flows and model training repeatable, reliable, and manageable.
![07.7_pipeline_in_job_section_with_completed_status.png](/images/07.7_pipeline_in_job_section_with_completed_status.png)
![07.1_completed_pipeline_experiment.png](/images/07.1_completed_pipeline_experiment.png)

#### Pipeline Status and REST Endpoint
The pipeline is shown as active, and a REST endpoint has been created. This setup allows for easy access to the pipeline through API calls, making it possible to trigger the pipeline programmatically.
![07.2_pipeline_endpoint_active.png](/images/07.2_pipeline_endpoint_active.png)
![07.6_pipeline_active_page.png](/images/07.6_pipeline_active_page.png)

#### Dataset and AutoML in Pipeline
This image displays the dataset and AutoML model integrated into the pipeline, which confirms that the end-to-end process of data preparation and model training is fully automated within Azure ML.
![07.3_dataset_and_automl_in_pipeline.png](/images/07.3_dataset_and_automl_in_pipeline.png)

#### DetailRun Widget in notebook
The DetailRun Widget provides a comprehensive view of the pipeline run’s status and progress in the notebook, allowing us to monitor execution details in real-time.
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


