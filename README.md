# Scheduled Shutdown and Startup using Azure Tags and Azure Automation
 
This script is used to automate the shutdown and startup of virtual machines in Azure based on their tags.

The script starts by connecting to Azure using the `Connect-AzAccount` cmdlet and managed identity, which provides the necessary authentication and authorization to access the Azure resources.

Next, it gets all virtual machines that have a `ShutdownTime` tag and `StartTime` tag using the `Get-AzVM` cmdlet and `Where-Object` cmdlet.

For each virtual machine, the script checks the value of the `ShutdownTime` tag and compares it with the current time. If the difference is less than or equal to 80 minutes and greater than or equal to zero, the script shuts down the virtual machine using the `Stop-AzVM` cmdlet.

Similarly, for each virtual machine, the script checks the value of the `StartTime` tag and compares it with the current time. If the difference is less than or equal to 60 minutes and greater than or equal to zero, the script starts up the virtual machine using the `Start-AzVM` cmdlet.

Finally, the script outputs a message to indicate the action taken on each virtual machine.

## Azure Automation Account Setup with Managed Identity

To run this script in an Azure Automation account using a managed identity, you need to follow these steps:

1.  Create an Azure Automation account in your subscription.
    
2.  Enable the managed identity for the Azure Automation account.
    
3.  Assign a role to the managed identity to access the virtual machines.
    
4.  Create a runbook in the Azure Automation account and copy the script.
    
5.  Schedule the runbook to run on whatever schedule you need.
    
6.  Save and publish the runbook.

or refer to [https://learn.microsoft.com/en-us/azure/automation/enable-managed-identity-for-automation]
