 # GIT Essential Training Basic 
 ## Version Control 
 Version control, also known as source control, is the practice of tracking and managing changes to software code. Version control systems are software tools that help software teams manage changes to source code over time.
 - As development environments have accelerated, version control systems help software teams work faster and smarter. They are especially useful for DevOps teams since they help them to reduce development time and increase successful deployments.
 - Version control software keeps track of every modification to the code in a special kind of database. If a mistake is made, developers can turn back the clock and compare earlier versions of the code to help fix the mistake while minimizing disruption to all team members.
 - Software developers working in teams are continually writing new source code and changing existing source code. The code for a project, app or software component is typically organized in a folder structure or "file tree". One developer on the team may be working on a new feature while another developer fixes an unrelated bug by changing code, each developer may make their changes in several parts of the file tree.
 - -Version control helps teams solve these kinds of problems, tracking every individual change by each contributor and helping prevent concurrent work from conflicting. Changes made in one part of the software can be incompatible with those made by another developer working at the same time. This problem should be discovered and solved in an orderly manner without blocking the work of the rest of the team. Further, in all software development, any change can introduce new bugs on its own and new software can't be trusted until it's tested. So testing and development proceed together until a new version is ready.
 
 ### Why you need Version control ?
 - track history 
 - work together 

### Catagories
- Centralized ![Centralized-Version-Control-System-Workflow-What-Is-Git-Edureka](https://user-images.githubusercontent.com/48562260/143176323-a6e04f13-b938-436c-9ed3-4ef03d3fe8e5.png)

- distributed ![Distributed-Version-Control-System-Workflow-What-Is-Git-Edureka](https://user-images.githubusercontent.com/48562260/143176332-287b72d1-bf44-459f-bd34-00deee85316d.png)

### What we are going to learn ?
- How to keep track of the different versions of your code and configuration files using version control systems or VCS.
-  These are tools that everyone in IT can benefit from, even if it's not just for programming or automation itself. It will allow us to easily roll back when mistakes happen and also help us collaborate with others.
-  Popular VCS GIT 
-  go through how to set up an account with GitHub
-  store your codes history in Git, and collaborate with others in GitHub
-  GitHub portfolios 
-  Git Commands  

### Course prerequisites
- few basic operating system concepts like files, directories, and file systems
- command line for interacting with Gi
   
   
---
   
### What is GIT ?
It's a most popular version control system in the world.

### Download and install Git

#### Linux
Git can be installed in Linux executing the following commands:
```
sudo apt-get update
sudo apt-get install git
```
#### Windows
Firstly, we have to download the last stable release from official page. https://git-scm.com/downloads

![image](https://user-images.githubusercontent.com/48562260/143528234-61fad806-ff9e-4a24-829d-d5e828a9e278.png)


Run the executable, and click “next” button until you get to the following step:
![image](https://user-images.githubusercontent.com/48562260/143528696-f2bb2aac-98be-4605-8385-033dc691f05d.png)


### Git usage
In this chapter, we will see how to use Git to start with our version controlling.

#### Creating a repository
To begin using Git, we have first to create a repository, also known as “repo”. For that, in the directory where we want to have the repository, we have to execute:
``` 
git init 
```
![image](https://user-images.githubusercontent.com/48562260/143530401-72e87c1f-2c44-4316-ba69-aa50ff5b14c3.png)

We have a Git repository! Note that a folder named .git has been created. The repository will be the directory where the .git folder is placed. This folder is the repository metadata, an embedded database. It’s better not to touch anything inside it while you are not familiarized with Git

#### Creating the history: commits
Git constructs the history of the repository with commits. 
- A commit is a full snapshot of the repository, that is saved in the database. 
- Every state of the files that are committed, will be recoverable later at any moment.

When doing a commit, we have to choose which files are going to be committed; not all the repository has to be committed necessarily. This process is called ***staging***, where files are added to the index. The _**Git index**_ is where the data that is going to be saved in the commit is stored temporarily, until the commit is done.

Let’s see how it works.

We are going to create a file and add some content to it, for example:
```
echo 'My first commit!' > README.txt
```
Adding this file, the status of the repository has changed, since a new file has been created in the **working directory**. We can check for the status of the repository with the status option:
```
git status
```
Which, in this case, would generate the following output:

![image](https://user-images.githubusercontent.com/48562260/143530724-c5675b34-48fc-4b48-ba9e-2152a937ca54.png)

What Git is saying is _“you have a new file in the repository directory, but this file is not yet selected to be committed“_.

If we want to include this file the commit, remember that it has to be added to the index. This is made with the add command, as Git suggests in the output of status :
```
git add README.txt
```
![image](https://user-images.githubusercontent.com/48562260/143530873-d9daaca5-0f6a-4ae1-bb64-9955a797073c.png)

Again, the status of the repository has changes:

![image](https://user-images.githubusercontent.com/48562260/143530945-4e632d1b-56b1-45ff-858a-06f8e28270e7.png)

Now, we can do the commit!
```
git commit
```
Now, the default text editor will be shown, where we have to type the commit message, and then save. **If we leave the message empty, the commit will be aborted.**

Additionally, we can use the shorthand version with ``` -m ``` flag, specifying the commit message inline:
```
git commit -m 'Commit message for first commit!'
```

We can add all the files of the current directory, recursively, to the index, with .:
```
git add .
```

Note that the following:

```
echo 'Second commit!' > README.txt
git add README.txt
echo 'Or is it the third?' > README.txt
git commit -m 'Another commit'

