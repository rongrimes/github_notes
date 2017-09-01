# Guidlelines for registering and maintaining a project in git/github

### Add name, email, push mechanism
[[ One time activity (loads ~/.gitconfig) ]]  

`git config --global user.name "Ron Grimes"`  
`git config --global user.email ron.grimes@pobox.com`  
`git config --global push.default simple`  
Alternative: `matching`.  
[[ When push.default is set to 'matching', git will push local branches to the remote branches that already exist with the same name. ]] 


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

`echo "# projectname" >> README.md`  
`git init`  
`git add README.md`  
`git commit -m "first commit"`  
`git remote add origin https://github.com/rongrimes/projectname.git`  
`git push -u origin master`  

This will:
* Create a default README.md
* Initialize git
* Commit and upload local files to github repository  
Note: Github will substitute in correct values for username and projectname.

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


## Sync with development platform
`git pull`
`git status`  to review

You are now set up to develop the project
---

### Initial/Early actions  
`git add <files>`

### Commit files   
`git commit -am "messsage"`   [[ commit all files, with message ]]  
`git log` (run after the first commit)
   
### Upload to Github
`git push`  
* requires login	

### Download
Use this to get the latest from _github_ - often after updating README.md.  
`git pull`

---

## Operational cycle
**Create a new branch named "feature_x" and switch to it**  
`git checkout -b feature_x`

**Switch back to master**  
`git checkout master`
   
A branch is not available to others unless you push the branch to your remote repository.

*** Make changes here to the source directory ***

**Delete the branch**  
`git branch -d feature_x`
   
**Commit a branch**  
`git commit -m "message"`
`git merge master`

**Tag [optional]**  [[ Not tested yet ]] 
`git tag 1.0.0 <10 chars of commit ID>`
  
---
# To print this README

See: [adamburmister/gitprint.com](https://github.com/adamburmister/gitprint.com)

In the URL bar replace the `github.com` part of the URL with `gitprint.com`. The markdown file will be rendered to a printable PDF.
