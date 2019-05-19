# Setting up the Azure Machine Learning service Notebook VM

![Data Science with AML Notebook VMs 1](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/amlNotebookVMs1.png)

![Data Science with AML Notebook VMs 2](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/amlNotebookVMs2.png)

## Prerequisites

1) [Create](https://docs.microsoft.com/en-us/azure/machine-learning/service/setup-create-workspace) an Azure Machine Learning service workspace 

## Create an Azure Machine Learning service workspace in an Azure Resource Group using the Azure Portal

`Note if you already have an Azure Machine Learning service workspace that you created earlier you can just use it (no need to create another)`

Search for `Machine Learning service workspace` in the Azure Portal

![AMLserviceWorkspace](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/amlServiceWorkspace.png)

Click `Create`

![CreateAMLserviceWorkspace](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/createAMLserviceWorkspace.png)

File out parameters

Click `Create`

![CreateAMLserviceWorkspace2](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/createAMLserviceWorkspace2.png)

Click on the Machine Learning service workspace.  You should now see a new choice under Authoring.  Choose Notebook VMs

![amlServiceWorkspaceOverview](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/amlServiceWorkspaceOverview.png)

Click on +New

![amlNotebookVMsConsole](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/amlNotebookVMsConsole.png)

Enter an Name for the Notebook VM, choose a VM size, and click create

![amlNotebookVMsCreate](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/amlNotebookVMsCreate.png)

Notice how the status is `Creating`.  This is where you can go to Stop, Start, Restart, Delete, or Create Notebook VMs

![amlNotebookVMsConsole2](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/amlNotebookVMsConsole2.png)

After a few minutes the Status will change to `Running`.  Now you can click on the URI link `Jupyter`

![amlNotebookVMsConsole3](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/amlNotebookVMsConsole3.png)

This will open the Jupyter Notebook VM.  Navigate to your user folder. 

## Stop the Notebook VM

When you are done using the Notebook VM go back to the Notebook VMs console and click `Stop`.  You can return here to start it again, but this way you are not charged for compute while it is not being used.

![amlNotebookVMsConsole3Stop](https://raw.githubusercontent.com/DataSnowman/amlworkshop/master/images/amlNotebookVMsConsole3.png)