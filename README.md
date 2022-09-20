# Git Exercice

`git` is a powerfull command that handle the versioning and decentralization of code for collaboration purposes.

In this Course, you'll learn how to use `git` and cover 80% of daily basis usage.

> :bulb:  I recommend that you take note of every command you enter in a cheat sheet.

## Prerequisites

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

Now, find how to change the remote URL of your repository

<details>
<summary>Solution</summary>

```bash
git remote set-url origin <URL>
```

</details>

### Commits

#### Setting Author and Commiter name and email

There are two methods to define Author and Committer name and email.
One is via the `git` CLI, the other is via environment variables.

1. Find via the `git` CLI how to

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

2. Find the common variables used by git

    <details>
    <summary>Hint</summary>
    Environment variables are in CAPS_SNAKE_CASE and for our case, they are prefixed by `GIT_`.
    </details>

    <details>
    <summary>Solution</summary>

    - GIT_AUTHOR_NAME
    - GIT_AUTHOR_EMAIL
    - GIT_COMMITTER_NAME
    - GIT_COMMITTER_EMAIL

    </details>

    You may be wondering what the difference is between author and committer. The author is the person who originally wrote the patch, whereas the committer is the person who last applied the patch. So, if you send in a patch to a project and one of the core members applies the patch, both of you get credit — you as the author and the core member as the committer.

    <details>
    <summary>Bonus : Use <code>direnv</code></summary>
    I recommend using environment variables alongside direnv to to this as it allows me to set different values for bunch of repos.

    Let's install [direnv](https://direnv.net/)

    ```bash
    brew install direnv
    ```

    Then we add the hook that will handle loading and unloading env vars

    ```bash
    # For Bash
    # Add the following line at the end of the ~/.bashrc file:
    eval "$(direnv hook bash)"

    # For Zsh
    # Add the following line at the end of the ~/.zshrc file:
    eval "$(direnv hook zsh)"

    # Reload your SHELL
    exec $SHELL
    ```

    Finally, create a `.envrc` in the directory where you want to load your env vars like this

    ```bash
    # .envrc
    export TEST_VAR=foo
    ```

    Allow `direnv` to read and execute the file

    ```bash
    direnv allow .
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

- [ ] 1. Clone a repo
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

### Merge Requests

Merging is the action to add all the commits from a source branch to a destination branch

<details>
<summary>Solution</summary>

1. Open remote git repository on your web browser

2. Create a new Merge Request or Pull Request

3. Review your changes in the MR files section

4. Add a description

5. Tag reviewer

</details>

This article sums up some good tips for reviewers <https://mtlynch.io/code-review-love/>

#### Open source Merge Request

Can you find out the little difference there is between your repository and public repositories ?

<details>
<summary>Hint</summary>
The difference resides in pushing rights and there is a keyword associated to open source contributing
</details>

<details>
<summary>Solution</summary>
Just a few people can push code and branches directly to public repositories.

In order to collaborate and suggest a change, you'll have to <b>fork</b> the public repository.

This action will make a full copy of the repository in your personal space.

Then you'll be able to push some modifications and when it's tested and ready to be merged into the public repo,
you need to open a Merge Request on the public repo with source: your_repo/your_branch and destination: public_repo/main
</details>

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

### Patching

It's informational, we don't use patching that much but sometimes you may need to send your changes as a file.
The way to do it is to create a patch from a commit.

Find commands to

- [ ] 1. create a patch from the last commit
- [ ] 2. apply the patch

<details>
<summary>Solution</summary>

```bash
git format-patch HEAD^
git am patch_file
```
</details>