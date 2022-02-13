# Ron's git/github/development Notes

This repository contains my technical cheatnotes and has evolved over time. The content is shared between this README file, and in the wiki for this repository.

## Contents
1. [git/github: Guidlelines for registering and maintaining a project](#gitgithub-guidlelines-for-registering-and-maintaining-a-project)
1. [wiki: github Wiki Markup Cheatsheet](../../wiki/github-README-Wiki-Markup-Cheatsheet)
1. [Using a Python Virtual Environment](../../wiki/Python-Virtual-Environment)
1. [Building a Django project](../../wiki/Django-Project)

***

# git/github: Guidlelines for registering and maintaining a project

## On a local machine

### Add name, email, push mechanism
[[ One time activity (loads ~/.gitconfig) ]] 

```
git config --global user.name "Ron Grimes"
git config --global user.email ron.grimes@pobox.com
git config --global push.default simple
```  
`push.default`  
git will refuse to push if the upstream branch’s name is different from the local one. This is the safest option and is suited for beginners. (ref: [Git - git-config Documentation](https://git-scm.com/docs/git-config#Documentation/git-config.txt-pushdefault))


Alternative: `matching`.  
[[ When push.default is set to 'matching', git will push local branches to the remote branches that already exist with the same name. ]] 

### Set env values
bash
```
GIT_EDITOR=vim
export GIT_EDITOR
```

### Check global values   
`git config -l`

---

### Create project on Github
Project: projectname

Step 1. Create a new repository, with required name.
* Give brief description (optional)
* Do not add files (example: README.md, LICENSE, .gitignore)
* Click **Create Repository**

Step 2. Collect the code in `…or create a new repository on the command line`
* Load to the clipboard, or other transfer means

Step 3. On the local platform (Raspberry Pi, Mint, etc.)
* `cd` to project directory
* This directroy can have project files but must not be using `git`. (Check for the presense of the `.git` directory)

Step 4. Run the code collected above.

```
echo "# projectname" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/rongrimes/projectname.git
git push -u origin master
```

This will:
* Create a default README.md
* Initialize git
* Commit and upload local files to github repository  
Note: Github will substitute in correct values for username and projectname.]

### Notes
1. Use `git add -A` to add all files.
1. Use [`gitignore.io`](#) to build a .gitignore file for the project.

***

## License file
On github:
* Click `<>Code` to see current files.
* Click `Create new file`
* Filename: license (a button will appear to the right.)
* Click `Choose a license template`
* Choose MIT (or other)
* Click `Review and submit`
* At bottom of the page:
  * Click `Commit directly to the master branch. `
  * Click `Commit new file`

***

## .gitignore
On github:
* Click `<>Code` to see current files.
* Click `Create new file`
* Filename: .gitignore (a button will appear to the right.)
* Click `Choose .gitignore template` (optional)
* (Optional) Choose Python
* At bottom of the page:
  * Click `Commit directly to the master branch. `
  * Click `Commit new file`

### Notes
* Use [`gitignore.io`](https://gitignore.io) to build a .gitignore file for the project.

***

## Sync with development platform
```
git pull
```

or ```git pull origin master``` - to only get _master_ branch updates

`git status`  to review

You are now set up to develop the project
---

### Initial/Early actions
`git add <files>`  
`git add -A` for all files

### Remove files from the repository
`git rm <options> <files>`

WARNING!! BY DEFAULT `rm` deletes a file from the repository, AND from the filesystem.

#### Options
`<filename>`  
The files to remove. You can use filename / path to a single file, multiple filenames (delimited by spaces) and wildcard patterns (e.g. test.*).
 
--cached  
Removes the file only from the Git repository, but not from the filesystem. BY DEFAULT, the git rm command deletes files both from the Git repository as well as the filesystem.

-r  
Recursively removes folders. When a path to a directory is specified, the -r flag allows Git to remove that folder including all its contents.

--dry-run  (-n)  
Files are not actually removed. You will see the files that Git would remove - but no files are actually deleted.

***
### Commit files   
Use editor to add descriptive content.

`git commit`

alt: 

`git commit -am "messsage"`   [[ commit all files, with message ]]  

`git log` (run after the first commit)
   
### Upload to Github
`git push`  (requires login)   
or `git push origin master` - to only push _master_ branch updates

### Download
Use this to get the latest from _github_ - often after updating README.md.  
`git pull`  
or ```git pull origin master``` - to only get _master_ branch updates

***

## Operational cycle

Best practices:
* A successful Git branching model: http://nvie.com/posts/a-successful-git-branching-model/
* A Git Workflow for Solo Projects: https://sdlambert.github.io/2015/04/09/git-workflow-for-solo-development/
* `solo-development` in `softwareengineering.stackexchange.com`: https://softwareengineering.stackexchange.com/questions/tagged/solo-development

From here, solo-development sites suggest a single branch (say "develop"), develop and commit on this branch.

Then periodically, merge `develop` into `master` and push to the main repository. 

**Create a new branch named "develop" and switch to it**  
`git checkout -b develop`

**Switch back to branch**  
`git checkout develop`
   
**Switch back to master**  
`git checkout master`
   
**Show branches on local repository**  
`git brannch -a`  
Note: The current branch gets shown with "*".

A branch is not available to others unless you push the branch to your remote repository.

_** Make changes here to the source directory **_

**Delete the branch**  
`git branch -d develop`
   
**Commit a change**  
```
git commit -m "message"
git merge master
```

***
## Quick Note: Create/Sync Repository on desktop and _github_
(This note comes from the [Django class](../../wiki/Django-Project).)

1. Create project on the desktop.
1. On _github_, create new repository (```portfolio-project```).
1. On desktop:
```  
git remote add origin https://github.com/rongrimes/portfolio—project.git  
git push -u origin master
```
The project is now synchronized on the desktop and at _github_.

***
## Cloning to another location
(This note comes from the [Django class](../../wiki/Django-Project).)

Use these steps to deploy code to an external server.
1. Copy project string on _github_: ```https://github.com/rongrimes/portfolio-project```
1. Run clone command on deployment server: ```git clone https://github.com/rongrimes/portfolio-project.git```
1. To update, _push_ on development site, then _pull_ on the deployment site.

*** 

## Other learning sources ##
```man <git topic>```

Good intro topics:
```
gittutorial - A tutorial introduction to Git
giteveryday - A useful minimum set of commands for Everyday Git
```


Other Tutorial topics:
```
gitcli - Git command-line interface and conventions
gitcore-tutorial - A Git core tutorial for developers
gitcredentials - providing usernames and passwords to Git
gitcvs-migration - Git for CVS users
gitdiffcore - Tweaking diff output
gitglossary - A Git Glossary
gitmodules - Defining submodule properties
gitnamespaces - Git namespaces
gitrevisions - Specifying revisions and ranges for Git
gitsubmodules - mounting one repository inside another
gittutorial-2 - A tutorial introduction to Git: part two
gitworkflows - An overview of recommended workflows with Git

```

Also see:
```man git<tab>```
