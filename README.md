# Apache Spark and Databricks Stream Processing in Lakehouse.
-An end to end data engineer project using ADLS, Databricks, Azure DevOps, Pyspark  and Python.

# Steps involved in the Project 
-Setting up all the services like  Storage account ,Databricks access connector, Azure ADLS, Databricks workspace in the cloud under single Resource group.

-Create a storage container for metastore-level managed storage,Create the metastore and attach a workspace.Also , create a group and assign a worspace to this group by also providing permission .Ready with unity catalog integrations.

-A metastore is the top-level container for catalog in Unity Catalog. Within a metastore, Unity Catalog provides a 3-level namespace for organizing data: catalogs, schemas (also called databases), and tables / views.

-Using the Databricks create the catalog for different environments (dev,prod,sit) and create the external locations which point unmanaged containers(storing data files).Also , grant the access to the user according to requirements(Azure Blob Contributor Role).We don't want managed and unmanaged data store in unity catalog so we create external locations.Creating a catalog in managed location.(dev)

-First create the project name and set configs in Azure Devops and clone the Azure Devops repository of my project in the Databricks repos folder and merge all the notebooks of local to my repos.

-Start coding first step is to create the DDL (02-setup) and required configuration in one place instead of hardcoding the values(01-config).

-Perform the history loader to load one time data in the tables(03-history-loader).

-Load the data from the landing zone to bronze layer(04-bronze).

- Follow the Medallion architecture for brz-slv-gld notebooks.

- Create the project name and set configs in Azure Devops and clone the Azure Devops repository of my project in the Databricks repos folder and merge all the notebooks of local to main branch.
 
# Build and Test
-Creating a CI/CD pipeline for my project integration.

-Creating build pipeline by first creating a yaml file(setting the configuration of yaml file in feature-build branch) and creating the artifact of my code.

-Now, create the pipeline in Azure DevOps using the yaml file in release branch the pipeline will run when we commit to release branch or create pull request for release branch.

-Creating release pipeline in the artifact add the required bash script install , python also. 

-The bash script consist of steps to create a job to run (08-batch-test) notebook from deployment folder, trigger the job and get run id,wait for job to complete while it's running , delete job after completion,publish the job result.

-In order to deploy code in QA workspace we require Databricks Workspace URL and Access Token for Authentication.

-In the devops pipeline add the databricks_host and databricks_token in environment variable.Hence, we created a release pipeline.

-So , my build pipeline is successful and artifact is ready for deployment.
