# Git

Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency. Git is easy to learn and has a tiny footprint with lightning fast performance.

It outclasses SCM tools like Subversion, CVS, Perforce, and ClearCase with features like cheap local branching, convenient staging areas, and multiple workflows.

```shell
# Initialize a new Git repository
git init

# Add all changes in the working directory to the staging area
git add .

# Commit staged changes with a descriptive message
git commit -m "messgae"

# Push committed changes to a remote repository
git push

# Fetch and merge changes from a remote repository
git pull

# Clone a repository from a URL
git clone "url"

# Show the status of files in the working directory
git status

# Show commit logs
git log

# Create a new branch named branch_name
git branch branch_name

# Switch to the specified branch
git checkout branch_name

# Merge changes from the specified branch into the current branch
git merge branch_name

# Show remote repositories
git remote -v

# Remove unversioned files from the working directory
git clean -f

# Show unversioned directories and files that will be deleted
git clean -f -d -n

# Delete unversioned directories and files from the working directory
git clean -f -d

# Reset the special commit record
git reset --soft commit_hash
git reset --hard commit_hash
```

## Git-filter-repo

Git-filter-repo is a versatile tool for rewriting history. You can use it to remove large files in commits.

> https://github.com/newren/git-filter-repo

```shell
# Install
pip install git-filter-repo

# View files
git rev-list --objects --all | grep "$(git verify-pack -v .git/objects/pack/*.idx | sort -k 3 -n | tail -10 | awk '{print$1}')"

# Execute delete
git filter-repo --path "need remove path" --invert-paths --force
git filter-repo --path-glob '*.pdf' --invert-paths

# Add the remote URL and force push
git remote -v
git remote add origin "repo_url"
git push --force origin --all
```

