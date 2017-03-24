
**Azure Deployment Template for multiple virtual machines**
-------------------------------------------------------

This ARM template for Viusal Studio 2015 supports deploying multiple azure virtual machines at once. Additionally features like multiple harddisks can be added and harddisk size can be chosen. The ARM template parameters default values can be updated via included powershell scripts. Deployment is executed just as a normal arm deployment.




Project structure
-------------

The project consists of three powershell scripts, the json deployment file and the deployment parameter file.

 **azuredeploy.json**

Standard json deployment file, containing the json strucure of the azure resource to deploy. The parameters "Image" and "VirtualComputerSize" can be updated by running the addition script "Update-AzureParameters.ps1" (see description below).

 **azuredeploy.parameters.json**

The parameters file containing values from last saved deployment.

**Deploy-AzureResourceGroup.ps1**

The powershell script running the deployment. Creates all needed resources for the deployment. Executes jobs for each virtual machine deployment, so dployment of multiple virtual machines runs parallel.

**Create-VirtualMachine.ps1**

Powershell script runing the deployment of the virtual machines. Is executeted in jobs created by Deploy-AzureResourceGroup.ps1.

**Update-AzureParameters.ps1**

Powershell script to update skus ("Images") and hardware configuration ("VirtualComputerSize") parameters. Execute after microsoft announced changes. You are promted to login with your azure account.

**VmList.txt**

If you want to deploy more than one virtual machine, write down the name of each machine into a single line. The virtual machine name parameter is discarded, when deploying multiple virtual machines.


