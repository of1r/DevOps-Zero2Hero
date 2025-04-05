# Branches
    
Branches enable us to work on multiple ideas in parallel. If we make changes on one branch, they do not effect the other branches (unless we merge the branches).

![a visualization of branching](resources/branching.png)


In git we are always working on a branch, the default one is `master` .

### Head
    
  Head is a pointer that refers to the current branch in your repo.
    
- `git branch` - List all existing branches. The branch that has a `*` in front of it is the branch we are currently on.
- `git branch branch-name` - Create a new branch, based upon the current HEAD . It does not switch to the branch.
- `git switch branch-name` - Switch to a different branch. There is an older command which is `git checkout branch-name`
- `git switch -c branch-name` - Creates a new branch and switches to it.
- `git branch -d branch name` - Deletes the specified branch, you can’t delete a branch if you’re in it.
- `git branch -m new-name` - Renames the branch, you have to be on the the branch to rename it.

##### Switching Branches With Unstaged Changes
    
    💡 When you have unstage changes they will come with you to the branches you switch to, if you have uncommitted changes git will yell at you.