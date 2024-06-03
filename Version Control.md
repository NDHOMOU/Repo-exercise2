Module 1 
# Software Collaboration
What is version control?
Version control is a system that records all changes and modifications to  files for tracking purposes. Developers also use the term source control or source code management. The primary goal of any version control system is to keep track of changes.

Benefits associated with version control:
- Revision History
- Identity
- Collaboration
- Automation
- Efficiency

## Systems of version control: Centralized & Distributed
- Centralized version control systems, or CVCS for short, contain a server and a client. The server contains the main repository that houses the full history of versions of the code base.
- Distributed version control systems or DVCS for short, are similar to the centralized model. You still need to pull code down from the server to view the latest changes. The key difference is that every user is essentially a server and not a client. This means that every time you pull down code from the distributed model, you have the entire history of changes on your local system.

# Version control in professional software development
Workflow
Workflows are essential to ensure code is managed correctly and reduce mistakes from happening.

Continuous Integration
CI is used to automate the integration of code changes from multiple developers into a single main stream. Using workflow whereby small changes are merged frequently, often many times per day, will reduce the number of conflicts. CI is often used to automatically compile the project and run tests on every code change to ensure that the build remains stable and prevent regressions in functionality.

Continuous Delivery
CD is an extension of CI. Once the changes have been merged into the main stream, a CD system automatically packages the application and prepares it for deployment. This helps avoid human error when packaging the application.

Continuous Deployment
Continuous Deployment is an extension of C.Delivery. The Goal of C.Deployment is to deploy and release software to customers frequently and safely. The strategy commonly involves automatically deploying to a test (also known as staging) environment first to validate the deployment package and software changes. Once validated, it can automatically deploy to the live (production) environment for customers.

## Staging vs. Production
### Development Environments

**Staging** -
The staging environment should mimic your production environment. The reason for this is because you want to test the code in an environment that matches what you have in production. This allows teams to spot or find any potential issues prior to them getting to production. The closer the staging environment is to your production, the more accurate your testing is going to be. Staging environments can also be used for testing and verifying new features and allow other teams including QA or stakeholders to see and use those features as a pre-trial.

**New Features** -
Developers submitting new features along with feature flags for turning them on and off should always do a testing round in a staging environment. They allow teams to verify that the feature works, it can be turned on and off via configuration flags and also that it does not break or interfere with existing functionality.

**Testing** -
As the staging environment mimics your production environment, it's also a great place to run tests. QA teams will normally use it to verify new features, configuration changes or software updates/patching. The types of testing covered will be Unit testing, Integration testing and performance testing. All except performance testing can also be carried out in production. Performance can also be completed in production but only at specific times - usually out of hours as it will have a drastic effect on the user experience.

Sometimes it is not always feasible to have an exact replication either due to costs or time. Certain areas can be cut back - for example, if your service is load balanced on 10 virtual machines in production, you could still have 4 virtual machines in staging. The underlying architecture is the same but the overall performance may be different.

**Migrations** -
Staging is a perfect place to test and verify data migrations. Snapshots can be taken from production and used to test your migration scripts to confirm your changes will not break anything. If in the case it does cause an issue, you simply rollback and try again. Doing something like a migration in production is extremely risky and error-prone.

**Configuration Changes** -
Configuration can also cause headaches for teams, especially in a large cloud-based architecture. Having a staging environment will allow you to spot any potential issues or bottlenecks.

**Production** -
Production is live. It's out there for people to see and/or interact with. Any issues or problems you may have had should have been caught and fixed in the staging environment. The staging area gives the team a safety net to catch these possible issues. Any code that is deployed to production should have been tested and verified before the deployment itself.

**Downtime** -
Downtime for any service especially customer facing will most likely be revenue impacting. If customers can not access or use your website or app to its full capabilities, it will most likely have a cost involved. Take for example an e-commerce company that allows users to buy goods and services online. If they release a new feature to their shopping cart which actually breaks the payment process, this will have an impact on customers not being able to buy goods online.

**Vulnerabilities** -
Cyber-security should also play a big role in what gets released in production. Any updates to software such as patching or moving to the latest version should be checked and verified. This is also the same rule for not upgrading software when critical updates are released.

**Reputation** -
Downtime or issues in production is damaging for a company as it does not instill confidence in end users. If something is down or broken it can cause the company to lose potential customers.

Module 1 additional resources: 
**About Version Control**
[https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control)
**List of Version Control Software**
[https://en.wikipedia.org/wiki/List_of_version-control_software](https://en.wikipedia.org/wiki/List_of_version-control_software)
**The benefits of a distributed version control system**
[https://about.gitlab.com/topics/version-control/benefits-distributed-version-control-system/](https://about.gitlab.com/topics/version-control/benefits-distributed-version-control-system/)
**What is Cloning?**
[**https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository**](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository)



Module 2
## Using Bash on Mac Terminal
### Bash commands

Bash provides a list of commands for navigating through files, viewing the contents of files, and edit features for changing or updating the contents of a file. Below is a list of the most common commands:

| **Command** | **Used for**                                                                 |
| ----------- | ---------------------------------------------------------------------------- |
| cd          | Change Directory                                                             |
| ls          | List command used for showing the content of a directory.                    |
| rm          | Remove command used for removing a file or a directory                       |
| mv          | Used to move files or folders to another location                            |
| touch       | Allows creating of a new empty file or to update a timestamp on a file       |
| cp          | Used to make a copy of a file or folder                                      |
| mkdir       | Make a new directory                                                         |
| pwd         | Print work directory, shows the current location in the shell                |
| cat         | Allows reading or concatenation of a file                                    |
| less        | Displays the contents of a file one page at a time.                          |
| grep        | Global regular expression, allows for searching contents of files or folders |
**Flags** -
Every bash command has flags for changing the output of the command itself. For example, the **ls** command prints out the list of contents inside a directory. If we wanted to show the list in a different view, we simply need to add a flag such as **-l**.

**Man Pages** -
When first learning commands from bash, it can feel a bit daunting. Luckily, every command has its manual (or man pages for short). The man page lists all the flags and options that a particular command has to offer. The man pages are a great way to recall the different flags that are available and a great tool in your arsenal to becoming more fluent in bash.

**Editing** -
There are many options for editing files in bash. The most common is usually VI or Vim. VI stands for visual editor. It's used for making edits and changes to a file and saving them. It's similar to what you may have used in applications like Word. VIM is a better version of VI with some improvements - hence its name: visual editor improved. Learning the commands in Vim will feel different from GUI applications, but once you practice, it will feel like second nature. Vim uses modes to determine the commands you can work with:
- Normal mode: Default mode
- Insert mode: Allows the contents of the files to be edited.
- Command line mode: Normal commands begin with **:**

Lab: "Your Working Directory"
coder@a9289c0a1298:~/project$ pwd
/home/coder/project

Lab: "Make and change directories and files"
- **mkdir lab** - creates lab directory(folder)
- **cd lab** - changes directory to lab
- **touch file1.txt** - creates file "file1.txt"
- **mk dir1**
- **mv file1.txt dir/** - moves "file1.txt" to dir1
- **mkdir -p dir2/dir3** - **-p** flag to create the parent directories if they do not exist. In this case it will create the dir2 directory and then create the dir3 directory inside of dir2
- **ls -l** - note how many files and directories are in current dir

## Pipes |

A coding tool that allows the output of one command to be used as the input for a different command. Use pipes to combine commands together.

## Redirection

There are three types of IO or input/output redirections. Standard input, standard output, and standard error. The shell keeps a reference of standard input, output, and error by a numbering system. The zero(0) is for standard input, one(1) is for standard output, and two(2) is for standard error.
- The standard input redirection gives you the option to record your input and save it to a file either by overwriting or appending the file.
- The redirection standard output allow you to control where the output goes.
- The standard error redirect allows you to specify that the error should be written to a file.

## Grep - Global regular expression print

Grep is used for searching across files and folders as well as the contents of files.