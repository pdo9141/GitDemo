Git Command
01) Visual Studio 2013 and up already has Git installed
02) Cloning, get clone URL so that you can bring respository down locally
	git clone https://nwcadence.visualstudio.com/DefaultCollection/MVA-Git/_git/demo
03) Now edit your files in any editor even Notepad
04) Show history: git log --oneline
05) Show status of working directory: git status (unmodified, modified, staged)
06) Stage file: git add index.html
07) Commit (if you don't use -m, editor will display where enter comments there): git commit -m "Add link to MVA"
	This commits to your local repository not online public repo
08) Commit to public repo: git push or git push origin
	This pushes your changes into the public online repo
	You will get rejected if someone else made a change and pushed before you even if folks pushed a different file
	You need to merge his changes into yours before you can push
09) Sync and merge (works well if no conflicts): git pull origin		
	After merge is done, run "git push origin" again 
10) Initializing Repo: git init
11) Cloning: git clone [url]
12) Stages are untracked > unmodified > modified > staged
13) Disregard changes: git checkout -- <file>...
14) The .gitignore file specifies files git needs to ignore
15) After initializing repo, to change all untracked files to tracked: git add -A 
16) What is a Branch? Just a file that is a pointer to a commit.
	Create branch: git branch [branch name]
	View branches: get branch
	Switch branches: git checkout [branch name]
	Shortcut create and checkout branch: git checkout -b hotfix
	Delete branch: git branch -d hotfix
17) Switching branches: git checkout testing (HEAD is now pointing at testing)
18) Use command: "gitk --all" to see visual representation of history of logs
19) Learn branching online: http://learngitbranching.js.org/?NODEMO or http://learngitbranching.js.org (get tutorial)
20) Merging, you "git checkout master" then "git merge [story]"
21) Merge: git merge hotfix
22) Hotfix workflow: create hotfix branch, make your changes, do a "git checkout master" then "git merge hotfix"
23) Get latest: git fetch origin
24) Leverage remote branches and repositories to work on more time consuming projects
25) Why rebase instead of merge? Code is all the same in the end, you get linear history.

Git in Visual Studio
01) Connect using the plug in icon (Connect to Team Projects, in Team Explorer - Home)
02) To default directory of where repositories are cloned, click plug in icon, click down arrow to the right of Connect, click Settings, click Git Settings
03) Click Team Explorer tab, click Changes, you can now Commit, Commit and Push, or Commit and Sync.
	Commit: commits locally
	Commit and Push:
	Commit and Sync: 
04) Click Unsynced Commits link to view what you need to push to the server
05) View "Incoming Commits" to see if you need to Fetch or Pull
06) When you click the "Sync" button, it will pull down locally, do a Fetch, do a Merge, do a Push
07) Keep in mind that VS still can't do everything Git command does but most common workflows work
08) Most of the time clicking the "Sync" button is fine
09) You'll probably always create branches for your changes
10) You can still go to the Git command and work, use "Open Folder in File Explorer" and Powershell
11) Right-click the Repository and select New Local Branch From… Enter develop as the new destination branch name, and select origin/master as the source branch. 
	I'd recommend not checking Track remote branch. This will track changes made to develop and will automatically apply them to master. This is not ideal since 
	we want to control changes, through code reviews, into the master branch. For some reason, Visual Studio will tick this box by default. Coincidentally, if 
	you create a branch from local instead of origin, the check box won't be there, which is our preference. The problem with creating new branches based on local 
	branches is that they could be stale, so you need to remember to pull or sync before you create a new branch.
12) Push: Copies all pending commits from my local machine to the server for the branch that I'm working on. 
13) Pull: Copies and commits from the server branch down to my local branch. In our case, we have no commits on our server branch yet.
14) Fetch: Fetches information about any new branches that have been created on the server. In our case, we have all the branches since we're the only ones working in the 
	repository at the moment. If another developer had created and published a branch, fetch would get the details about that branch and make you aware of it, if you needed to use it.
15) Sync: Sync is something Microsoft came up with. The sync keyword does not exist in Git. It performs multiple Git command—namely, fetch, pull, and then push, for your 
	convenience. If we wanted to get our changes onto the server branch, we could select either push or sync, and both would achieve the same objective for us.