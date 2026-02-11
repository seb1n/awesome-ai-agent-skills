---
name: version-control
description: A skill for managing code repositories and version control workflows using Git and GitHub. It helps with initializing repositories, committing changes, pushing to remotes, and managing branches.
license: MIT
---

## Workflow

1.  Initialize a Git repository in a project directory.
2.  Stage and commit changes to the local repository.
3.  Create and manage branches for feature development or bug fixes.
4.  Push changes to a remote repository on GitHub.
5.  Clone existing repositories and pull updates.

## Usage

Use this skill when you need to track changes in your code, collaborate with others on a software project, or manage different versions of your files.

## Example

```bash
# Initialize a new git repository
git init

# Stage all changes
git add .

# Commit the changes with a message
git commit -m "Initial commit"

# Add a remote repository
git remote add origin https://github.com/user/repo.git

# Push the changes to the remote repository
git push -u origin master
```
