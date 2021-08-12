# GIT

- Commits
- Multiple users
- Merging
- Source Control Server

## WorkFlow

  - Local
    - Initialize repo
    - Add and commit changes
    - Branch and merge/rebase
    - Push Changes
  
  - Remote
   
    - Clone the repo
    - Add and commit changes
    - Branch and merge/rebase
    - Pull and merge/rebase
    - Resolve merge conflicts
    - Push changes
 
  - Github:
    
    - Fork Repository
    - Make a Pull request
    - Discussion Issues
    - Actions and Codespaces




## Two step for commit

- Staging and Commiting 


```
git status -> shows the status of commits. Shows the untracked files. 

git add <file> -> staging 

git commit -m"description of the snapshot" -> commit. Taken the picture of all the changes to the staging

git status again the working tree will be clean

```
---

## Three state architecture

1st state --> Working directiory (OS)
   
  |
   
   `git add`

Intermediate stage --> Staging area... changes

 |
 
 `git commit`


3rd state --> Commits. All the commits. (Commit history)

---

**Think changes not file** 

**You can have a long commit message if you skip the -m flag**

---

## Seeing previous commits

  
    git log

    // unique id to identify the commit
    // Author and date

    // Shows commit in reverse chronological order

    - n --> show number of commits
    -- author -> who authored (`as`)

    -p --> see what has been changed

---

## Deletion

Delete is also treated as a change. If we commit after deletion than the deletion is commited.

---

## Undo all the changes to local files

git checkout --> Switch branches or restore working tree files.

Undo or revert back to the previous commit before new changes being staged. 
  
    git checkout -- <file name>

    giit checkout -- .

---

## Unstaging file with git restore

Restore specified paths in the working tree with some contents from a restore source. 

    git restore --staged<filename> to unstage

---

## Ammend the last commit

    git commit --amend

 - Not creating a new commit. Update to the last commit. 

---

## view changes with git diff

    git diff 

All the changes made that are not in the staging area.

For the staging area
  
    git diff --staged

Can see just one file also.

---

## Using git ignore

IF we have some files that we don't want git to be tracked. For example: IDE files, project info. 


Create a .gitignore file and add the file in .gitignore


Can put directories as well. for example build/

--- 

## Branching 

- A commit is :


  - Git keeps track of the state of the code. It keeps the metadata of the commit. Who made it? When? These get save with the commit. **The commit has a pointer to the previous commit.** ***Like a linked list*** A commit hash is generated. A unique id for the commit. Hash is generated out of the state but is a one way function. The hash is referred to as **checksum** .  <u> The commits are chained</u>

<br>

- What is Branching?

  - Branch out from the current branch and do the bug fix or add the feature. They might share the files but change itself is not changed. 

    - Copy of the source code. 
    - Add keep track. How?
     
      - Current state of each stream. (Pointer to the commit)
      - All previous commits in that branch/stream. (Commits are chained)


Default branch is the master. `Git status` shows current branch.

    //  shows all the available branch. * is the current branch.
    git branch

    // create a branch
    git branch <name> 

    // switch between branches
    gti checkout color-experiment
     // but now there is no different from master
    // current branch would be the new branch


### Fast- forward merge

  - If one branch is ahead of another. Just change the pointer of the lagging to the forward. 

      ```
      git merge <branch>
      ```

### No fast forward 

 Suppose the main branch and another branch have changes that conflic each other. Git allows to merge using recursive strategy. A merge commit will be created. 


 **What if there is overlap?**

  - A merge conflict will occur. How to reslove?

    Compare between the branches changes and keep the one you like.


## Deleting branches

  
    git branch -d <name of the branch> 

    // can't delete the current checked out branch

 
 ## Go back to a previous commit 

   
    git checkout <Commit hash>

The curtrent  pointer head would be in a detached state. A new branch can be created and given a name. 


## Rebasing 

The comment in the extra branch are needed but we don't want to merge. We can bring commits from another branch and applying to the master branch almost ad if it were done on the master branch. 

- Have to rebase from the side branch whose tail we want one the head of the master.
- Then on master we do the fast forward merge


      // On side branch
      git rebase master

      // fastforward merge in master
      git merge <branchname> 