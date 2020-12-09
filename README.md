# Ron's git/github/development Notes

This repository contains my technical cheatnotes and has evolved over time. The content is shared between this README file, and in the wiki for this repository.

## Contents
1. [git/github: Guidlelines for registering and maintaining a project](#gitgithub-guidlelines-for-registering-and-maintaining-a-project)
1. [wiki: github Wiki Markup Cheatsheet](../../wiki#github-wiki-markup-cheatsheet)
1. [Using a Python Virtual Environment](../../wiki/Python-Virtual-Environment)
1. [Building a Django project](../../wiki/DjangoProject)

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
GIT-EDITOR=vim
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
1. Use [`gitignore.io`](#) to build a .gitignore file for the project.

***

## Sync with development platform
```
git pull
```
`git status`  to review

You are now set up to develop the project
---

### Initial/Early actions  
`git add <files>`

### Commit files   
Use editor to add descriptive content.

`git commit`

alt: 

`git commit -am "messsage"`   [[ commit all files, with message ]]  

`git log` (run after the first commit)
   
### Upload to Github
`git push`  (requires login)

### Download
Use this to get the latest from _github_ - often after updating README.md.  
`git pull`

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

**Tag [optional]**  [[ Not tested yet ]]  
`git tag 1.0.0 <10 chars of commit ID>`

***
## Web based git

Review [gitkraken](https://www.gitkraken.com/) for usefulness.

---
# To print this README

(Previous reference no longer valid... need to research further).
