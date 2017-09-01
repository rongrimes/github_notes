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

### Project Initialize:  
`git init`

### Create project on Github with a "projectname". Create with:
* README.md
* LICENSE
* .gitignore (use python by default)

`git pull origin master` to bring files to local box
`git push origin master` to sync files from local box

### Link to repo at github.com  
`git remote add origin https://github.com/rongrimes/project_name`
   
### Review  
`git status`

### Initial/Early actions  
`git add <files>`

### Status / Log  
`git status`
   
### Commit files   
`git commit -am "messsage"`   [[ commit all files, with message ]]  
`git log` (run after the first commit)
   
### Upload to Github
`git push origin master (pushes all files up)`  
* requires login	

---

## Operational cycle
Set tag: [optional]	[[ verify ]]

### Create a new branch named "feature_x" and switch to it using
`git checkout -b feature_x`

### Switch back to master
`git checkout master`
   
A branch is not available to others unless you push the branch to your remote repository.

*** Make changes to source directory

### Delete the branch
`git branch -d feature_x`
   
### Commit a branch
`git commit -m "message"`
`git merge master`

### Tag [optional]
`git tag 1.0.0 <10 chars of commit ID>`
  
### Upload
Use this to push the latest to _github_ - usually after a committed update.  
`git push`

### Download
Use this to get the latest from _github_ - often after updating README.md.  
`git push`



---
# To print

See: [adamburmister/gitprint.com](https://github.com/adamburmister/gitprint.com)

In the URL bar replace the `github.com` part of the URL with `gitprint.com`. The markdown file will be rendered to a printable PDF.
