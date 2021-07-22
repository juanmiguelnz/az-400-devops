## Exam AZ-400: Designing and Implementing Microsoft DevOps Solutions

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

* Microsoft-hosted
	* less administrative overhead
* Self-hosted
	* you have specific software you need to install to build your application
	* avoid latency

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

### 7. Define and implement a continuous delivery and release management strategy (10-15%)
