# Git-Cheat-Sheet

Notes with commit tips, branching strategies, command shortcuts and more.


<br />

## Table of contents

- [Good Git commit tips](#keyboard-keys-cheatsheet)
- [Github Flow](#github-flow)
- [Naming conventions for branches](#naming-conventions-for-branches)
- [Git command shortcuts](#git-command-shortcuts)


<br />

## Good Git commit tips
Mostly based on [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/).
<br />

**Conventional Commits** define a standard format in commit messages.It lets you easily scan valuable context about your changes.

Commit message should be interpreted as if it’s about to be applied, rather than about what have just been done.

Your commit message should be concise and state the context of the change.

Ensure that it is short and use an imperative mood.

<br />

### Commit message structure

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

<br />

### Commit Types
The ```<type>``` field provides the context for the commit. It communicates the intent of the change that was made.

<br />

| ```<Types>``` | Definition |
| --- | --- |
| feat | a new feature |
| fix | a bug fix |
| style | changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc) |
| refactor | a code change that neither fixes nor adds a feature |
| test | adding missing tests or correcting existing tests |
| docs | documentation only changes |
| chore | other changes that don't modify src or test files |
| build | changes that affect the build system or external dependencies (example scopes: gulp, broccoli, npm) |
| ci | changes to our CI configuration files and scripts (example scopes: Travis, Circle, BrowserStack, SauceLabs)Deprecate: |
| perf | a code change that improves performance |
| revert | reverts a previous commit |

<br />

### Scopes *(Optional)*
The ```<scope>``` field is optional used describing with a noun a section of the codebase.

<br />

The first word in your commit ```<description>``` should be for example:

- add
- create
- refactor
- fix
- release
- document
- highlight
- format
- allow 
- implement
- modify
- update
- remove
- delete etc…

<br />

### Body *(Optional)*
```[optional body]``` is optional with additional details in the commit describing the change that was made or feature that was added.

<br />

### Footer *(Optional)*
```[optional footer(s)]```  is optional which can provide additional metadata for a commit. It alerts readers and tools to significant changes such as breaking changes or can link commits to issues or pull requests.

<br />

### Rules of a great Git commit message
- Separate subject from body with a blank line
- Limit the subject line to 50 characters 
- Stay consistent with the style of commits (ex. first letter of commit uppercase or lowercase)
- Do not end the subject line with a period
- Use the imperative mood when in the subject line
- Wrap the body at 72 characters
- Use the body to explain what/why the change was made. (Optional)
- Remove unnecessary punctuation marks
- Make sure to follow top conventions throughout all project

<br />

### Few examples of good git commits
- docs: add short circuit to hook example
- docs: fix typo in code inside README.md 
- fix(deps): update dependency cz-conventional-changelog to v3
- fix(deps): update dependency lodash to v4.17.15 
- chore: update mocha, other dev deps 
- fix(node): remove node 6 and 8 support 
- chore(deps): update dependency semantic-release to v15.13.18 
- fix: update dependencies for security 
- fix(deps): update dependency lodash to v4.17.14 
- docs: highlight pre-requisties and bubble up related sections 
- fix(cli): allow argv to be overridden in bootstrap 
- feat(cli): implement --hook option for git hooks integration 
- test(ED-439): add tests for Modal component
- style: format code with new prettier config

<br />

*More examples in [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) official documentation.*

<br />

## Github Flow
Github Flow is a branching strategy used by Github. It is the easiest and best suggested for small projects with quick release.

<br />

### Github Flow Process

1. Create Branch
2. Edit Branch
3. Create a Pull Request
4. Merge Pull Request
5. Delete Branch

<br />

Great Github flow explanation with visual illustration can be found [here](https://www.alexhyett.com/git-flow-github-flow/) as well as in [Github Flow official documentation](https://docs.github.com/en/get-started/using-github/github-flow) on Github.

<br />

### Delete branching issue after merge
Github has an option to delete a branch after merging of pull request. After a pull request has been merged, you'll see a button to delete the branch. This action will delete the branch **only in remote.**

<img src = "README_images/button-delete-branch.png" width="500" height="80"/>

<br />
In order to delete the branch locally we have to perform number of commands below:

<br />

Let's say, our branch to delete is ```feature/demo```

<br />

1. **List branches in local machine**

   The command ```git branch -a``` shows the test branch ```feature/demo``` is present on local and also present on remote.

    <img src = "README_images/list-branch.png" width="400" height="100"/>

   <br />

2. **Prune/Cleanup the local references to remote branch**

   The command ```git remote prune origin --dry-run``` lists branches that can be deleted/pruned on your local. An option ```--dry-run``` is needed.

    <img src = "README_images/check-prune.png" width="450" height="60"/>

   <br />

    Now go ahead and actually prune/cleanup the local references by running the command ```git remote prune origin```. Note that you don't need an option ```--dry-run```.

    <img src = "README_images/prune.png" width="450" height="60"/>

    <br />

    Again, run the command ```git branch -a``` will show the local status of branches and there you can notice that ```remotes/origin/feature/demo``` has been removed, but not the local branch ```feature/demo```.
    
     <img src = "README_images/removed-remote.png" width="400" height="60"/>

    <br />

3. **Delete local branch**
    
    > Make sure to switch to some other branch than the one to be deleted.

    In order to delete local branch ```feature/demo```, we have to perform command ```git branch -d feature/demo```

    <img src = "README_images/delete-branch.png" width="400" height="35"/> 

<br />

## Naming conventions for branches
A crucial aspect of using Git effectively is the proper usage and naming of branches. A branch in Git is essentially a unique set of code changes with a unique name. It is important for maintaining clean and understandable codebase.

<br />

### Basic Rules

<br />

| Rule | Definition |
| --- | --- |
| lowercase and hyphen-separated | lowercase for branch names and hyphens to separate words (```feature/new-login``` or ```bugfix/header-styling```) |
| alphanumeric characters |  use only alphanumeric characters (a-z, 0–9) and hyphens. Avoid punctuation, spaces, underscores, or any non-alphanumeric character |
| no continuous hyphens | do not use continuous hyphens. ```feature--new-login``` can be confusing and hard to read |
| No trailing hyphens | do not end your branch name with a hyphen (```feature-new-login-``` is not a good practice) |
| descriptive | the name should be descriptive and concise, ideally reflecting the work done on the branch |

<br />

### Branch Prefix
Prefix in branch names help to quickly identify the purpose of the branch. Below are common types of branches used with their prefixes:

<br />

| Type | Prefix | Definition | Example |
| --- | --- | --- | --- |
| feature branch | ```feature/``` | develop new features | ```feature/login-system```
| bugfix branch | ```bugfix/``` | fix bugs in code | ```bugfix/header-styling```
| hotfix branch | ```hotfix/``` | made directly from the production branch to fix critical bugs in the production environment | ```hotfix/critical-security-issue```
| release branch | ```release/``` | prepare for a new production release | ```release/v1.0.1```
| documenation branch | ```docs/``` | write, update, or fix documentation | ```docs/api-endpoints```

<br />

### Few examples of good branch names
- ```feature/T-456-user-authentication```
- ```bugfix/T-789-fix-header-styling```
- ```hotfix/T-321-security-patch```
- ```release/v2.0.1```
- ```docs/T-654-update-readme```

## Git command shortcuts

