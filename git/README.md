# Git

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

