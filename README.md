# Azure_CICD_dot_net
1.	The very first step is to Install Terraform in your machine, by visiting the official site of Terraform. Here you need to download the binary file as per your Operating System.

Site Link: https://developer.hashicorp.com/terraform/downloads
 
![Picture1](https://github.com/chxtan/Azure_CICD_dot_net/assets/58957605/386b0fca-3549-4123-a7c4-05aca85dd15d)

2.	Unzip and copy the single executable file (terraform.exe) into a separate install directory (for example, inside c:\Terraform).

3.	Set the path environment variable with the path to the install directory.
•	Run the command sysdm.cpl and in the Advanced tab, click on Environment variables.
•	Scroll down in system variables until you find PATH and click edit.
•	Add the installation directory of Terraform (c:\Terraform).

4.	To Verify, if Terraform got installed.
 

5.	Install Azure CLI, for that go to Google and search for Download Azure CLI setup and install it.

Site Link: https://learn.microsoft.com/en-us/cli/azure/install-azure-cli-windows?tabs=azure-cli

 

6.	Now, login to Azure via CMD by running “az login”. It will take you to the browser to login.

 

7.	Now create the Azure SP.

 

This created Azure Service Principle; we will use it to setup the authenticate between Terraform and Azure.
8.	Now, make a directory in your local system and create a file named “main.tf” and write the script to create the resources.
9.	Where, we have written code to create resources like, Resource Group, App Service Plan, App Service.
10.	Also code to upload the .tfstate file to the Azure Storage Accuont.

 

11.	Now, after creating the terraform file, we will initiate it with the help of command
“terraform init”.

 

12.	Now, we will run the following command to check what is the plan of terraform with this code, going forward.
“terraform plan”.

 
 

13.	As, we can see it is planning to create three resources.
14.	Now, we will go ahead and create it, with the help of following command.
“terraform apply”

 
 
 
15.	We can see Apply has been completed and new resources has been deployed in the above screenshot. Let’s verify it by visiting the Azure Portal.

 

 

All the desired services have been created successfully.

16.	We will open the App Service that we have created. Now, we have to deploy our code.


 

17.	For that, we will go to “Deployment Center” and select the Code Source as “GitHub”. 

 

18.	Authenticate it with your GitHub account.
19.	Now, enter the Organization, Repository, Branch as per your requirements.

 

20.	We need to click on “Configure runtime”.

 

21.	Here, select the “Stack: .NET” and “.NET version: .NET 7 (STS)” and click on Save.

 

22.	Now, after saving check logs, it is in progress.

 

23.	From the logs, we can see it has been completed successfully.

 

 



24.	To check if your site is up, click on browse.

 































To Upload .tfstate file in Storage Account:

1.	Create a storage account, where you want to store the tfstate file. As, we have created in the below screenshot,

 

2.	Now, go inside the storage account and add a Container by clicking on “Containers” on LHS.

 

3.	Create a new container. As, I have created named “chxtan”.

 

4.	Now, add the below block to the terraform file.


backend "azurerm" { 
resource_group_name = "NAME_OF_RG" 
storage_account_name = "NAME_OF_STORAGE_TO_STORE" 
container_name = "NAME_OF_CONTAINER_TO_STORE" 
key = "deploy.tfstate" 
}

 

5.	It will save the tfstate file to the Storage Account along with the resource creation.

 


