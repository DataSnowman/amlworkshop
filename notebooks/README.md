# Running the MNIST Jupyter Notebooks

## MNIST Machine Learning Example

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



## MNIST Deep Learning Example

Navigate to the `<username>/amlworkshop/notebooks/MNIST/train-hyperparameter-tune-deploy-with-keras` directory

![dlNotebooks](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/dlNotebooks.png)



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