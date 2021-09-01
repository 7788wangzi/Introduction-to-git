## Git Command Lines

### Two Types of VCS

- centralized version control  
- distributed version control 

git is a distributed version control system.  
each computer store a full database, you don't need to connect to server to get a file or update a file.

server - reprository  
====|====  
====|====|computer1 - repository  
database=|computer2 - repository  
======== |computer3 - repository  

git three main states: ***committed, modified, staged***

**committed** means that the data is safely stored in your local database.  
**modified** means that you have changed the file but have not committed it to your database yet.  
**staged** means that you have marked a modified file in its current version to go into your next commit snapshot.  

### Git Command lines

#### 1. For create a local repository first

First, you create a folder in your disk, then use `git init` to make this folder a repository.  

    mkdir createdlocal
    cd createdlocal
    git init


you can see the empty repository with commandline `ls -ah`.


get the commit status  

	git status

>Note: git status only check the diff of his local version with the last push version of his own, it doesn't identify the changes pushed by other people.

staging and commit 
   
	git add <file>  
	git commit -m "comment goes here"  

skip staging, directly commit

	git commit -a -m "comment goes here"

get differences

	git diff --staged
	git diff --cached

delete a local file

	git rm <file>

untrack a file

	git rm --cached <file> -f

rename a file

	git mv <fileA> <fileB>
	git commit -m "comment goes here"

view committed version
	
	git log  
	git log -p -2  
	git log --stat  
	git log --pretty-oneline  
	git log --pretty:format:"%h  %an, %ar  : %s"  
	git log --since=1.weeks  
	

unstage a staged file

	git reset head <file>

unmodifying a modified file

	git checkout --<file>

rollback to a previous version  commit number "e77ab46b2800c8c758a05985dfa428a12773ed14"  

    git reset --hard e77ab46b2800c8c758a05985dfa428a12773ed14

then you will get a message "HEAD is no at 10c4dde XXX"



#### 2. Work with Remote repository
clone a remote repository, cd to the expected path in local, then run:

	git clone https://github.com/7788wangzi/git_ws10.git

or add local repository to a remote location

	git remote add [name] [url]
	E.G. git remote add origin https://github.com/7788wangzi/git_2.git

check remote version

	git remote -v

push local update to remote

	git push [remoteName] [localBranchName]

pull remote repository to local

	git pull [remoteName] [localBranchName]

stop mapping local and server

	git remote rm origin

create local branch

	git branch [branchName]
	E.G. git branch 117

switch to branch 117

	git checkout 117

sync branch to remote

	git push origin 117

delete remote branch

	git push origin :heads/117

delete local brach

	git branch -d 117

get a specific branch from server (for clone project only)

	git branch -b 1118 origin/1118

merge a branch to current branch

	git merge 1118

Overwrite the local branch with the remote branch, when your commit in local branch is ahead of the remote branch, and you don't want to keep the local changes, then you could overwrite the branch with the remote branch

```cmd
git fetch --all
git reset --hard origin/digital-literacy
```

List all branches
```cmd
git branch
```

List all local branches
```cmd
git branch -a
```

List all remote branches
```cmd
git branch -r
```

#### 3. Work with multiple branch
In order to keep main branch to be always the workable branch:
- When main branch is updated after working branch being created, Always Use `git rebase` to make sure the integration is done in working branch and everything works fine before pull request to main branch.
- If you use `git merge` to merge changes back to main branch directly without `git rebase`, you have no idea whether the integration works or not after merged to main. In this way, you cannot keep main a workable branch at all times.

**Usage of `git rebase`:**
Before rebase your working branch M1, you should pull the latest main branch to your local.
```git
git checkout main
git fetch --all
git pull origin main
```

Swtich to M1 branch and run rebase command:
```git
git checkout M1
git rebase main
```
then, it switches to a new branch for resolving the merge conflicts, Pls manually edit the files to resolve conflicts, then run following commands to continue the rebase.
```git
git add -A
git commit -m "resolve conflicts"
git rebase --continue
```
Then, it switches back to M1 branch and it's rebased.

#### 4. Issues

if you runinto following issues

> Another git process seems to be running in this repository, e.g.
an editor opened by 'git commit'. Please make sure all processes
are terminated then try again. If it still fails, a git process
may have crashed in this repository earlier:
remove the file manually to continue.

You can use following command to resolve it  

    rm .git/index.lock

Note: Not git `rm .git/index.lock`
