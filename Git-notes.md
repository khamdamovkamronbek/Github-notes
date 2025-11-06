1. #Git - tool that use track changes
2. #Github - website that include git repository
3. #Repository - is a storage location where all the files, code, and history of a software project are kept.
    1.Remot 
    2.local
4. #gitint - Git will create a new directory named **.git** in your project folder. This directory contains all the information about your project's history and configuration.
5. #GitCommands:
	  1. git clone  ---> Download this project for the first time
	2. git add
	3. git push -u
	4. git pull   ---> Get the latest updates from the project.”
	5. git commit
	6. git init ---> It **creates a new Git repository** inside your current folder — meaning Git starts tracking all changes to files in that folder.
	7. git remote
	8. *git status*      --> tells you **what’s going on right now** in your repository ,what files are changed, added, deleted, or not yet tracked by Git.
	9. *git branch name*     -- > creates a new branch any name
	10. *git checkout created branch name*     --> switch to new created branch
	11. *git checkout -b any name*      --> both create and switch into new branch
	12.  echo "This line is added in test branch" >> note.txt
	13. *git log --oneline*         ---> show the history
	14. git merge ----> combines changes from **two branches** into **one branch**
	15. git stash (pop) - Save your current uncommitted changes temporarily

6. #Gitbranch - **separate version of your project** that lets you work on new features, experiments, or fixes **without touching the main code**.
7. #GitWorkflow = working directory (git add) - > staging area(git commit) - > repository
8. #Forking - a process where you create a personal copy of someone else's repository on GitHub.
9. #Branch 
	1. 1.The **main branch** (`main`) is your tree trunk — stable and official.
	2. .**Branches** are like smaller branches — where you can experiment safely.
10. #gitignorefile - tells Git **which files or folders to ignore** — meaning Git will **not track, stage, or commit** them.
11. #mergeConflict ---> Git can’t automatically decide how to combine changes because **two branches edited the same part of the same file**
12. #PullRequest ---> it’s basically a **request to merge your branch into another branch** (usually `main` or `develop`).
13. #gitRestore --> Git, please throw away my local changes and make `app.py` exactly like it was in the last commit, **does not delete your commit history** — it only affects _uncommitted_ changes or helps fix _merge conflicts_.
14. #GitRemote -->   just a **nickname for a repository URL** (usually on GitHub/GitLab/Bitbucket)
		git remote -v       ---->   see which URL 'origin' points to
		git remote add upstream <URL>   ----> add another remote (e.g., the original repo)
		git push origin main         ---> push to the online repo named 'origin'
		git fetch upstream           ---->  download updates from 'upstream'
		
15.      #MergeStrategies  ----> **different ways to combine** two sets of changes. 
		a. Fast-forward merge -- >Happens when the target branch (like `main`) **hasn’t moved** since the feature branch started.
		b. 3-way merge    --- > Used when **both branches have new commits**.
		c. Squash merge --->  Combines **all commits** from the feature branch into **one single commit** before merging.
		d. Rebase merge --> Instead of merging, you **replay your commits** on top of another branch.
