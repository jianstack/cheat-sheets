https://git-scm.com/docs

## No you are NOT Already up-to-date.
git fetch --all

git reset --hard origin/master

## reset a file
git checkout filename

## Resets the index and working tree.
git reset --hard af64315 

## Merge conflicts
git mergetool

## Stage and unstaged changes
git diff HEAD

## Show changes between two commits
git diff commit1 commit2

## List the change dates and authors for a file
git blame [file]

## List all branches verbose
git branch -av

## Switch branch
git checkout my_branch

## Delete branch
git branch -d my_branch

## Create branch
git branch new_branch

## Merge branch_a into branch_b
git fetch --all

git checkout branch_a

git merge branch_b

## revert to a commit
git revert af64315