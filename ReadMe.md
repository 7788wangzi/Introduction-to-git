abc
## Brief introduction to Git
**Git** is a *distributed* version control system, which is a bit different from the team foundation server(the team foundation server is *centralized* VCS). In git, the **repository** is an important concept, data are stored in repository. Server has a repository on server, client computers have local repository on themselves. Therefore, in git system, each client computer has a full database, you no longer need to connect to server and check-out a file before you want to modify the file. That comes two benefits:  

+ Faster, end user would not sync files from server each time. As all files are stored in its client computer, end user modify the tracked file just as modify the local file.  
+ Offline work, version control operations are done in local repository, end user can work with version control system even when he/she doesn’t have network connection.

There are three main states in git, they are ***modified***, ***staged***, and ***committed***: 
 
+ modified means that you have changed the file but have not committed it to your database yet.
+ staged means that you have marked a modified file in its current version to go into your next commit snapshot.
+ committed means that the data is safely stored in your local database.

Git has a set of command-line, with git command-lines, user can track files, make branch in local repository, and also can push the local data to remote repository on the server.

install git, please go to [download](http://www.git-scm.com/downloads).

use git, if you install the git to default directory, then add below path to your system environment: 

	;C:\Program Files (x86)\Git\bin\;C:\Program Files (x86)\Git\libexec\git-core

for git command lines, go to [Git Command line!](https://github.com/7788wangzi/git_ws10/blob/master/gitCmdline.md)

for how git resolves push conflicts, go to [Push Reject](https://github.com/7788wangzi/git_ws10/blob/master/PushReject.md)

### Show something cool  

([EMOJI](http://www.emoji-cheat-sheet.com/)), supported by Github

:notes:  
:pray:  
:v:  
:thumbsup:  
:dancer:  
:sweat_drops:  
:cn:  

### Resources
[1] Step by step setup git server by
[CopSSH+msysGit](http://www.codeproject.com/Articles/296398/Step-by-Step-Setup-Git-Server-on-Windows-with-CopS)  
[2] Learn Git from scratch
[Jump Start](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)

