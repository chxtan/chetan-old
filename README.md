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
 
![Picture2](https://github.com/chxtan/chetan-old/assets/58957605/f18c7af8-187d-4afa-8132-1e9d408a42b7)

5.	Install Azure CLI, for that go to Google and search for Download Azure CLI setup and install it.

Site Link: https://learn.microsoft.com/en-us/cli/azure/install-azure-cli-windows?tabs=azure-cli

 ![Picture3](https://github.com/chxtan/chetan-old/assets/58957605/d35a044a-e04e-4b66-9feb-2d31225ff768)


6.	Now, login to Azure via CMD by running “az login”. It will take you to the browser to login.

 ![Picture4](https://github.com/chxtan/chetan-old/assets/58957605/440f4aa7-11f6-478b-829a-2e8bb2820f94)


7.	Now create the Azure SP.

![5 1](https://github.com/chxtan/chetan-old/assets/58957605/6e406073-bb7d-4f76-bca4-cac85fd460a6)



This created Azure Service Principle; we will use it to setup the authentication between Terraform and Azure.

8.	Now, make a directory in your local system and create a file named “main.tf” and write the script to create the resources.

9.	Where, we have written code to create resources like Resource Group, App Service Plan, and App Service.

10.	Also code to upload the .tfstate file to the Azure Storage Account.

 ![6 1](https://github.com/chxtan/chetan-old/assets/58957605/be64222a-814f-4737-9728-6ad6473b507f)


11.	Now, after creating the terraform file, we will initiate it with the help of the command
“terraform init”.

 ![Picture7](https://github.com/chxtan/chetan-old/assets/58957605/e1d387ad-b678-4922-913e-850a263de76f)


12.	Now, we will run the following command to check what is the plan of terraform with this code, going forward.
“terraform plan”.

 ![Picture8](https://github.com/chxtan/chetan-old/assets/58957605/13e85ed7-cd58-4567-bcdb-f14f166e1a60)
 ![Picture9](https://github.com/chxtan/chetan-old/assets/58957605/9a700b94-14ba-4c9d-bb12-356ee196e966)


13.	As, we can see it is planning to create three resources.
14.	Now, we will go ahead and create it, with the help of following command.
“terraform apply”
 
 ![Picture10](https://github.com/chxtan/chetan-old/assets/58957605/4f412824-6e8e-46f7-bb30-612d4cafcbab)
 ![Picture11](https://github.com/chxtan/chetan-old/assets/58957605/d68286e9-5ad2-49ac-a9ec-457f1eedfef5)

15.	We can see Apply has been completed and new resources has been deployed in the above screenshot. Let’s verify it by visiting the Azure Portal.

 ![Picture12](https://github.com/chxtan/chetan-old/assets/58957605/05b29ce0-cb8e-477a-9e56-4ba81486c0f6)
![Picture13](https://github.com/chxtan/chetan-old/assets/58957605/664e3157-236e-45cd-8bc6-aed4167579c1)

 
All the desired services have been created successfully.

16.	We will open the App Service that we have created. Now, we have to deploy our code.

![Picture14](https://github.com/chxtan/chetan-old/assets/58957605/c40c802b-96da-4422-b3e2-670b28f50d63)

17.	For that, we will go to “Deployment Center” and select the Code Source as “GitHub”. 

 ![Picture15](https://github.com/chxtan/chetan-old/assets/58957605/bcb869fa-2761-4d0a-88e2-0db0a0b91c64)


18.	Authenticate it with your GitHub account.
19.	Now, enter the Organization, Repository, Branch as per your requirements.

 ![Picture16](https://github.com/chxtan/chetan-old/assets/58957605/3320d6d2-aa1d-41c2-aec5-838bceb2289b)


20.	We need to click on “Configure runtime”.

 ![Picture17](https://github.com/chxtan/chetan-old/assets/58957605/17a29b0f-1aaf-47ac-a1b8-98c3618f388d)


21.	Here, select the “Stack: .NET” and “.NET version: .NET 7 (STS)” and click on Save.

 ![Picture18](https://github.com/chxtan/chetan-old/assets/58957605/85fb87ca-fdcf-41d8-af74-2d72fffc9980)


22.	Now, after saving check logs, it is in progress.

 ![Picture19](https://github.com/chxtan/chetan-old/assets/58957605/2020f9e1-16a3-4fe6-9645-5eeb955db400)


23.	From the logs, we can see it has been completed successfully.

![Picture20](https://github.com/chxtan/chetan-old/assets/58957605/9f7ee2d5-a250-45ec-983f-48307b98d701)
![Picture21](https://github.com/chxtan/chetan-old/assets/58957605/07e10d50-aeb2-46d6-90fb-cee0f6924110)


24.	To check if your site is up, click on browse.

 ![Picture22](https://github.com/chxtan/chetan-old/assets/58957605/2090d35e-6628-45a8-bf4f-6671c77f9165)


===========================================================================================================


To Upload .tfstate file in Storage Account:

1.	Create a storage account, where you want to store the tfstate file. As, we have created in the below screenshot,

 ![Picture23](https://github.com/chxtan/chetan-old/assets/58957605/97387751-a498-4fad-956a-f747fc25d25b)


2.	Now, go inside the storage account and add a Container by clicking on “Containers” on LHS.

 ![Picture24](https://github.com/chxtan/chetan-old/assets/58957605/bffc6086-4145-4df9-ab60-7ae86a35ae24)


3.	Create a new container. As, I have created named “chxtan”.

 ![Picture25](https://github.com/chxtan/chetan-old/assets/58957605/a4d5844f-a238-4fe2-9463-edc8a4a5d360)


4.	Now, add the below block to the terraform file.


backend "azurerm" { 
resource_group_name = "NAME_OF_RG" 
storage_account_name = "NAME_OF_STORAGE_TO_STORE" 
container_name = "NAME_OF_CONTAINER_TO_STORE" 
key = "deploy.tfstate" 
}

 ![Picture26](https://github.com/chxtan/chetan-old/assets/58957605/5d825b63-8960-45df-b229-50685e1b4ae3)


5.	It will save the tfstate file to the Storage Account along with the resource creation.

![Picture27](https://github.com/chxtan/chetan-old/assets/58957605/e6dad45c-aa95-4466-8543-e6e583f4c631)


