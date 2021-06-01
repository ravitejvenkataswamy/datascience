[[Learning Git in 15 Minutes]] form Colt Steele
[[Git tutorial 4 Basic Commands add, commit, push]]

---
>Backing all the obsidian data
1.  Initialize the local directory as a Git repository.
    
    ```shell
    $ git init -b main
    ```
1. Add the files in your new local repository. This stages them for the first commit.

```shell
$ git add .
```
Adds the files in the local repository and stages them for commit.
~~To unstage a file, use~~
```shell
git reset HEAD YOUR-FILE
```

1. Commit the files that you've staged in your local repository.

```shell
$ git commit -m "First commit"
```
Commits the tracked changes and prepares them to be pushed to remote repositoty.
~~To remove this commit and modify the file, use~~
```shell 
git reset --soft HEAD ~1' and commit and the file again.
```
### Setting up for remote push
1. Copy the remote repository URL


2. In Terminal, add the URL for the remote repository where your local repository will be pushed.
```shell
git remote and origin <REMOTE_URL>
```
- Sets the new remote
```shell
git remote -v
```

- Verifies the new remote URL
1. Push the changes in your local repository to GitHub
```shell
git push -u origin main
```
- Pushes the changes in your local repository up to the remote repository you specified as the origin

[For more](https://docs.github.com/en/github/importing-your-projects-to-github/importing-source-code-to-github/adding-an-existing-project-to-github-using-the-command-line)

- [ ] Should start learning [[GitHub]] from this Thursday ^ftaqe54

### .gitignore file
      

echo ".obsidian/cache

dquote> .trash/

dquote> .DS\_Store" > .gitignore
