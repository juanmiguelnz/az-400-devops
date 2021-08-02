## Continuous Integration  
The process of automating the build and testing of code every time a team member commits changes to version control.

Concurrent Pipelines (aka Parallel Jobs)  
Lets you run a single build or release job at any give time. Purchased at the organization level. Shared by all projects in the organization.

## Microsoft-hosted vs Self-hosted 
[More info here](https://docs.microsoft.com/en-us/azure/devops/pipelines/agents/hosted?view=azure-devops&tabs=yaml)

* Microsoft-hosted
	* Less administrative overhead
	* Has a fixed disk space
	* You can't sign in to a Hosted Agent
	* You can't drop build artifacts to UNC file shares
* Self-hosted
	* Hosted Agents share resources with other Azure DevOps customers. Use Self-Hosted if you want to minimize latency.
	* You have to maintain the Build Agent yourself.
	* Use Self-Hosted if you want to perform incremental builds. Incremental builds take less time to complete because the system already has the build tools and dependent components installed.

## Functional Tests  
Verifies that each function of the software does what it should. How the software implements each function isn't important in these tests. What's important is that the software behaves correctly. You provide an input and check that the output is what you expect.

* Smoke Testing - Verifies the most basic functionality of your application or service. These tests are often run before more complete and exhaustive tests. Smoke tests should run quickly.
* Unit Testing - Verifies the most fundamental components of your program or library, such as an individual function or method.  
	** Code Coverage - Computes the percentage of your code that's covered by your unit tests.
* Intergration Testing - Verifies that multiple software components work together to form a complete system. For example, an e-commerce system might include a website, a products database, and a payment system. You might write an integration test that adds items to the shopping cart and then purchases the items. The test verifies that the web application can connect to the products database and then fulfill the order.
* Regression Testing - A regression occurs when existing behavior either changes or breaks after you add or change a feature. Regression testing helps determine whether code, configuration, or other changes affect the software's overall behavior.
* User interface Testing - Verifies the behavior of an application's user interface. UI tests help verify that the sequence, or order, of user interactions leads to the expected result.
* Usability Testing - A form of manual testing that verifies an application's behavior from the user's perspective. Usability testing is typically done by the team that builds the software.
* User Acceptance Testing - like usability testing, focuses on an application's behavior from the user's perspective. Unlike usability testing, UAT is typically done by real end users.  

## Nonfunctional Tests
* Checks characteristics like performance and reliability. An example of a nonfunctional test is checking to see how many people can sign in to the app simultaneously. Load testing is another example of a nonfunctional test.  

* Automated Testing - Uses software to execute your code and compare the actual results with the results you expect.
* Lint Testing - A form of static code analysis, checks your code to determine whether it conforms to your team's style guide.

## What is a package?
* A package contains reusable code that other developers can use in their own project.
* Typically contains the compiled binary code (ex. .dll for .NET or .class for Java).
* For language that are interpreted instead of compiled (ex. JavaScript or Python), a package might include source code.

## Semantic Versioning ( Major.Minor.Patch[-Suffix] )

* Major - Introduces breaking changes. Apps typically need to update how they use the package to work with a new major version. 
* Minor - Introduces new features but is backward compatible with earlier versions.
* Patch - Introduces backward compatible bug fixes but not new features.
* -Suffix - identifies the package as a pre-release (ex. 1.0.0-beta1)

Azure Artifacts
- A repository in Azure DevOps where you can manage the dependencies for you codebase.
- Stores artifacts and binaries.

Security Scanning
- During the build process, you can integrate external tools that scans the packages and gives feedback. During the CD process, the tool uses the build artifacts and performs scans (Ex. WhiteSource Bolt and Black Duck).

## Azure Pipeline  
* Trigger - tells the Pipeline to run
* Pipeline - made up of ***one or more Stages***. A Pipeline can deploy to ***one or more Environments***.
* Stage - a way of organizing Jobs in a Pipeline. Each Stage can have ***one or more Jobs***.
* Job - runs on one Agent. A Job can also be Agentless.
* Agent - runs a Job that ***contains one or more Steps***.
* Step - can be ***a Task or a Script*** and is the smallest building block of a Pipeline.
* Task - a ***pre-packaged script*** that performs an action.
* Artifact - a collection of files and packages ***published by a Run***.
* Run - represents one execution of a Pipeline.

# PowerShell DSC  
Declarative Management Platform used by Azure Automation State Configuration.

## Azure Automation State Configuration  
* Has a built-in pull server. You can target nodes to automatically receive configurations from this pull server, conform to the desired state, and report back on their compliance. Target virtual or physical Windows or Linux machines, in the cloud or on-premises.  

* You can configure Azure Automation State Configuration to send data to Azure Monitor Logs so you can review compliance of the Nodes.

## Local Configuration Manager (LCM)  
* A component of the Windows Management Framework that's on a Windows Operating System
* Responsible for updating the state of a node, like a VM, to match the desired state

## Push and Pull Architecture in DSC
* Push Mode  
	* An administrator manually sends, or pushes, the configurations toward one or more nodes. The LCM makes sure that the state on each node matches what the configuration specifies.
	* Easy to set up. It doesn't need its own dedicated infrastructure, and it can run on a laptop. Push mode is helpful to test the functionality of DSC. You could also use push mode to get a newly imaged machine to the baseline desired state.  

* Pull Mode
	* A pull server holds the configuration information. The LCM on each node polls the pull server at regular intervals, by default every 15 minutes, to get the latest configuration details.
	* Useful in an enterprise deployment that spans a large number of machines. The LCM regularly polls the pull server and makes sure the nodes are in the desired state. If an external tool or team applies hotfixes that result in configuration drift on individual machines, those machines are quickly brought back in line with the configuration you've set. This process can help you achieve a state of continuous compliance for your security and regulatory obligations.

## Enable an ARM Virtual Machine for management with State Configuration  
1. Create an Azure Automation Account
2. Create a DSC Configuration  
Example: TestConfig.ps1
```
configuration TestConfig
{
    Node IsWebServer
    {
        WindowsFeature IIS
        {
            Ensure               = 'Present'
            Name                 = 'Web-Server'
            IncludeAllSubFeature = $true
        }
    }

    Node NotWebServer
    {
        WindowsFeature IIS
        {
            Ensure               = 'Absent'
            Name                 = 'Web-Server'
        }
    }
}
```  
3. Import the configuration into Azure Automation
4. Compile the configuration in Azure Automation
5. Add the VM for management with State Configuration


