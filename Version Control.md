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
# Using Bash on Mac Terminal
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

Tip: escaping spaces in CLI by using "" 
- example:
```
personal@Device-MacBook-Pro GitHub % cd Meta Labs
cd: string not in pwd: Meta
```
This is the correct way to change directory that contains space in its name
```
nemanja@Nemanjas-MacBook-Pro GitHub % cd "Meta Labs"
```


## Pipes |

A coding tool that allows the output of one command to be used as the input for a different command. Use pipes to combine commands together.

## Redirection

There are three types of IO or input/output redirections. Standard input, standard output, and standard error. The shell keeps a reference of standard input, output, and error by a numbering system. The zero(0) is for standard input, one(1) is for standard output, and two(2) is for standard error.
- The standard input redirection gives you the option to record your input and save it to a file either by overwriting or appending the file.
- The redirection standard output allow you to control where the output goes.
- The standard error redirect allows you to specify that the error should be written to a file.

## Grep - Global regular expression print

Grep is used for searching across files and folders as well as the contents of files.

Additional resources:
**Agile methodologies**
[**https://www.planview.com/resources/guide/agile-methodologies-a-beginners-guide/**](https://www.planview.com/resources/guide/agile-methodologies-a-beginners-guide/)

**Installing git on mac and windows, detailed instructions.**
[**https://git-scm.com/book/en/v2/Getting-Started-Installing-Git**](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git "getting started installing git")

**Bash Reference Manual**[https://www.gnu.org/software/bash/manual/html_node/index.html#SEC_Contents](https://www.gnu.org/software/bash/manual/html_node/index.html#SEC_Contents)

**Bash Redirections**
[https://www.gnu.org/software/bash/manual/html_node/Redirections.html#Redirections](https://www.gnu.org/software/bash/manual/html_node/Redirections.html#Redirections)

**Bash Cheatsheet**
[https://devhints.io/bash](https://devhints.io/bash "https://devhints.io/bash")

**Grep Cheatsheet**
[https://devhints.io/grep](https://devhints.io/grep)

**Grep Manual**
[https://man7.org/linux/man-pages/man1/grep.1.html](https://man7.org/linux/man-pages/man1/grep.1.html)

**History and Timeline of Unix**
[https://unix.org/what_is_unix/history_timeline.html](https://unix.org/what_is_unix/history_timeline.html)

**History of Vim**
[https://en.wikipedia.org/wiki/Vim_(text_editor)](https://en.wikipedia.org/wiki/Vim_(text_editor))

**How to work with relative and absolute paths**
[**https://www.geeksforgeeks.org/absolute-relative-pathnames-unix/**](https://www.geeksforgeeks.org/absolute-relative-pathnames-unix/)

**Unix Commands Cheatsheet**
[https://cheatography.com/jluis/cheat-sheets/bash-and-unix-commands/](https://cheatography.com/jluis/cheat-sheets/bash-and-unix-commands/)

**Vim Cheatsheet**
[https://vim.rtorr.com/](https://vim.rtorr.com/)

Module 3
# What is Git and GitHub?

## Git

Git is a version control system designed to help users keep track of changes to files within their projects. Git was designed to fix the problem that it's created, Linus Torvalds was having with managing the huge challenge of keeping track of all changes to the kernel, the operating system for Linux. Linux has thousands of contributors who commit changes and updates daily. Git was designed to help with the challenge of tracking all these changes and updates. As well as helping to keep track of changes, Git was also designed to tackle some of the shortcomings of other version control systems. The benefits that Git offers over similar systems include, better speed and performance, reliability, free and open source axis, and an accessible syntax. It's also important to note that Git is used predominantly via the command line. Developers tend to find Git syntax and commands easy to learn.

## GitHub

GitHub is a Cloud-based hosting service that lets you manage Git repositories from a user interface. A Git repository is used to track all changes to files in a specific folder, and keep a history of all those changes. It incorporates Git version control features and extends these by providing its own features on top. Some of the most common of these features include access control, pull requests, and automation.

## Connecting to GitHub via HTTPS

When using Github you might be required to authenticate using a Personal Access Token over HTTPS. A Personal Access Token is a special password that you use instead of your actual account password. When you're finished using the token, you can revoke it so that it can no longer be used. It is also possible to set an expiry time for the token. This helps to keep your account secure.

**Generate a Personal Access Token**
- **Step 1:** Log in to Github
- **Step 2:** Click on the profile icon in the top right of the screen and select Settings.
- **Step 3:** On the Settings screen, on the left-hand side click Developer Settings.
- **Step 4:** On the Developer Settings screen, click **Personal access tokens**. Under that, click on **Tokens (classic)**. Then, click the **Generate new token** button and select **Generate new token (classic)**.
- **Step 5:** On the New Personal Access Token page, enter a token name and an expiry time. If you wish to manually revoke the token, set the expiry time to No Expiration.
- **Step 6:** Under scopes, select repo.
- **Step 7:** Scroll to the end of the page and click Generate token.
- **Step 8:** The token is now generated. Make sure to copy and keep note of the token as it will be hidden when you leave the page. This token can now be used when connecting to a repository over HTTPS.
-  Note: If you lose the token, you can delete the old token and create a new one.
### Accessing Repositories

When accessing a repository and using HTTPS authentication, make sure you have access/permission to connect, and then just use the HTTPS address for the Git repository itself.

## Connecting to GitHub via SSH

If you plan to use Github from your local device, the recommended way to authenticate is using Secure Shell, or SSH for short. This requires the creation of keys: a public and a private key. The advantage of using SSH is that you don't need to enter in your credentials when interacting with the remote repository. The keys are generated and stored on your local machine and then the public key is copied to the Github server. After you finish setting up, every operation will be authenticated using the keys.

### Generate SSH keys

The process is the same for both Windows and Mac. On Windows, you can use the Git Bash terminal and on Mac, the standard terminal will work.

- Open the terminal
- Enter the following: ssh-keygen -t ed25519 -C "your@email.com"
- Replace the email with your own and press enter.
- It will prompt to enter a password. Hit enter to skip setting a password and do the same for entering the same passphrase again.
![[Screenshot 2024-06-04 at 11.39.00 AM.png]]
- Once you have confirmed it will generate the above to confirm the keys have been created.
- Both keys will be stored in the .ssh folder.
- In order to add our key to Github, we need to get a copy of the public key which is always identified as .pub in your local directory. 
- Find the name of the key file using the below command. 
```
- ls ~/.ssh/ 
```
- Then, use the below command to copy the file, replacing the YOUR KEY with the name of the key file on your device. This step differs between Windows and Mac
- For Mac: 
```
pbcopy < ~/.ssh/<YOUR KEY>.pub For Windows: cat ~/.ssh/<YOUR KEY>.pub | clip
```
- For Windows: 
```
cat ~/.ssh/<YOUR KEY>.pub | clip
```

### Adding Your Keys to Github

We now need to add our public key to Github to grant access to the repositories we create.

- **Step 1:** Log on to Github
- **Step 2:** Click on the profile icon in the top right of the screen and select Settings.
- **Step 3:** On the Settings screen, on the left-hand side under the Access section, click SSH and GPG Keys
- **Step 4:** Click the New SSH key button in Green on the right-hand side of the screen.
- **Step 5:** Enter a title and paste in your public key that you copied previously.
- **Step 6:** Click the Add SSH key button. (You are now ready to access Github via SSH.)

### Accessing Repositories
- When accessing a repository and using SSH authentication, make sure to always use the SSH address of the repository.

### Git Workflow

![[Screenshot 2024-06-04 at 11.57.02 AM.png]]

### Branches

The approach of keeping everything at branch level is much easier than having everyone working from the main line. In fact, everyone working off the same branch is more likely to cause issues. Having independent branches makes the project easier to manage. Also, there's no limit to how many branches you can have.

### Remote vs. local

**Remote** - refers to any other remote repository to which developers can push changes. This can be a centralized repository, such as one provided by Git hub or repositories on other developer devices.Remote repo could be located on GitHub or other developer device.The remote code is accessed through a URI which is unique and only accessible to those who have permission local.

**Cloning** (term. explanation) - Let's say we have a project called coding project one which is located on Git hub with a unique URL. In other words, this project is stored on a remote server. When a user wants to copy this project to their local device, they need to either perform a clone if it's the first time or pull it to get the latest changes. To clone a project a user must first choose a folder on their local machine. Coding project one is then cloned from the server and copied into the chosen folder. The user can then make changes to the project and push those changes back to the server. Other users working on the code base won't see those changes on their local machines unless they pull the latest changes from the server. One of the advantages of it is that you can work offline and then commit your changes when you are ready.

**Local** - your own machine, laptop, desktop, mobile device.

When you use **Git Push**, Git compares a snapshot of your local repository with the remote one and only replaces the files that have been changed.
Using **Git Pull** you're taking all that data from the remote server. Git then merges the snapshot from the remote with the snapshot that's on your local. It will auto merge them if there is no conflicts.

**Lab:** Using a Repository
Objectives:
- Create a repository
- Clone a repository
- Commit a new file to the repository
- Push to a repository

- **Step 1:** Create a new repository on your Github account named repo-exercise. Ensure that Add a README file is selected.
- **Step 2:** Open the Terminal and authenticate using gh (Github CLI):
```
gh auth login
```
- **Step 3:** Create an authentication token in your Github account with specified scopes given in the terminal. Copy it from Github and paste it. Verify authorization was successful.
- **Step 4:** Clone the repository using its GitHub CLI.
```
gh repo clone <YOUR USERNAME>/<REPOSITORY-NAME>
```

```
gh repo clone userName/repo-exercise
Cloning into 'repo-exercise'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (3/3), done.
```
- **Step 5:** Move to the repo directory by using:
```
cd repo-exercise
```
- **Step 6:** Add the  result.txt to the repository folder.
```
touch result.txt
```
- **Step 7:** In the Git terminal, run the git status command. 
```
git status
On branch main
Your branch is up to date with 'origin/main'.

Untracked files:

  (use "git add <file>..." to include in what will be committed)

result.txt

nothing added to commit but untracked files present (use "git add" to track)
```
- **Step 8:** Verify that the output shows result.txt as an untracked file.
- **Step 9:** Run the command git add result.txt
```
git add result.txt
```
- **Step 10:** Run the git status command again.
```
git status
On branch main
Your branch is up to date with 'origin/main'.
  

Changes to be committed:

  (use "git restore --staged <file>..." to unstage)

new file:   result.txt
```
- **Step 11:** Verify that the output shows result.txt as a tracked file.
- **Step 12:** Next, run the git commit command and specify the commit message as Successful exercise.
- **Step 13:** Verify that the output shows result.txt with create mode
- **Step 14:** Next, run the git push command.
```
git push

Everything up-to-date
```
- **Step 15:** Verify that the output pushed successfully.
- **Step 16:** On Github, go to your repository page.
- **Step 17:** Verify that the result.txt file is listed. You may need to refresh the page to see the changes.

## Resolving Conflicts

Conflicts will normally occur when you try to merge a branch that may have competing changes. Git will try to auto-merge, but in the case of a conflict, it will need some confirmation. The competing changes need to be resolved by the end user. This process is called merging or rebasing.

### Diff Commands

**Git status** - tells you **which** files were changed.
**Git diff** -tells you **what** changes were made.

**Git diff** will compare the previous version of the file with your current one to find any differences. It will then tell you specifically what content has been removed as well as what content has been added to the file.

Individual files, branches, and commits can all be compared with Git diff.


### Blame

Git has a very helpful command for keeping track of who did what and when. It's called **git blame**. The git blame command is used to look at changes of a specific file and show the dates, times, and users who made the changes.

- Example:
```
git blame setup.py
```
	setup.py (any file name)

| **Git Blame Message**         | **Format**         |
| ------------------------- | -------------- |
| **90125897**                  | **Commit ID/Hash** |
| **Developer 1**               | **Author**         |
| **2024-06-01**                | **Date**           |
| **19:48:31**                  | **Time**           |
| **+0000 1**                   | **Line number**    |
| **`let add = (a , b) => {}`** | **Content**        |

### Forking

**Forking** - is another type of workflow. The key difference between branching and forking is that the workflow for forking creates a new repository entirely. Branching cuts a new branch from the same repository each time and each member of the team works on the single repository.
You can use forking to contribute to another person's repository, or that of another organization, by creating your own copy.

Additional resources:

**Git: An Origin Story**
[https://www.linuxjournal.com/content/git-origin-story](https://www.linuxjournal.com/content/git-origin-story)

**Git Cheatsheet**
[https://education.github.com/git-cheat-sheet-education.pdf](https://education.github.com/git-cheat-sheet-education.pdf)

**Git patterns and anti-patterns for successful developers**
[https://youtu.be/t_4lLR6F_yk](https://youtu.be/t_4lLR6F_yk)

**Tech Talk: Linus Torvalds on git**
[https://www.youtube.com/watch?v=4XpnKHJAok8](https://www.youtube.com/watch?v=4XpnKHJAok8)

**Vim Cheatsheet**
[https://devhints.io/vim](https://devhints.io/vim)

### Tips

- Don't make your edits directly on the master branch, always create and checkout a fork before making changes
    
- Make sure you push your development branch to your fork
    
- You can select the current branch inside Github by clicking the branch dropdown

Git common commands:
**git pull** - command is used to fetch and download content from a remote repo and immediately update the local repo to match that content.
**git pull** - command is used to upload local repo content to a remote repo.
**git commit** - command is used to capture a snapshot of the projects's currently staged changes.

**SETUP**:
Configuring user information used across all local repositories.
- set a name that is identifiable for credit when review version history
```
git config --global user.name “[firstname lastname]”
```
- set an email address that will be associated with each history marker
```
git config --global user.email “[valid-email]”
```
- set automatic command line coloring for Git for easy reviewing
```
git config --global color.ui auto
```


**SETUP & INIT**:
Configuring user information, initializing and cloning repositories.
- initialize an existing directory as a Git repository
```
git init
```
- retrieve an entire repository from a hosted location via URL
```
git clone [url]
```

**STAGE & SNAPSHOT**:
Working with snapshots and the Git staging area.
- show modified files in working directory, staged for your next commit
```
git status
```
- add a file as it looks now to your next commit (stage)
```
git add [file]
```
- unstage a file while retaining the changes in working directory
```
git reset [file]
```
- diff of what is changed but not staged
```
git diff
```
- diff of what is staged but not yet commited
```
git diff --staged
```
- commit your staged content as a new commit snapshot
```
git commit -m “[descriptive message]”
```

**BRANCH & MERGE**
Isolating work in branches, changing context, and integrating changes.
- list your branches. a * will appear next to the currently active branch
```
git branch
```
- create a new branch at the current commit
```
git branch [branch-name]
```
- switch to another branch and check it out into your working directory
```
git checkout
```
- merge the specified branch’s history into the current one
```
git merge [branch]
```
- show all commits in the current branch’s history
```
git log
```

**INSPECT & COMPARE**
Examining logs, diffs and object information.
- show the commit history for the currently active branch
```
git log
```
- show the commits on branchA that are not on branchB
```
git log branchB..branchA
```
- show the commits that changed file, even across renames
```
git log --follow [file]
```
- show the diff of what is in branchA that is not in branchB
```
git diff branchB...branchA
```
- show any object in Git in human-readable format
```
git show [SHA]
```

**TRACKING PATH CHANGES**
Versioning file removes and path changes.
- delete the file from project and stage the removal for commit
```
git rm [file]
```
- change an existing file path and stage the move
```
git mv [existing-path] [new-path]
```
- show all commit logs with indication of any paths that moved
```
git log --stat -M
```

**IGNORING PATTERNS**
Preventing unintentional staging or commiting of files.
- Save a file with desired paterns as .gitignore with either direct string matches or wildcard globs.
```
logs/
*.notes
pattern*/
```
- system wide ignore patern for all local repositories
```
git config --global core.excludesfile [file]
```

**SHARE & UPDATE**
Retrieving updates from another repository and updating local repos.
- add a git URL as an alias
```
git remote add [alias] [url]
```
- fetch down all the branches from that Git remote
```
git fetch [alias]
```
- merge a remote branch into your current branch to bring it up to date
```
git merge [alias]/[branch]
```
- Transmit local branch commits to the remote repository branch
```
git push [alias] [branch]
```
- fetch and merge any commits from the tracking remote branch
```
git pull
```

**REWRITE HISTORY**
Rewriting branches, updating commits and clearing history.
- apply any commits of current branch ahead of specified one
```
git rebase [branch]
```
- clear staging area, rewrite working tree from specified commit
```
git reset --hard [commit]
```

**TEMPORARY COMMITS**
Temporarily store modified, tracked files in order to change branches.
- Save modified and staged changes
```
git stash
```
- list stack-order of stashed file changes
```
git stash list
```
- write working from top of stash stack
```
git stash pop
```
- discard the changes from top of stash stack
```
git stash drop
```
