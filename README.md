# Git Exercice

`git` is a powerfull command that handle the versioning and decentralization of code for collaboration purposes.

In this Course, you'll learn how to use `git` and cover 80% of daily basis usage.

> :bulb:  I recommend that you take note of every command you enter in a cheat sheet.

## Prerequisites

- an account at github.com
- add a ssh key to <https://github.com/settings/keys>
- a terminal
- `git`

## Exercices

### Create a new repo

You can go on Github and create a new repo in your personal space.
Then find out wich commands help you to

- [ ] 1. Initialize the repository
- [ ] 2. Add the remote URL to this local repository
- [ ] 3. Create a main branch (called `main`)
- [ ] 4. Push this branch to the remote

<details>
<summary>Hint</summary>

The steps are written in the first page on the created repository

</details>

<details>
<summary>Solution</summary>

```bash
mkdir new_repo # creates the directory
cd new_repo # move yourself into this directory
# Initialize
git init
# Set remote URL where to upload/download code
git remote add origin git@github.com:path/repo-name.git
# Create a main branch
git branch -M main
# Upload code
git push -u origin main
```

</details>

### Commits

#### Setting Author name and email

Define Author name and email via the `git` CLI.

Find via the `git` CLI how to

- [ ] Set this parameter for the specific repo
- [ ] Set this parameter globally

<details>
<summary>Solution</summary>

```bash
# Changing Your Committer Name & Email per Repository

$ git config user.name "John Doe"
$ git config user.email "john@doe.org"

# Changing Your Committer Name & Email Globally

$ git config --global user.name "John Doe"
$ git config --global user.email "john@doe.org"
```

</details>

#### Commit messages

As `git` is our principal tool to collaborate we tend to have it display meaningful messages.

Read [here](https://www.conventionalcommits.org/en/v1.0.0-beta.2/) how to compose your message

<details>
<summary>Solution</summary>

<code>feat(scope): change details</code>

</details>

#### Ignore files

Find how to give a list to `git` so it won't upload the files from the list

<details>
<summary>Solution</summary>
It's done by creating a `.gitignore` file. We can create one at the root of the repository or in a subdirectory.
The `.gitignore` files in subdirectory excludes files within this particular directory.

A useful website to generate `.gitignore` files related to a given coding language <https://www.toptal.com/developers/gitignore>
</details>

### Git branching

Here, let's play with branches. Branching means you diverge from the main line of development and continue to do work without messing with that main line.

[![Git Branching Exemple](https://git-scm.com/book/en/v2/images/basic-merging-2.png)](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging)

- [ ] 1. In your cloned repo
- [ ] 2. Create a new branch
- [ ] 3. Switch to that branch
- [ ] 4. Push this branch to the remote
- [ ] 5. Create another branch from main
- [ ] 6. Push this branch to the remote
- [ ] 8. Delete a remote branch
- [ ] 7. Delete a local branch

<details>
<summary>Solution</summary>

```shell
# Clone a repo
git clone <URL>
# You'll need to commit something if the repo is empty
touch README.md && git add --all && git commit -m "Initial commit"
# Create a new branch AND switch on it
git checkout -b new_branch_name
# OR
# Create a new branch from current
git branch new_branch_name
# Switch on it
git checkout new_branch_name
# Push branch to remote repository
git push --set-upstream origin new_branch_name
# Create a branch from main
git checkout -b another_new_branch_name main
# Push it
git push --set-upstream origin another_new_branch_name
# Delete remote branch : git push -d <remote_name> <branch_name>
git push -d another_new_branch_name another_new_branch_name
# Delete local branch
git branch -d another_new_branch_name
```

</details>

#### Review your code before pushing

Here we'll see how to show differences at each git step before pushing to the remote repo.

Find out how to

- [ ] 1. Show differences before staging files (before `git add`)
- [ ] 2. Show differences between staged files and origin (before `git commit`)
- [ ] 3. Show differences between committed files and origin (before `git push`)

<details>
<summary>Solution</summary>

```shell
# Edit files then
git diff
# Add files with git add then
git diff --cached
# git commit changes then
git diff origin
# Finally, you can git push
```

</details>

### Merge Requests

Merging is the action to add all the commits from a source branch to a destination branch.

<details>
<summary>Solution</summary>

1. Open remote git repository on your web browser

2. Create a new Merge Request or Pull Request

3. Review your changes in the MR files section

4. Add a description

5. Tag reviewer

</details>

This article sums up some good tips for reviewers <https://mtlynch.io/code-review-love/>

> :raised_hand: Tag a reviewer that is in another group. Continue with code of the other team after break time.

### Stashing

Stashing in git is very useful. It puts every changes in a "stash" some temporary place where to move changes.
It allows to 1) git pull new commits and handle merge commit after and 2) quick erase changes without loosing them.

Find commands to

- [ ] 1. stash edited files
- [ ] 2. stash edited files and new files
- [ ] 3. retrieve stashed files
- [ ] 4. delete a stash
- [ ] 5. display the content of the last stash
- [ ] 6. display the content of a given stash

<details>
<summary>Solution</summary>

```bash
git stash
git stash -u
git stash pop
git stash drop
git stash show -p
git stash show -p stash@{0}
```

</details>

### Logs

Here you'll learn how to display the history of commits.

Find commands to

- [ ] 1. display the content of the last commit
- [ ] 2. show the differences between your changes and the `main` branch
- [ ] 3. show the differences between your changes and the remote branch
- [ ] 4. show the differences between your changes and the remote branch (when files are staged after a `git add`)

<details>
<summary>Solution</summary>

```bash
git show
git diff main
git diff
git diff --cached
```

</details>

### Rebasing

Rebasing is a tricky, yet usefiul, command. It rewrites the history of commits. It's useful in 2 major cases :

- Update a feature branch with commits pushed to `main` after the branching
- Concatenate too many commits on a feature branch

Find commands to

- [ ] 1. retrieve commits from `main` branch
- [ ] 2. rewrite the history of commits from the original commit where your branch begins.
- [ ] 3. push after a rebase

<details>
<summary>Solution</summary>

```bash
git rebase main # get new commits
git rebase -i origin # reword and squash commits
git push --force
# --force is needed as we changed the history and we'll erase old commits
```

</details>
