## Exam AZ-400: Designing and Implementing Microsoft DevOps Solutions
Regularly updated as I go thru each [Skills Measured in this doc.](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE3VP8d)

References:

* [AZ-400 Exam Page](https://docs.microsoft.com/en-us/learn/certifications/exams/az-400)
* [Microsoft Learn](https://docs.microsoft.com/en-us/learn/browse/?roles=devops-engineer&resource_type=learning%20path)
* [Pluralsight](https://app.pluralsight.com/paths/certificate/designing-and-implementing-microsoft-devops-solutions-az-400)

### 1. Develop an instrumentation strategy (5-10%)
### 2. Develop a Site Reliability Engineering (SRE) strategy (5-10%)
### 3. Develop a security and compliance plan (10-15%)
### 4. Manage source control (10-15%)
### 5. Facilitate communication and collaboration (10-15%)
### 6. Define and implement continuous integration (20-25%)
----

Continuous Integration - the process of automating the build and testing of code every time a team member commits changes to version control.

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

Function Tests
	- Verifies that each function of the software does what it should. How the software implements each function isn't important in these tests. What's important is that the software behaves correctly. You provide an input and check that the output is what you expect.

* Smoke Testing - Verifies the most basic functionality of your application or service. These tests are often run before more complete and exhaustive tests. Smoke tests should run quickly.
* Unit Testing - Verifies the most fundamental components of your program or library, such as an individual function or method.
* Intergration Testing - Verifies that multiple software components work together to form a complete system. For example, an e-commerce system might include a website, a products database, and a payment system. You might write an integration test that adds items to the shopping cart and then purchases the items. The test verifies that the web application can connect to the products database and then fulfill the order.
* Regression Testing - A regression occurs when existing behavior either changes or breaks after you add or change a feature. Regression testing helps determine whether code, configuration, or other changes affect the software's overall behavior.
* User interface Testing - Verifies the behavior of an application's user interface. UI tests help verify that the sequence, or order, of user interactions leads to the expected result.
* Usability Testing - A form of manual testing that verifies an application's behavior from the user's perspective. Usability testing is typically done by the team that builds the software.
* User Acceptance Testing - like usability testing, focuses on an application's behavior from the user's perspective. Unlike usability testing, UAT is typically done by real end users.

	** Code Coverage - Computes the percentage of your code that's covered by your unit tests.

Nonfunctional Tests
	- Checks characteristics like performance and reliability. An example of a nonfunctional test is checking to see how many people can sign in to the app simultaneously. Load testing is another example of a nonfunctional test.

Automated Testing - Uses software to execute your code and compare the actual results with the results you expect.
* Lint Testing - A form of static code analysis, checks your code to determine whether it conforms to your team's style guide.



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

### 7. Define and implement a continuous delivery and release management strategy (10-15%)
