## Learn GitHub in 20 minutes
- [[Learning Git in 15 Minutes]]
- `git push -u orgin master`

### What happens when somebody else makes changes?
- Add collabarators by going to setting
- We have to pull where, brach, the changes have been made
```ad-warning
>commit changes and then pull form remote
Check using `git status`

```

`git pull origin master`

### New branches
```shell
$ git checkout -b relaxing
Switced to a new branch 'relaxing'
$ git status
On branch relaxing
noting to commit, working tree clean
$ git status
....
.... 
modified: playlist.txt
no changes added to commit (use 'git add' and/or 'git commit -a')
$ git add playlist.txt
$ git commit -m "add relaxing songs"
.....
.....
1 file changed, 7 insertions 
$ git push -u origin relaxing
```

### clone a repository from GitHub using terminal
- copy the url
```ad-caution
don't clone a repository into another repository
```
- create a new directory using `mkdir`
```shell
git clone <paste url.git>
```
This will create all the history as well, everything.

- You can't push to a open source code without a permission

### Try and commit to a open-source project
- make a pull request
- `fork` a repository, makes a exact current copy of the repository, it'll will be your branch and then
- you can a make a request 
	- they can reject it or accept it, the they being developers
	- accepting it by merging it
- `fork` 
- then clone the forked repository
	- not in an existing repository
- make changes
- `add`
- `commit`
- double check the `git remote -v`
-  `git push -u origin master`
> this branch is 1 commit ahead of github-master

- Click on **pull request** 
- Review and then 
- **create pull request**
- Add comments
	- **create pull request**
- then wait

### accepting or rejecting the pull request
- Click on review change and select form
	1.  comment
	2.  Approve
	3.  Request changes

- **merge pull request**
- **confirm merge**
- if you want to get the changes
- you need to pull the changes down
- `git pull origin master`