# Guidlelines for registering and maintaining a project in git/github

1. One time activity (loads ~/.gitconfig)
Add name, email
`  git config --global user.name "Ron Grimes"`  
`  git config --global user.email ron.grimes@pobox.com`  
`  git config --global push.default "simple"`    [[ verify  ]]

Check global values   
   git config -l

---

Project Initialize:
   git init

Create project on Github with a "projectname" (NO!)
   Create with:
   * README.md
   * LICENSE
   * .gitignore (use python by default)

Link to repo at github.com
   git remote add origin https://github.com/rongrimes/project_name
   
Review
   git status

Initial/Early actions
   git add <files>

Status / Log
   git status
   
Commit files   
   git commit -am "messsage"    [[ commit all files, with message ]]
   git log (run after the first commit)
   
Upload to Github
   git push origin master (pushes all files up)
        > requires login	
	
Operational cycle
Set tag:
[optional]	
Create a new branch named "feature_x" and switch to it using
   git checkout -b feature_x
Switch back to master
   git checkout master
Delete the branch again
   git branch -d feature_x
A branch is not available to others unless you push the branch to your remote repository.

*** Make changes to source directory

[if a branch was created]
   git commit -m "message"
   git merge master

Tag [optional]
   git tag 1.0.0 <10 chars of commit ID>

   
Upload
git push
