## Sample Questions:

1. You need to create a Self-Hosted Build Agent. You already created the VM. What do you need to do first before you install the agent on the VM?
	* You need to install all the software required to build your application in the VM. The registration process checks for installed software before it registers the agent with Azure Pipelines.  

2. Which kind of functional testing is typically performed by humans, rather than through automation?
	* Usability Testing - Usability testing is typically performed by humans to validate that the software is intuitive and meets the user's needs.  

3. Your customer service team receives too many refund requests from customers who accidentally make purchases from your mobile application. Customers report that the Purchase button and Cancel button are too close together. Which kind of functional testing might help catch this sort of problem before it reaches your users?
	* Usability Testing - Usability testing helps you validate your application from the user's perspective. You can combine usability testing with user-acceptance testing to get feedback from real customers.  

4. Your user experience (UX) team proposed some drastic changes to your website's home page. Which kind of functional testing can you use to ensure that each button on the page performs the correct function?
	* UI Testing - UI tests help verify that the sequence, or order, of user interactions leads to the expected result.

5. You need to use Azure State Configuration. You already create the Azure Automation Account and the DSC script you need. What do you need to do next?
	* Upload the DSC script to the Azure Automation Account using the following command:
	```
	Import-AzAutomationDscConfiguration `
    -AutomationAccountName [your-automation-account-name] `
    -ResourceGroupName learn-decac6c7-6998-42ff-9e3d-48952ef394de `
    -SourcePath $HOME/MyDscConfiguration.ps1 `
    -Force `
    -Published
	```

6. You need to use Azure State Configuration. You already create the Azure Automation Account and the DSC script you need. Your DSC script require additional modules. What do you need to do next?
	* Add required Modules. Under your Azure Autoomation Account, go to Shared Resources > Modules. Select +Add a Module.

7. You need to use Azure State Configuration. You already have an Automation Account, you've created your DSC script and uploaded it to the Automation account, and compiled the configuration. What do you need to do next?
	* Register the VM with your Azure Automation account
	* Under your Automation Account go to **Configuration Management > State configuration (DSC) > Nodes (tab) >  click +Add > Select the VM then click +Connect**

8. You are an iOS developer for a mobile game app. You need to store diagnostics and analytics data for more than 90 days. What do you need to do?
 	* Use Azure Blog Storage or Application Insights. Currently, you can only configure data retention for diagnostics and analytics logs for 90 or 28 days.

9. You are a DevOps Engineer for a company called Contoso. You have an ARM template that requires access to secrets stored in Azure Key Vault. You have to ensure that the ARM template can access the secret using the least privilege principle.
	* Use Azure RBAC for Azure Key Vault.


## Things to look more into:
- Integrate Jenkins with Azure DevOps
- SonarQube & SonarCloud
- Code Analysis Tools (PMD and FindBugs)
