# Azure DevOps CI/CD

A guide for implementing CI/CD using an Azure DevOps Pipeline and a GitHub repository.

## Getting Started
In order to use this Azure DevOps Pipeline example, you'll need:
- A GitHub repository
- An active Astronomer deployment
- A Service Account created in your Astronomer Deployment

### Setting up a DevOps CI/CD Pipeline

Either clone this repository, or use a new/existing Astronomer project. Create a new one using `astro dev init`  

If using your own project/directory, be sure to copy or add the [astro-devops-cicd.yaml](https://github.com/astronomer/cs-tutorial-azuredevops/blob/main/astro-devops-cicd.yaml) file found in this repository.  
**Notes on this YAML file:** 

- `Build.SourceVersion` is a pre-defined DevOps variable used to tag your builds and will populate the **Current Tag** value on your Astronomer Deployment UI screen.

For further information on CI/CD triggers, see:
- [Branch Triggers](https://docs.microsoft.com/en-us/azure/devops/pipelines/repos/github?view=azure-devops&tabs=yaml#branches)
- [PR Trigger](https://docs.microsoft.com/en-us/azure/devops/pipelines/yaml-schema?view=azure-devops&tabs=schema%2Cparameter-schema#pr-trigger)


In your DevOps portal, create a new pipeline. On the "Where is your code?" screen, select `GitHub YAML`.  
Your repositories will be listed here - select the repository you'd like to use this CI/CD pipeline with.  
![image](https://user-images.githubusercontent.com/15913202/150423746-75793597-012d-499e-bfc9-217562226f30.png)

Once you've selected your repository, on the next "Configure your pipeline" screen, select "Existing Azure Pipelines YAML file":  
![image](https://user-images.githubusercontent.com/15913202/150423772-10751454-7927-461d-8b87-71e70157ae38.png)


Choose the branch you'd like to use CI/CD with (in this example, `main`), as well as the path to the yaml file in the dropdown menu, then click **Save**.  
![image](https://user-images.githubusercontent.com/15913202/150423564-ad143e07-0820-44f7-a295-978fc8049ad6.png)  

On this same screen, click **Variables** in the top right corner. This is where you will be adding your`BASE-DOMAIN`, `RELEASE-NAME`, and `SVC-ACCT-KEY` values found in your yaml file.   
If you'd like these variables to be kept secret, be sure to select the **Keep this value secret** box.  
![image](https://user-images.githubusercontent.com/15913202/150423607-12043a01-c46f-457f-a921-ca6b3ac93f2b.png)

Your CI/CD pipeline is now ready to be used. Create a DAG or make a change in your repository, then create a Pull Request in GitHub. Once your changes are merged, your pipeline will be triggered and the build/deploy can be monitored in the DevOps Pipelines screen.   
![image](https://user-images.githubusercontent.com/15913202/150423691-882959d7-75b2-4463-b1bf-4168cad11ec9.png)

Once your pipeline succeeds and is deploying your changes to your Astronomer project, you can monitor the deployment status in the Astronomer UI:
![image](https://user-images.githubusercontent.com/15913202/150424236-df301c4f-fbee-459d-a153-2aaa3d66abe3.png)  

If successful, the Current Tag and Last Updated values will reflect the pipeline you just ran:
![image](https://user-images.githubusercontent.com/15913202/150424325-e0c7e746-8d19-41da-918d-f27de41d8231.png)
