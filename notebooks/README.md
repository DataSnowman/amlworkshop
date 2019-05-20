# Running the MNIST Jupyter Notebooks

## MNIST Machine Learning Example

### Tutorial #1: Train an image classification model with Azure Machine Learning

Navigate to the `<username>/amlworkshop/notebooks/MNIST/scikit-learn` directory

![scikit-learnNotebooks](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/scikit-learnNotebooks.png)

Open up `img-classification-part1-training.ipynb`

Run the `Import packages` and `Connect to workspace` cells

![connectToWorkspace](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/connectToWorkspace.png)

Click on `https://microsoft.com/devicelogin` in the notebook and enter the code in the browser

![enterCode](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/enterCode.png)

Pick the account you want to login with

![pickAnAccount](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/pickAnAccount.png)

You should have now authenticated successfully back in the notebook

![authentication](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/authentication.png)

Run the next to cells to Create and Experiment and Azure Machine Learning Compute

![createExpAndCompute](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/createExpAndCompute.png)

Once you run these cells you should have Experiment and Compute Assets created in the AML server workspace

![experiment](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/experiment.png)

![compute](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/compute.png)

Now you can try to run all of the cells remaining by selecting the cell below `Download the MNIST dataset` and clicking on Cell and choosing `Run All Below`

![runAllBelow](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/runAllBelow.png)

If you issues with the Create an estimator cell you might need to define the compute target to one of your compute assets like `compute_target='default-compute',` vs `compute_target=compute_target`,

![createAnEstimator](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/createAnEstimator.png)

It could take 10 minutes or so for the model to run

![runTime](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/runTime.png)

The last cell should register the model

![registerModel](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/registerModel.png)

This is where to find the model in the Assets in the AML service workspace in the Azure Portal

![model](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/model.png)


### Tutorial #2: Deploy an image classification model in Azure Container Instance (ACI)

Feel free to skip the first cell if you completed the Tutorial #1 training tutorial 

Run each of the notebook cells individually.

It takes several minutes to deploy in an Azure Container Instance (ACI).  Don't run the last cell until the end after you have looked at the Images and Deployments.

![aci](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/aci.png)

Once deployed the ACI should show up as an Asset in Images

![images](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/images.png)

It should also show up in Deployments

![deployments](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/deployments.png)

Once you are finished looking at the notebook please run the last cell to delete the ACI deployment (which is the part that costs to keep running)

`service.delete()`

![cleanupResources](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/cleanupResources.png)

Once you run the command the Deployments should showup blank since the deployment was deleted

![deleteDeployment](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/deleteDeployment.png)

Great Job.  Now you can run MNIST using Deep Learning

## MNIST Deep Learning Example

Check out your [Azure Machine Learning Compute quota](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-manage-quotas#find-your-quotas) 

![usageQuotas](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/usageQuotas.png)

Create Azure ML Compute

`gpucluster` STANDARD_NC6, 0 to 1 nodes

Navigate to to Compute Assets in the AML service Workspace in the Azure Portal.  Click on `Add Compute`

![addCompute](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/addCompute.png)

Computer name: `gpucluster`

Compute type: `Machine Learning Compute`

Region: `Southeast Asia` or other region appropriate for you where you have NC series resources

Virtual machine size: `Standard_NC6`

Virtual machine priority: `Dedicated`

Minimum number of nodes: `0`

Maximum number of nodes: `1`

Idle seconds before scale down: `120`

Click `Create`

![gpuCompute](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/gpuCompute.png)

Navigate to the `<username>/amlworkshop/notebooks/MNIST/train-hyperparameter-tune-deploy-with-tensorflow` directory

![dlNotebooks](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/dlNotebooks.png)

Open up `train-hyperparameter-tune-deploy-with-tensorflow.ipynb`

Run all of the cells individually

The `Monitor the Run` cell will update as the job progresses with phases like queued, preparing, running

![queued](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/queued.png)

![preparing](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/preparing.png)

![running](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/running.png)

And eventually complete

![complete](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/complete.png)

When you run the `Download the saved model` cell 

![downloadModel](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/downloadModel.png)

It will download the Model into a model directory in Jupyter

![modelJupyter](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/modelJupyter.png)

The Hyperparameter Tuning is interesting

![hyperparameterTuning](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/hyperparameterTuning.png)

![hyperparameterTuning2](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/hyperparameterTuning2.png)

![hyperparameterTuning3](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/hyperparameterTuning3.png)

Deploy the model to ACI

![acitf.png](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/acitf.png)

Once you are finished looking at the notebook please run the last cell to delete the ACI deployment (which is the part that costs to keep running)

`service.delete()`

![cleanupResources](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/cleanupResources.png)

Once you run the command the Deployments should showup blank since the deployment was deleted

![deleteDeployment](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/deleteDeployment.png)

Great Job, more resources below.

## More Learning Opportunities using the Azure Machine Learning service

**For additional learning please try below content:**

[Build 2019 updates](https://azure.microsoft.com/en-us/blog/new-azure-machine-learning-updates-simplify-and-accelerate-the-ml-lifecycle/): New Azure Machine Learning updates simplify and accelerate the ML lifecycle

[Visual-interface (preview)](https://docs.microsoft.com/en-us/azure/machine-learning/service/ui-tutorial-automobile-price-train-score)

[Automated ml with GUI (preview)](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-create-portal-experiments)

[interpretability-explainability](https://docs.microsoft.com/en-us/azure/machine-learning/service/machine-learning-interpretability-explainability)

[onnx](https://docs.microsoft.com/en-us/azure/machine-learning/service/concept-onnx)

[fpga](https://docs.microsoft.com/en-us/azure/machine-learning/service/concept-accelerate-with-fpgas)

[pipelines](https://docs.microsoft.com/en-us/azure/machine-learning/service/concept-ml-pipelines)

[security](https://docs.microsoft.com/en-us/azure/machine-learning/service/concept-enterprise-security)

[custom vision](https://customvision.ai)

### Running AML SDK on Azure Databricks

Set up Azure Databricks using this [guide](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-configure-environment#azure-databricks)

Create a cluster, and import the [sample notebook](https://github.com/Azure/MachineLearningNotebooks/blob/master/how-to-use-azureml/azure-databricks/Databricks_AMLSDK_1-4_6.dbc).

Install `azureml-sdk[automl_databricks]` if needed.

Run samples.
    
* For Automated ML sample, set `max_concurrent_iterations` to the number of worker nodes.

### Machind Learning Ops: Manage, deploy, and monitor models with Azure Machine Learning Service

Check out [MLOps](https://docs.microsoft.com/en-us/azure/machine-learning/service/concept-model-management-and-deployment)


Hope you enjoyed this workshop.