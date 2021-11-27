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


## Git usage
In this chapter, we will see how to use Git to start with our version controlling.

### Creating a repository
To begin using Git, we have first to create a repository, also known as “repo”. For that, in the directory where we want to have the repository, we have to execute:
``` 
git init 
```
![image](https://user-images.githubusercontent.com/48562260/143530401-72e87c1f-2c44-4316-ba69-aa50ff5b14c3.png)

We have a Git repository! Note that a folder named .git has been created. The repository will be the directory where the .git folder is placed. This folder is the repository metadata, an embedded database. It’s better not to touch anything inside it while you are not familiarized with Git

### Creating the history: commits
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
```
**Would commit the file with** ``` 'Second commit!' ``` **content, because it was the one added to the index, and then we changed the file of the working directory**, not the one added to staging area. **To commit the latest change, we would have to add again the file to the index,** _being the first added file **overwritten**._

Git identifies each commit uniquely using SHA1 hash function, based on the contents of the committed files. So, each commit is identified with a 40 character-long hexadecimal string, like the following, for example: ``` de5aeb426b3773ee3f1f25a85f471750d127edfe ``` . Take into account that the commit message, commit date, or any other variable rather than the committed files’ content (and size), are not included in the hash calculation.

So, for our first two commit, the history would be the following:
History of the repository, with two commits.
![image](https://user-images.githubusercontent.com/48562260/143669117-ddbce443-f3da-4c70-b1d6-6b6cdafdd823.png)

Git shortens the checksum of each commit to 7 characters (whenever it’s possible), to make them more legible.

Each commit points to the commit it has been created from, being this called the “**ancestor**”.

Note that HEAD element. This is one of the most important element in Git. _**The HEAD**_ is the element that points to the current point in the repository history. **The contents of the working directory will be those that belong to the snapshot the HEAD is pointing to.
**

#### Tips for creating good commit messages
The commit message content is more important that it may seem at first sight. Git allows to add any kind of explanation for any change we made, without touching the source code, and we should always take advantage of this.

For the message formatting, there’s an unwritten rule known as the 50/72 rule, which is so simple:

- One first line with a summary of no more than 50 characters.
- Wrap the subsequent explanations in lines of no more than 72 characters.
- 
This is based on how Git formats the output when we are reviewing the history.

But, more important than this, is the content of the message itself. The first thing that comes to mind to write are the changes that have been made, which is not bad at all. But the commit object itself is a description of the changes that have been made in the source code. To make the commit messages useful, **you should always include the reason that motivated the changes**

### Viewing the history
Of course, Git is able to show the history of the repository. For that, the log command is used:
~~~
git log
~~~
If you try it, you will see that the output is not very nice. The log command has many flags available to draw pretty graphs. Here’s a suggestion for using this command through this guide, even if graphs are shown for each scenario:
```
git log --all --graph --decorate --oneline
```
If you want, you can omit the --oneline flag for showing the full information of each commit.

### Independent development lines: branches
Branching is probably the most powerful feature of Git. **A branch represents an independent development path.** The branches coexist in the same repository, but each one has its own history. In the previous section, we have worked with a branch, Git’s default branch, which is named ``` master ```.
Taking into account this, the proper way to express the history would be the following, considering the branches.

![image](https://user-images.githubusercontent.com/48562260/143671265-c44651a4-58d0-4a3f-b087-8b609421ef92.png)

History of the repository, showing the branch pointer.

Creating a branch with Git is so simple:

```
git branch <branch-name>
```

For example:

```
git branch second-branch
```
And that’s it.

But, what is Git doing really when it creates a branch? It just creates a pointer with that branch name that points to the commit where the branch has been created:

![image](https://user-images.githubusercontent.com/48562260/143671475-c43fbeb9-f37f-43f3-924e-1d23cc8d4910.png)

This is one of the most notable features of Git: the branch creation speed, almost instantaneous, regardless of the repository size.

To start working in that branch, we have to ```checkout``` it:
```
git checkout second-branch
```
![image](https://user-images.githubusercontent.com/48562260/143671552-94340e64-0a1d-40e5-9168-06e15bd587c9.png)
 
 Now, the commits will only exist in ```second-branch```. 
 Why? Because the HEAD now is pointing to second-branch, so, the history created from now will have an independent path from master.

We can see it making a couple of commits being located in second-branch:

![image](https://user-images.githubusercontent.com/48562260/143671906-2e98e634-34d0-4f0d-9369-168ac5cceb2f.png)

**But, what if we return to master?**
```
git checkout master
```
The content of the file will be:
 > Second commit!

This is because, after creating the history of ```second-branch``` , we have placed the ```HEAD``` pointing to ``` master ```:
![image](https://user-images.githubusercontent.com/48562260/143672070-6c453b8d-934b-4b71-ab42-b23d26f5f08a.png)

 Independent history for second-branch.
 ### Combining histories: merging branches
 
 In the previous subsection, we have seen how we can create different paths for our repository history. Now, we are going to see how to combine them, what for Git is calling merging.

Let’s suppose that, after the changes made in second-branch, is ready to return to master. For that, we have to place the HEAD in the destination branch (master), and specify the branch that is going to be merged to this destination branch (second-branch), with merge command:

```
git checkout master
git merge second-branch
```
Now, the history of the ``` second-branch ``` has been merged to ``` master ```, so, all the changes made in this first branch have been applied to the second.

In this case, the entire history of ``` second-branch ``` is now part of the **history** of ``` master ``` , having a graph like the following:
![image](https://user-images.githubusercontent.com/48562260/143672363-19bedda8-38c6-4da9-9060-1c13100d8163.png)

As you can see, no track of the life of ```second-branch``` has been saved, when you probably were expecting a nice tree.

This is because Git merged the branch using the _fast-forward mode_. 
Note that is telling it in the merge output, shown above. Why did Git do this? Because master and second-branch shared the _common ancestor_, f043d98.

When we are merging branches, is always advisable** not to use** the fast-forward mode. This is achieved passing **--no-ff** flag while merging:
```
git merge --no-ff second-branch
```
_What does this really do?_  Well, it just creates an intermediate, third commit, between the **HEAD**, and the “**from**” branch’s last commit.

After saving the commit message (of course, is editable), the branch will be merged, having the following history:

![image](https://user-images.githubusercontent.com/48562260/143672533-35d732ec-8b7d-4a5f-9048-18581194688b.png)

History after merging second-branch to master, using no fast-forward mode.

Which is much more expressive, since the history is reflected as it is actually is. The no fast-forward mode should be always used.

A merge of a branch supposes the end of the life of this. So, it should be deleted:

```
git branch -d second-branch
```
Of course, in the future, you can create again a ``` second-branch ``` named branch.

###Conflictive merges
In the previous section we have seen an “**automatic” merge**, i.e., _Git has been able to merge both histories_. 

Why? Because of the previously mentioned common _**ancestor**_. That is, the branch is returning to the point it started from.

But, when the branch another branch borns from suffers changes, problems appear.
To understand this, let’s construct a new history, which will have the following graph:
![image](https://user-images.githubusercontent.com/48562260/143673851-82dd8ffe-d230-43c2-af34-91d8cc197c6b.png)
Continuing the history of master, after the creation of second-branch.

With the following commands:
```
echo 'one' >> file.txt
git add file.txt
git commit -m 'first'
 
echo 'two' >> file.txt
git add file.txt 
git commit -m 'second'
 
git checkout -b second-branch
 
echo 'three (from second-branch)' >> file.txt 
git add file.txt 
git commit -m 'third from second branch'
 
git checkout master
 
echo 'three' >> file.txt 
git add file.txt 
git commit -m 'third
```
What will happen if we try to merge second-branch to master?
```
git checkout master
git merge second-branch
```
Git won’t be able to do it:
```
CONFLICT (content): Merge conflict in file.txt
Automatic merge failed; fix conflicts and then commit the result
```

Git doesn’t know how to do it, because the changes made in second-branch are not directly applicable to master, since it has changed from this first branch inception. What Git has done is to indicate in which parts exists these incompatibilities.

Note that we haven’t used the --no-ff flag, since we now in advance that the fast-forward won’t be possible.

If we check the status, we will see the following:
