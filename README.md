# Beginners
Some basic how-to's so new students can learn git workflows without breaking another repository and instructional reference for development with git on windows machines.


## Intial Setup - SSH and github integration with Windows Laptop
It is necessary to communicate/clone with github via ssh keys (Secure SHell keys) and not via https

1. install [git](https://git-scm.com/download/win)
2. select the default options and just make sure you have `vim as default text editor for git`
2. open `git bash`
3. ssh-keygen -t rsa -b 4096 -C "your_github_email@email.com"
4. use the default file name `id_rsa` by hitting enter
5. choose a password, or just hit enter twice
6. type `ls ~/.ssh` and you should see 2 files: id_rsa and id_rsa.pub which are a public/private key pair, continue to 11, however, if you have an error instead go to steps 8 through 10
7. if you see an error with `ls ~/.ssh`: sometimes the ssh-keygen does not do things properly and you have to make your own folders and move files, continue with steps 8, 9, and 10
8. type `mkdir ~/.ssh`
9. type `mv id_rsa ~/.ssh` and `mv id_rsa.pub ~/.ssh` this will make the folder used to hold keys and move the keys that are in your current folder to the proper location
10. to authorize yourself to github you need to take the public key and import that to github so type `cat ~/.ssh/id_rsa.pub`
11. select all the text and open github and go to settings, `ssh and gpg keys`
12. click the green new ssh key button
13. set a title and paste the public key string and click the green add key button
14. tell git bash you have a new ssh key: `eval $(ssh-agent -s)` and `ssh-add ~/.ssh/id_rsa`

if you have invalid key make sure you do not have newlines in the key, it should all be 1 long line ending with your email

now you have an ssh key connected to github and you can interact with the repositories


# Initial Setup - Git User Configuration
You need to setup your user information when saving code to github and that is tied to commits by your name and email
1. open git bash or use the same one from the previous section
2. type `git config --global user.name "your full first and last name"`
3. type `git config --global user.email "your_github_email@email.com"`
4. type `git config --global user.name` you should see your name
5. type `git config --global user.email` you should see your email


# Initial Setup - Verify Email
if you have not verified your email with github yet for your github account
1. open github in a browser
2. go to settings -> emails
3. click verify email
4. open email and click that link

now you have a verified key locally and email address synced to github and you can modify code if you have permissions to


## Terms
- `repository` = the singular location where code is saved and others can pull/push to
- `clone` = making a local copy of the repository on your computer
- `commit` = usually locally saved changes to be sent to the repository, when typing a message with -m "something" the something is like a reason for saving the changes, a ctrl + s with giving a reason for saving things
- `pull` = sync your local copy with the updates from the remote repository
- `push` = the local commits are uploaded to the repository
- `issue` = a writeup of some problem with code that a user has reported and you wish to track/fix
- `branch` = the current location you are working on, usually master for stable code and "feature_xyz" for your current development
- `remote` = the name of the server you are pushing code to, origin is default by convention, specifically pushes to github as that is what we are using, you can add a remote if you want to push to other servers if desired
- `merge` = you want to sync your changes with another developer/the repository and there are modifications that require approval/conflicts to overwrite


# Workflows

Outlined below are several common functions that are used when using version control

for ease of use students will make branches and files named using their github username so it is easy to verify they are working properly and it is easier to understand and keep things clean

These should be completed by each student once in-order, then can be used as a reference later on


## Start working - clone a repository
1. open the repository page on github, click the green `clone or download` button
2. click the `use ssh` button to select the proper url to use when interacting with github, 
since you have an ssh key setup you should use this method, and the url should be `git@github.com:FullMetalFalcons/beginners.git`
3. copy that url
4. open git bash
5. enter `cd ~/Documents`
6. enter `git clone git@github.com:FullMetalFalcons/beginners.git` by pasting the url
7. now you can view that folder in your Documents folder
8. you have successfully cloned a repo


## Start working - push a text change to the repository
1. open git bash and navigate to your beginners folder/repo if you are not already there
2. type `touch your_github_username.txt`
3. type `git status` this should show your text file as untracked file
3. now you are going to commit this to the repo, type `git add <filename>.txt`
4. type git status and see the added file
5. type `git commit -m "<enter a reason for saving something>"` 
5a. this is a commit message and tells git you are saving the added changes to the repo
6. type `git status` you should see you are ahead of origin/master by 1 commit
6b. this means you have 1 change saved that the repository on github does not have
7. to sync github with your local changes you need to push the commits to the repository
7a. type `git push origin master`
8. you should not have issues and see `master -> master` because you merged your changes into the repo


## Start working - make a branch to add some feature to the robot
You want to start development, so it is good to differentiate your changes from other developers until you can verify your changes are acceptable.  This is merged usually done via Pull Request (PR) and is very common
1. open git bash and navigate to the beginners repository if you are not alreayd there
2. 


## Finish working - make a pull request on github
1. open github and navigate to the beginners repository `https://github.com/FullMetalFalcons/beginners`
2. you should see some yellow text displaying the name of your branch and that you pushed x time ago
3. click the grey `create/new pull request button`
4. the `base:master` <- `compare:branch_name` should be selected
5. modify the name as it will probably just use the name of the branch as the title if you want to give a more specific reason for your changes and write a description if you want
6. click the green `create pull request` button
7. if you have conflicts and see the red `unable to merge` text then please see the section for `Finish working - resolve merge conflits in github`
8. if everyone wants your changes and you see the green text for `able to merge` then click the green `merge pull request` button and you should see a purple icon saying `merged`
8. you have successfully merged your code into the base code for the repository and everyone can pull your changes from master to sync up with your changes

## Start working - cause a merge conflict
1. open git bash and navigate to the beginners repository if you are not already there
2. 
3. 
4. 


## Finish working - resolve merge conflicts in github
1. you are on the page with your pull request and you see the red text `unable to merge automatically`
2. click the grey `resolve conflicts` button
3. you should now see a webpage showing you any text changes with your changes and something that conflicts
```
<<<<< branch_name
changes you made
======
old changes to not save
>>>>>> master
```
you want to save your changes usually so delete the <<<< ===== and >>>>> and related branch names, resulting in
```
changes you made
```
4. click `mark as resolved` and click the green `commit merge` button to save these fixed changes
5. you can then click the green `merge pull request` button on your pull request page like normal


## Bug tracking - tie commit to an issue a user has with your code
1. open the beginners repository 
2. click the `issues` tab and notice a list of possible issues that exist
3. click the `new issue` green button and name the issue `"your github username commit tab"`
4. normally you are writing about something that broke and you would give a description, but this is practice, so you can just click the green `submit new issue` button
5. navigate to the issues tab and make a note of the grey `#xyz` number next to your issue in the list such as `#11` for `jonobrien commit tag` and you will use this later 
6. open git bash and navigate to your beginners repository if you are not already there
7. type `touch github_username-issue.txt`
8. add and commit the file with "#xyz tying commit to issue" where xyz is the grey number from your issue
9. push the commit to the repository
10. navigate to the github repository issue tab again and click on your issue, you should see an additional line with that message
11. if you click that message in the issue conversation tab it will take you to that commit
12. you have successfully tied a commit/code fix to an issue and can track changes in a better/more visible manner


# Notes

## Basic commit/push workflow steps
- `git status` to show pending changes/edits/additional files/deleted files
- `git add file_1 file_2` or `git add .` to add specific files or everything in the current folder and subfolders or `git add --all` to also add renamed files or deletions
- `git status` verify you added whatever you wanted to and nothing extra, or nothing is broken
- `git commit -m "commit message here, reason for deleting file or making necessary change"`
- `git push origin branch_name` to push to the repository on the branch you are currently working
