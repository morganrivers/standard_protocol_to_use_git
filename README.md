# Standard Protocol to Use Git

This tutorial will walk you through a standard Git workflow, which includes creating a new branch, checking its status, adding changes, committing them, and finally, pushing them to the remote repository. The workflow also includes how to prepare for a pull request.

Here, we'll be using two remotes: 'origin' represents your fork of the original repository, and 'upstream' represents the original repository itself.

## Preparing Your Main Branch

Before creating a new branch, ensure your local main branch is up to date:

```bash
git checkout main
git pull upstream main
```

This updates your local version of the main branch.

## Creating a New Branch

To create a new branch:

```bash
git checkout -b [branch_name]
```

Replace `[branch_name]` with the name you want for your branch.

## Saving Changes

After you complete a chunk of work:

1. Check the status of your changes:
   ```bash
   git status
   ```
2. Add the changes you want to commit:
   ```bash
   git add [file_names]
   ```
3. Commit your changes with a message:
   ```bash
   git commit -m "commit_message"
   ```
4. Push your changes to the origin remote for safekeeping:
   ```bash
   git push origin [branch_name]
   ```

## Preparing a Pull Request For Collaborative project
Before you open a pull request in a collaborative project, you need to fork the existing repository, create your own remote, create a new branch, and finally open a pull request to merge them.

1. In the project on github.com, find the "fork" button, and create a fork of the project.
2. To create your own remote, you need to use the following command:
   ```bash
   git remote add [remote name] [remote address]
   ```
   `[remote name]` is whatever short name you'd like that's not "origin"
   `[remote address]` is formatted as:
   `https://github.com/[other user]/[reponame].git`
3. Now follow "preparing a pull request" except instead of origin, use `[remote name]`

You only need to do step 1 and 2 once. Any future pull requests should use `[remote name]` instead of origin.


## Preparing a Pull Request

Before you open a pull request to merge your branch with the main branch:

1. Update your local main branch:
   ```bash
   git checkout main
   git pull upstream main
   ```
2. Push your updated main branch to the origin remote:
   ```bash
   git push origin main
   ```
3. Checkout the branch you were developing on:
   ```bash
   git checkout [branch_name]
   ```
4. Rebase your branch onto the updated main branch:
   ```bash
   git rebase -i main
   ```

## Additional Information

To give permissions for pushes and pulls:

```bash
eval `ssh-agent -s`
ssh-add ~/.ssh/[key_file_name]
```
Replace `[key_file_name]` with the name of your key file.

For more information about keys and ssh'ing, check out my other tutorial and helpful scripts for this:
https://github.com/morganrivers/how_to_ssh_key/
