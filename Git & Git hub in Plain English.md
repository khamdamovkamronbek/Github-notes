#### What are Git and GitHub (really)?

- **Git**   → the tool on your machine that **tracks changes** to files.
- **GitHub** → the website that **stores Git repositories online** and lets teams collaborate with pull requests, reviews, and issues.
- A **repository**  → **storage space** like a **folder** for your project — but smarter.  It not only stores your files but also keeps **track of all changes** made to them over time.
	- There are two main types:
		- **Local Repository** – on your own computer.  
		    Example: a folder created after `git init`.
		- **Remote Repository** – on the internet (e.g., GitHub, GitLab, Bitbucket).  
		    Example: `https://github.com/yourname/myproject`
### First step: initialize or clone

###### **Option A**— Start a brand new repo
	git init
	
Notes: `git init`This creates a hidden **.git/** folder in your project—That’s Git’s “brain” — it stores all commits, branches, and history.
###### **Option B** — Download an existing repo
     git clone https://github.com/<you>/<repo>.git

Note: `git clone` - copy a repository from other on the internet (GitHub, GitLab, etc.) to your and automatically connects it to the GitHub version computer. 

Think of it like **downloading a project** — but smarter!  
Because it not only downloads files, it also includes **all the history, commits, and branches** of that project 

### The everyday Git workflow (muscle memory)

**Mental model:** working directory → staging area → repository.

1. **Working Directory** — where you _do your work_ that your normal project folder — where you **create, edit, or delete files**
		example: You edit `app.py` and add new code. Right now, the file is only **changed on your computer**, not saved in Git’s memory.

2. **Staging Area** — where you _prepare your changes_. When you’re ready to save some files, you use:
		`git add app.py`
	Note: Now Git knows **which files** you want to include in your next snapshot (commit).


3. **Repository** — where you _permanently save (commit)_
	1. `git commit -m "Added new feature"`
	Note: Now Git **takes a snapshot** of your staged files and stores them in the repository.

4. Push to **remote** (GitHub):
	   git push -u origin 'branch'
5. Pull updates from remote:
	    git pull
                   
### What is Branching?

A **branch** in Git is like a **separate line of work** — a copy of your project where you can make changes **without touching the main version**.

Example: You have a project on the main branch that works fine.
		Now you want to add a new feature — but you don’t want to break the main code.  So you make a new branch:

**Creating and switching to new brand**

		git branch feature/readme-badge   # Create new branch
		git checkout feature/readme-badge   # switch to new brand
		git checkout -b feature/readme-badge   # create AND switch

**List branches**
		`git branch`    #  give all branches 
		
**Why branch?**
	- Experiment freely
	- Keep `main` stable
	- Review changes via Pull Requests

### Remote basics (origin, upstream)

A **remote** is simply a **Git repository stored online** (like on GitHub, GitLab, or Bitbucket).  
It’s a **cloud copy** of your project that you can connect your local computer to.
Think of your Git project like Google Docs:
- You have a **local copy** (on your laptop).
- There’s also an **online copy** (on GitHub).
- Both can be synced with each other.

#### 1. Origin
This is the **default name** for the **remote repository you cloned or created**.

#### 2.Upstream
This one appears **when you fork someone else’s project** on GitHub.

Notes:  A **fork** means making **your own copy** of someone else’s project **on GitHub** (not on your computer yet).  
It lives **in your GitHub account**, and you can change it freely.

   Let’s say:
- You fork someone’s repo → now you have **your copy (origin)**
- The original project (the one you forked) is called **upstream**
So:
- `origin` → your fork
- `upstream` → the main/original repository

**Commands**
	- `git remote -v`     --> see URLs that this shows which GitHub repositories your local project is connected to
	
	- `git remote add origin your-fork-URL`     ---> **Connect your own GitHub fork** to your local repo
	- `git remote add upstream original-URL` **Connect the original project (the one you forked from).**our local project also knows where the **main source  project** lives — so you can **get updates** from it later.
	- `git fetch upstream`  -->  This pulls all new commits and branches **from the original repo** but doesn’t change your code yet — it just updates your local info
	- `git push origin main`    --> **Upload your latest commits** from your computer → to your GitHub fork.

### Status, history, and quick helpers

**Check what’s going on**:
		 git status

**View history (short):**
		git log --oneline

**Temporarily stash unfinished work:**
	Notes:  
	Temporarily put away my unfinished work — I’ll come back to it later.
	Example: You’re working on a new feature, you edited some files...  
			then suddenly your team says: Hey, switch to another branch and fix a quick bug!
			But you can’t switch branches right now — because you have **unsaved (uncommitted)** changes.
 	So you use:
			`git stash`
		`git stash pop`  --> Bring back your hidden changes and continue working

### Merging & Pull Requests

- **Merge**  means that combines changes from **another branch** into your current one.
	 Simple idea:
		Imagine you created a new branch to work on a feature:
		You make some changes in `new-feature`.  
		Once it’s ready, you want to **add those changes into `main`** — that’s what `merge` does.
		 `git merge new-feature`

-  **Pull Request (PR)** is a request to merge your changes into `main` (or another branch). It enables code review, CI checks, and discussion.
	  Simple idea: 
	  Imagine you fork or clone a repository and worked on a new feature in your **own branch**:
	  You make some changes, then commit and push and go to your **GitHub page**, and you’ll see a button:  “Compare & pull request”
	  Click it → write a short message explaining what you did → click **“Create Pull Request.”**
	  Now the project owner can:
	  - Review your code
	  - Comment on it
	  - Approve or request changes
	  - Finally, **merge** it into the main project
	 

## When Git can’t auto-merge: conflicts

A **merge conflict** happens when **two branches edit the same lines**. Git needs you to decide which content wins.

**Fix recipe:**
		1. Try to merge or pull
		2. Open conflicted files; look for markers like `<<<<<<<`, `=======`, `>>>>>>>`
		3. Keep the right lines (or combine)
		4. `git add <file>` then `git commit` (or continue merge if prompted)
		
## Merge strategies: which one to use?

Let’s **learn merge strategies (Fast-forward, Squash, and Rebase)** through **hands-on practice** — step by step.

Step 1. Create a small test project

		mkdir git-merge-practice
		cd git-merge-practice
		git init
		echo "Hello world" > app.txt
		git add .
		git commit -m "Initial commit"

Step 2. Create a new branch

		''' 
		git checkout -b feature
		echo "Feature line 1" >> app.txt
		git add app.txt
		git commit -m  <Add feature line 1>
		'''
Step 3. **Fast-forward merge**

		''' 
		git checkout main
		git merge feature 
		 '''

1. Notes:
	    - Used when the target branch **hasn’t moved** since your branch diverged.
	    - Result: looks like a straight line of commits (no merge commit).
	    - **Use when:** simple, linear history is fine.

Step 4. **Squash merge**
	Let’s create a new branch again:
	
	'''
		git checkout -b feature2
		echo "line 2" >> app.txt
		git commit -am "Add line 2"
		echo "line 3" >> app.txt
		git commit -am "Add line 3"
	'''
	
Now you have **2 commits** in your branch.
	
		`git checkout main`
		`git merge --squash feature2`
		`git commit -m "Add lines 2 and 3 (squashed)"`

Notes:
	    - Combines all commits on your branch into **one** before merging.
	    - **Use when:** you want a clean history (one commit per feature/fix).


Step 5. **Rebase** (alternative to merge)
##### Add a new commit on main
	`echo "main update" >> app.txt`
	`git add app.txt`
	`git commit -m "Main updated"`

##### Create a new feature branch
	`git checkout -b feature3`
	`echo "feature 3 line" >> app.txt`
	`git commit -am "Feature 3 line added"`

Now rebase:
		`git rebase main`
		Notes:
	    - **Replays your commits** on top of another branch, creating a linear history.
	    - **Use when:** you prefer a tidy, linear log; okay rewriting local history.
	    - Be careful rebasing **shared** branches.



