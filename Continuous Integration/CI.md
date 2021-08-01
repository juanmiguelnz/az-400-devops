# Continuous Integration  
The process of automating the build and testing of code every time a team member commits changes to version control.

A Pipeline is composed of:
1. Tasks - script or scripts that defines how your build, test, and deployment steps are run.
2. Code - source code stored in a repository
3. Agent - an installable software that runs the build and deployment.
4. Artifact - smallest compiled unit that can be tested or deployed.

Concurrent Pipelines (aka Parallel Jobs) - Lets you run a single build or release job at any give time. Purchased at the organization level. Shared by all projects in the organization.

Microsoft-hosted vs Self-hosted 
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
	

Automated Testing - Uses software to execute your code and compare the actual results with the results you expect.
* Lint Testing - A form of static code analysis, checks your code to determine whether it conforms to your team's style guide.
* Unit Tests - Testing a single peice of functionality.
* Code Coverage - Computes the percentage of your code that's covered by your unit tests.
* Intergration Tests - Done after the build. Verifies that multiple components work together.
* Regression Tests -

What is a package?
* A package contains reusable code that other developers can use in their own project.
* Typically contains the compiled binary code (ex. .dll for .NET or .class for Java).
* For language that are interpreted instead of compiled (ex. JavaScript or Python), a package might include source code.

Semantic Versioning ( Major.Minor.Patch[-Suffix] )

* Major - Introduces breaking changes. Apps typically need to update how they use the package to work with a new major version. 
* Minor - Introduces new features but is backward compatible with earlier versions.
* Patch - Introduces backward compatible bug fixes but not new features.
* -Suffix - identifies the package as a pre-release (ex. 1.0.0-beta1)

Azure Artifacts
- A repository in Azure DevOps where you can manage the dependencies for you codebase.
- Stores artifacts and binaries.

Security Scanning
- During the build process, you can integrate external tools that scans the packages and gives feedback. During the CD process, the tool uses the build artifacts and performs scans (Ex. WhiteSource Bolt and Black Duck).

Azure Pipeline  
* Trigger - tells the Pipeline to run
* Pipeline - made up of ***one or more Stages***. A Pipeline can deploy to ***one or more Environments***.
* Stage - a way of organizing Jobs in a Pipeline. Each Stage can have ***one or more Jobs***.
* Job - runs on one Agent. A Job can also be Agentless.
* Agent - runs a Job that ***contains one or more Steps***.
* Step - can be ***a Task or a Script*** and is the smallest building block of a Pipeline.
* Task - a ***pre-packaged script*** that performs an action.
* Artifact - a collection of files and packages ***published by a Run***.
* Run - represents one execution of a Pipeline.