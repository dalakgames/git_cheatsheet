# git_cheatsheet

-- Submodule Not Currently On any branch
git checkout -b newbranch
git checkout master
git merge newbranch
git branch -d newbranch

-- Update submodules
git submodule update --init --recursive
git pull --recurse-submodules

-- Move folder and tell it to git, without this submodules inside moved folders breaks
git mv OldFolderName NewFolderName

-- Always pull submodule when executing git pull
git config --global submodule.recurse true

-- Undo last commit --
git reset HEAD^

-- Reset repo to spesific commit
git reset --hard <sha1-commit-id>

-- Git diff - shows only the changed files' names
 git diff --name-only 0fe74c06676872391740896e58de77a81cb9a3b9

-- Tags
git tag v2.0.0
git push --tags
git tag <tag_name> <commit_sha>

git fetch --all --tags
git checkout tags/<tag> -b <branch>

-- Large File --
git lfs install - installs large file extention
git lfs track "*.psd" - treat psd files as large files, store the information at .gitattributes
git lfs track "*.so"
git lfs track "*.a"

-- Add Submodule
git submodule add https://github.com/chaconinc/DbConnector

-- Get remote url
git config --get remote.origin.url

-- Set remote url
git remote set-url origin https://git-repo/new-repository.git


-- Remove ignored files
git rm -r --cached .

-- Change to feature branch, merge master into feature branch
git checkout feature1
git merge master

-- Create a Git branch and checkout in one command:
git checkout -b <branch_name>

-- Create a new Git branch and checkout:
git branch <branch_name>
git checkout <branch_name>

-- Pull remote branch and switch to it
git switch <branch_name>

-- Create a new branch:
git checkout -b feature_branch_name

-- Push your branch to the remote repository:
git push -u origin feature_branch_name

-- Undo add
git reset

-- Remove branch 
git branch -d branch_name
git push <remote_name> --delete <branch_name> // remove remote branch

-- Change branch 
git checkout <branch>

Set a Git username:
$ git config --global user.name "Mona Lisa"



-- Remove Submodule
To remove a submodule you need to:

Delete the relevant section from the .gitmodules file.
Stage the .gitmodules changes git add .gitmodules
Delete the relevant section from .git/config.
Run git rm --cached path_to_submodule (no trailing slash).
Run rm -rf .git/modules/path_to_submodule (no trailing slash).
Commit git commit -m "Removed submodule "
Delete the now untracked submodule files rm -rf path_to_submodule


-- Duplicate git repo

mkdir foo; cd foo 
# move to a scratch dir

git clone --bare https://github.com/exampleuser/old-repository.git
# Make a bare clone of the repository

cd old-repository.git
git push --mirror https://github.com/exampleuser/new-repository.git
# Mirror-push to the new repository

cd ..
rm -rf old-repository.git  
# Remove our temporary local repository
