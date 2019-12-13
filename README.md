# Workshop Automated ML - Predict Wine Quality

In this case, you want to predict the quality of wine. We used a dataset from UCI Machine Learning repository that contained 6497 observations with physicochemical properties of red and white Portuguese wine and their quality (Cortez). You will use [Azure Machine Learning Automated ML service](https://docs.microsoft.com/en-us/azure/machine-learning/service/concept-automated-ml/?WT.mc_id=gaic-github-cxa).

## Steps

### Get the data

You can obtain the data 'winedata.csv' from the GitHub repo [Wine Quality](https://github.com/mdragt/WineQuality)

### Create an Azure Machine Learning instance

Go to [azure.microsoft.com](https://azure.microsoft.com/?WT.mc_id=gaic-github-cxa)

Sign in and open the Azure Portal (top right)

Select 'Create a resource'

Type 'Machine Learning' and 'Create' button

![Machine Learning in Azure Portal](docsimages/azure-portal-ml.PNG)

Enter details:
* **Workspace Name:** provide a name (ex: globalaibootcamp)
* **Subscription:** choose your azure subscription
* **Resource Group:** select new and provide a name (ex: globalaibootcamp)
* **Location:** choose a data centre closest to you
* **Workspace edition:** choose Enterprise in order to use the Automated ML UI

Select **'Review + Create'**
![Create Azure Machine Learning Service](docsimages/create-ml-service.PNG)

Once complete select 'Go to resource'

![Go to Resource once created](docsimages/resource-created.PNG)

Then select 'Launch the new Azure Machine Learning studio'

![Launch the new Azure Machine Learning studio](docsimages/ml-resource.PNG)

This will take you to a new browser window: [https://ml.azure.com/?WT.mc_id=gaic-github-cxa](https://ml.azure.com). Now you have created the Azure Machine Learning instance in the Azure Portal once you can navigate directly to [https://ml.azure.com/?WT.mc_id=gaic-github-cxa](https://ml.azure.com) when you are using the studio.


Go to Datasets and select Create dataset, from local file.

![Create dataset](docsimages/createDataset.png)

#### Basic Info

Select the winedata.csv file.

![Select dataset](docsimages/importData.png)

Click on Next.

#### Settings and Preview

Now you have the option to change the settings, but in this case this is not neccesary.

![Settings of the dataset](docsimages/settingsData.png)

Click on Next.

#### Schema

The next step is to look at the schema of the data. Here we can change the data types, and deselect columns we don't want in our dataset. In this case, we deselect "quality", which is a numeric value of the wine quality. In this case, we want to predict whether the wine is good or bad, for which we will use the dependent variable "qual_bool".

![Schema dataset](docsimages/schemaData.png)

Click on Next.

#### Confirm Details

Finally, you have the option to profile your data, which gives you a generic overview of your data. Therefore, you would need a compute with at least 1 node.
To create the dataset, click on Create.

![Confirm dataset](docsimages/finalCreateDataset.png)

### Create Experiment

You are now ready to create a new experiment. Go to Automated ML in the left menu, and select New automated ML run.

![Create ML Run](docsimages/createMLRun.png)

#### Select dataset

Select the prior created dataset and click on Next.

![Select dataset](docsimages/selectDataset.png)

Fill out the details to create the experiment:

* Experiment name: any name you want
* Target column: the dependent variable of your dataset, in our case "qual_bool"
* Select training compute target: the compute you want to use for this experiment

Click on Next.

![Experiment settings](docsimages/experimentSettings.png)

#### Configure Run

In this step you can configure the ML run. By default, Classification was selected as task, which is ok. Now click on View additional configuration settings. Here you can select things like:

* Primary metric: define on which metric you want to train the model
* Training job time (in hours): the amount of hours to train the model
* Metric score threshold: minimim metric value that should be reached. I.e. you could be happy with 90% accuracy.
* etc.

Click on OK, and furthermore on Create.

![Configure run](docsimages/configureRun.png)

The ML run will now be prepared.

![Prepare run](docsimages/preparingRUn.png)

During the run, you get an overview of how well the models are performing:

![Running models](docsimages/runningModels.png)

The running process can take quite a while (remember, we defined 1 hour as possible running time), so take a coffee and go to the next workshop.

When the running process is finished, you have the option to deploy the best model.

## Clean up resources
Finally, If you don't expect to need these resources in the future and want to save cost, you can delete them by deleting the resource group you created. To do so go to the Azure Portal, select 'Resource Groups' and select the resource group for this workshop, select Delete, then confirm the name of the resource group to delete.

Looking for another example to continue your learning - check out another [tutorial here](https://docs.microsoft.com/en-us/azure/machine-learning/service/tutorial-auto-train-models/?WT.mc_id=gaic-github-cxa)
