# Azure Machine Learning Service Workshop
> AML Notebook VMs Hands on workshop

## Agenda

### Deep Learing Track
- **Dev environment setup: Azure ML service Workspace and Azure Notebooks, authenticate, prepare compute (Azure ML Compute)**

    1. [Create an AML service workspace](https://docs.microsoft.com/en-us/azure/machine-learning/service/setup-create-workspace)
        - region: Southeast Asia
        - resource group: new (one per person for practice)
        - after creation, check `Usage + quotas`, Standard NC Family vCPUs: should have 100+ available dedicated cores for this workshop (e.g., 5 people * 6 cores * 4 nodes = 120 cores)

    1. From Azure ML service Workspace `Overview` tab, click `Download config.json`, save locally.
    1. Set up Notebook environment. In this workshop, use Option 1 to practice.
        - Using Notebook VMs from Azure ML service Workspace
            - go to `Notebook VMs`, create a new VM (STANDARD_D3_V2)
            - Click `Jupyter`, click `Terminal`
            - From the current directory `/mnt/azmnt/code/Users/`, cd <USERNAME> (or mkdir if needed), git clone with `git clone https://github.com/Azure/MachineLearningNotebooks`
            ![](https://raw.githubusercontent.com/dem108/AMLWorkshop-IotEdge-DevOps/master/doc/images/setup-notebook-vm-jupyterlab-gitclone.jpg)
            - Note that the config.json is already automatically added to `/mnt/azmnt/`, you do ***not*** need to upload it manually.
            - From `Notebook VMs`, click `Jupyter`, and you can run notebooks there
            ![](https://raw.githubusercontent.com/dem108/AMLWorkshop-IotEdge-DevOps/master/doc/images/setup-notebook-vm-jupyter-notebook.jpg)

    1. Create Azure ML Compute: To do that, open `configuration.ipynb`

        - Skip creating config.json, because you already have it
        - Instead, add a cell and run following script to load the config.json and authenticate.
            ```python
            from azureml.core import Workspace
            ws = Workspace.from_config()
            ```
            ![](https://raw.githubusercontent.com/dem108/AMLWorkshop-IotEdge-DevOps/master/doc/images/authenticate-workspace.jpg))
        - Proceed to create Azure ML Compute
            - `cpucluster` STANDARD_D2_V3, 0 to 4 nodes
            - `gpucluster` STANDARD_NC6, 0 to 4 nodes

- **Train first DL model on Azure Notebooks using Azure ML Compute**

    1. Open sample notebook `train-hyperparameter-tune-deploy-with-keras.ipynb` under `how-to-use-azureml/training-with-deep-learning/train-hyperparameter-tune-deploy-with-keras` (find [this notebook](https://github.com/Azure/MachineLearningNotebooks/blob/master/how-to-use-azureml/training-with-deep-learning/train-hyperparameter-tune-deploy-with-keras/train-hyperparameter-tune-deploy-with-keras.ipynb) from your notebook environment)
    1. Run (before `run.wait_for_complettion()` cell)
    1. Monitor the Jupyter widget, and the Workspace (from Azure Portal - check Experiment and Compute)
    1. Additionally, note that files in `./outputs` and `./logs` are automatically uploaded to the Workspace. Tensorboard logs should also be saved in this `./logs`. Refer to [how to train models](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-train-ml-models#single-node-training) and [TensorBoard integration sample](https://github.com/Azure/MachineLearningNotebooks/blob/master/how-to-use-azureml/training-with-deep-learning/tensorboard/tensorboard.ipynb).
    1. Try to understand how the model files are moving, from AML Compute, to Workspace, to local environment.
    1. Continue running the notebook and try hyperparameter tuning.
        - Set `max_concurrent_job` parameter to the maximum number of nodes in your Azure ML Compute cluster.
        - Run, monitor the Jupyter widget and Azure Portal (AML service Workspace), evaluate the results
            > Note: Generally when you open the Notebook, you can see the last run results of the code cells, but Jupyter widget results are not shown. So in order to review last Widget run status without running the experiment again, you should find and load the run before using the widget. Sample notebook to do this is [here](https://github.com/dem108/AMLWorkshop-IotEdge-DevOps/blob/master/notebooks/Check-Jupyter-widget-for-a-specific-run.ipynb). 
    1. Stop here. You may continue and deploy to ACI from this notebook, but we will cover deployment in the afternoon.

- **Create container images, deploy to Azure Container Instance (and/or Azure Kubernetes Service)**

    1. We will continue from morning's sample, `train-hyperparameter-tune-deploy-with-keras.ipynb`. Open the notebook, and run the latter part, creating container image and deploying to ACI.
    1. Explore Workspace from Azure Portal.
    1. Refresh the concepts of MLOps from [concept-model-management-and-deployment](https://docs.microsoft.com/en-us/azure/machine-learning/service/concept-model-management-and-deployment)

  **For additional learning please try below content:**

        - [Build 2019 updates](https://azure.microsoft.com/en-us/blog/new-azure-machine-learning-updates-simplify-and-accelerate-the-ml-lifecycle/): New Azure Machine Learning updates simplify and accelerate the ML lifecycle
        - [visual-interface (preview)](https://docs.microsoft.com/en-us/azure/machine-learning/service/ui-tutorial-automobile-price-train-score)
        - [automated ml with GUI (preview)](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-create-portal-experiments)
        - [interpretability-explainability](https://docs.microsoft.com/en-us/azure/machine-learning/service/machine-learning-interpretability-explainability)
        - [onnx](https://docs.microsoft.com/en-us/azure/machine-learning/service/concept-onnx)
        - [fpga](https://docs.microsoft.com/en-us/azure/machine-learning/service/concept-accelerate-with-fpgas)
        - [pipelines](https://docs.microsoft.com/en-us/azure/machine-learning/service/concept-ml-pipelines)
        - [security](https://docs.microsoft.com/en-us/azure/machine-learning/service/concept-enterprise-security)
        - [custom vision](https://customvision.ai)

    * Running AML SDK on Azure Databricks
        - Set up Azure Databricks using this [guide](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-configure-environment#azure-databricks)
        - Create a cluster, and import the [sample notebook](https://github.com/Azure/MachineLearningNotebooks/blob/master/how-to-use-azureml/azure-databricks/Databricks_AMLSDK_1-4_6.dbc).
        - Install `azureml-sdk[automl_databricks]` if needed.
        - Run samples.
            - For Automated ML sample, set `max_concurrent_iterations` to the number of worker nodes.

    * And check out [MLOps](https://docs.microsoft.com/en-us/azure/machine-learning/service/concept-model-management-and-deployment). This will be covered in Day 3, but will be good if we can get familiar with key concepts earlier.