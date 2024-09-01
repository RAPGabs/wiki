---
id: buildanddeployment
title: Build & Deployment
---
## Basic Build & Deployment Info

We typically use Jenkins for all the builds and deployment , be it UI or our backend services. Internally the deployment takes place using Azure CLI.
We use Jenkins because it has an advantage of deploying to varios environments on a single click.
FYI, we maintain the following types of environments for all the implementations-

- Development
- Test
- UAT
- Production

For deployments on Dev and Test, the developer can simply do it by running the respective deployment pipeline, while for the rest, we need the QA's sign-off.Also all the deployments must be sourced from release branch of the respective service repository on GitLab.
Post succesfull deployment, the respective service owners like developers & QAs are notified.
All the deployments are done on Azure since all our services & UIs are deployed there as differet Azure resources. For these deployements, we need a jenkins.json file which is basically a configuration file for the respective service to be deployed. Please refer to the sample ``jenkins.json`` file below-
```
{
  "git_url": "https://git.cogitate.us/diep2/implementations/bnb/ui.git",
  "git_project_id": "469",
  "redmine_project_id": "359",
 
  
  "unit_test_project_path": "",
  "unit_test_project_name": "",
  
  "should_skip_automation_test": true,
  "automation_git_url": "",
  "should_skip_unit_test": true,
  "automation_branch": "",
  "automation_target_url": "",
  "automation_browser": "Chrome",
  "deploymentPath" :"C:\\jenkins\\workspace\\diep-UI\\out",
  "develop": {
    "target": "develop",
    "filePath": "https://ctsdiep2devstorage.blob.core.windows.net/$web/bnb",
	"mystorageccount": "ctsdiep2devstorage",
    "ContainerName": "$web/bnb"
  },
  "test": {
    "target": "test",
    "filePath": "https://ctsdiep2teststorage.blob.core.windows.net/$web/bnb",
	"mystorageccount": "ctsdiep2teststorage",
    "ContainerName": "$web/bnb"
  },
  "uat": {
    "target": "uat",
   "filePath": "https://ctsdiep2uatstorage.blob.core.windows.net/$web/bnb",
	"mystorageccount": "ctsdiep2uatstorage",
    "ContainerName": "$web/bnb"
  },
  "production": {
    "target": "production",
    "filePath": "https://ctsdiep2prodstorage.blob.core.windows.net/$web/bnb",
    "mystorageccount": "ctsdiep2prodstorage",
    "ContainerName": "$web/bnb"
  }
}


```

## Jenkins Pipelines

Jenkins Pipeline (or simply "Pipeline" with a capital "P") is a suite of plugins which supports implementing and integrating continuous delivery pipelines into Jenkins.

A continuous delivery (CD) pipeline is an automated expression of your process for getting software from version control right through to your users and customers. Every change to your software (committed in source control) goes through a complex process on its way to being released. This process involves building the software in a reliable and repeatable manner, as well as progressing the built software (called a "build") through multiple stages of testing and deployment.
Please have a look on the below sample pipeline for reference-

>![JenkinsSamplePipeline](../../static/img/docs/deployment/pipelinesample.png)

### References 
1. Cogitate Jenkins Platform- [https://jenkins.cogitate.us/login?from=%2F](https://jenkins.cogitate.us/login?from=%2F)


