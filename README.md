# git-test
Some basic how-to's so new students can learn git workflows without breaking another repository

## Intial Setup - SSH and github integration with Windows Laptop
1. install [git](https://git-scm.com/download/win)
2. open `git bash`
3. ssh-keygen -t rsa -b 4096 -C "your_github_email@email.com"
4. use the default file name `id_rsa` and hit enter
5. choose a password, or just hit enter
6. `ls ~/.ssh` and you should see 2 files: id_rsa and id_rsa.pub which are a public/private key pair
7. to authorize yourself to github you need to take the public key and import that to github so type `cat ~/.ssh/id_rsa.pub`
8. select all the text and open github and go to setting, ssh and gpg keys
9. click new ssh key and add the key
10. set a title and paste the public key string and click add
11. tell git bash you have a new ssh key: `eval $(ssh-agent -s)` and `ssh-add ~/.ssh/id_rsa`

if you have invalid key make sure you do not have newlines in the key, it should all be 1 long line ending with your email

now you have an ssh key connected to github and you can interact with the repositories

# Initial Setup - Git User Configuration
1. open git bash
2. git config --global user.name "your name"
3. git config --global user.email "your_github_email@email.com"
4. git config --global user.name
5. git config --global user.email

# Initial Setup - Verify Email
1. open github in a browser
2. go to settings -> emails
3. click verify email
4. open email and click that link

now you have a verified key locally and email address synced to github and you can modify code if you have permissions to

## Terms
- `repository` = the singular location where code is saved and others can pull/push to
- `commit` = usually locally saved changes to be sent to the repository
- `pull` = sync your local copy with the updates from the remote repository
- `push` = the local commits are uploaded to the repository
- `merge` = you want to sync your changes with another developers/the repository and there are modifications that require approval to overwrite

## branching to start work
You want to start development, so it is good to differentiate your changes from other developers until you can verify your changes are acceptable.  This is merged usually done via Pull Request (PR) and 

# Workflows

## Basic commit/push workflow
The most common workflow, small changes...
 
