### Introduction #instinct
- What is Git?
	- Git is officially defined as a distributed version control system(VCS)
- In other words, it's a system that tracks changes to our project files over time.
	- It enables us to record project changes and go back to a specific version of the tracked files, at any given point in time.
	- This system can be used by many people to efficiency work together and **collaborate on team projects**, where each developer can have their own version of the project, distributed on their computer.
	- Later on, these individual versions of the project can be merged and adapted into the main version of the project
- Basicaly, its a massively popular tool for coordinating parallel work an managing projects amoung individuals and teams.
	- Needless to say, knowing how to use Git is one of the most important skills of any developer nowadays - and it's definitely a great addition of your resume!

[Official Homepage: ](https://git-scm.com/)

```       

superbeliever@Ravitejs-MacBook-Air ~ % git --version

git version 2.31.1

superbeliever@Ravitejs-MacBook-Air ~ % git config --global user.name "Ravitej Venkataswamy"

superbeliever@Ravitejs-MacBook-Air ~ % git config --global user.email "ravitejvenkataswamy@icloud.com"

```

It's just to keep track of who is doing the changes
Git and GitHub are two separate things
	You need to understand Git to use GitHub

### Repositories
- When working with Git, it's important to be familar with the term repository.
- `ls` is command for to check for all the files in a file
- To create a Git repository in a path
	- use `git init`
``` 
superbeliever@Ravitejs-MacBook-Air courses % cd GitInstinct 

superbeliever@Ravitejs-MacBook-Air GitInstinct % git init

hint: Using 'master' as the name for the initial branch. This default branch name

hint: is subject to change. To configure the initial branch name to use in all

hint: of your new repositories, which will suppress this warning, call:

hint: 

hint: git config --global init.defaultBranch <name>

hint: 

hint: Names commonly chosen instead of 'master' are 'main', 'trunk' and

hint: 'development'. The just-created branch can be renamed via this command:

hint: 

hint: git branch -m <name>

Initialized empty Git repository in /Users/superbeliever/Documents/Courses/GitInstinct/.git/

superbeliever@Ravitejs-MacBook-Air GitInstinct %
```

- use `ls -a` to view hidden folders and files, you will see
`		- .				..				.git`

### Git status
`git status`
	
```       

superbeliever@Ravitejs-MacBook-Air GitInstinct % git status

On branch master

  

No commits yet

  

nothing to commit (create/copy files and use "git add" to track)
```

### Creating a new file
`touch index.html`

```       

superbeliever@Ravitejs-MacBook-Air GitInstinct % touch gittesting.py

superbeliever@Ravitejs-MacBook-Air GitInstinct % open GitInstinct

The file /Users/superbeliever/Documents/Courses/GitInstinct/GitInstinct does not exist.

superbeliever@Ravitejs-MacBook-Air GitInstinct % open gittesting.py

superbeliever@Ravitejs-MacBook-Air GitInstinct % git status
On branch master
  
No commits yet
  
Untracked files:
 (use "git add <file>..." to include in what will be committed)

gittesting.py

  

nothing added to commit but untracked files present (use "git add" to track)
```

### Commiting
###### Staging files 
	From this Staging area, we then commit
1. `git add gittesting.py`
	1. Adds files to stating area
2. `git status`

```       

superbeliever@Ravitejs-MacBook-Air GitInstinct % git add gittesting.py 

superbeliever@Ravitejs-MacBook-Air GitInstinct % git status

On branch master

  

No commits yet

  

Changes to be committed:

 (use "git rm --cached <file>..." to unstage)

new file: gittesting.py
```

`"git commit -m "I love the Git"`
This commits the code to local version control database.
`git status`
`git log`


```       

superbeliever@Ravitejs-MacBook-Air GitInstinct % git commit -m "I love the Git"

\[master (root-commit) 04970b5\] I love the Git

 1 file changed, 0 insertions(+), 0 deletions(-)

 create mode 100644 gittesting.py

superbeliever@Ravitejs-MacBook-Air GitInstinct % git status

On branch master

nothing to commit, working tree clean

superbeliever@Ravitejs-MacBook-Air GitInstinct % git log

commit 04970b5a9f9c0bfa1beacb6fac35ea220c5757bf (**HEAD ->** **master**)

Author: Ravitej Venkataswamy <ravitejvenkataswamy@icloud.com>

Date: Sun May 30 20:22:33 2021 +0530

  

 I love the Git
```

`touch app.py`
`touch styles.app`
- it commit -m gives a overview of what happened when you did a commit
	`Author: Ravitej Venkataswamy <ravitejvenkataswamy@icloud.com>`

### Commit history
`git log`

`git checkout <commithash>`
This modifies the file to that particular hash
It's like a time machine

### Brachnes
- A **brach** could be interpreted as individual timeline of our project commits.
- With Git, we can create many of these alternative environments (i.e. we can create different **branches**) so other versions of our project code can exist and be tracked in parallel.
- That allows us to add new (experimental, unfinished, and potentially bugyy) features in separate brances, without touching the '*official*' stable version of our project code (which is usually kept on the **master** branch).
#### Creating a new branch

- `git branch <new-branch-name>`
- `git branch`
		Lists out current branch
		If it's a master or some other branch
- To go to master branch anytime:
	- `git checkout master`
	- This also gets us to the master 
	- Back to original
	- `git status`
	- Back form the dead.
	- `git branch crazycolors`
		- crazycolors
		- master
	`git checkout crazycolors`
		Creates a new duplicate of master at that time
		
#### Commiting  the modified branch
- `git status`
	- lists out the all modified files		
	- To add the modified files
	- use command `git add .`  translates to add all
	- use command `git commit -m "Add animated bg"` , this addes and modifed the files	in the master and makes this **branch** as **master**
**	- (HEAD -> crazycolors)**
#### Merging our branch
`git merge crazycolor`


[Notes on Notion: Introduction to Git](https://www.notion.so/Introduction-to-Git-ac396a0697704709a12b6a0e545db049)

`git push` uploads the code to cloud.
`git difftoll ` shows difference between your local changes and previous version of the file
[[meld]]
`git commit -m 'About the push, actually'` is used to give us impormation about the next push to the code.

It's always
`git add <file.name>` then 	`git commit -m "a telegram"`

![[Drawing 2021-05-31 00.48.42.excalidraw]]