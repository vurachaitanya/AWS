## Code Commit
- You need to have IAM access to create, pull and update the git repo.
  - `Codecommit power` user will have all the permissions.
  - once policy is been attached to user which you have created, you will get option to see `Git credentials generated` 
  - Download user name & Password for git(Codecommit)
- search for resource codecommit


### create new repo 
- Repo name
- Description of the repo for
- Tag for that repo


### Clone git code, update & commit to master: 
- `git clone https://git-codecommit` - AWS Git repo URL
- `cd chaitutest` - got to repo 
- update some files `touch samplefile.md readme.md`
- `git add .`
- `git commit -m "inetial commit"` - Commit to git reop
- `git push origin master` - Push the changes to repo back


### if you update git from UI, So get the latest code by 
- `git pull https://git-codecommit.us-gov-west-1.amazonaws.com/v1/repos/chaitutest` - pull the updated code before editing to get latest version



### Brach creation
- `git checkout -b branch1` - Create branch 
- `echo print("welcome to pyhton code") > hellow.py` - updated the code
- `git add hellow.py` - Add file to git repo back
- `git commit -m "change commit"` - Commit to branch1
- `git push origin branch1` - push to branch1




### Marge branch with master
`git checkout master` - checkout master branch
`git merge branch1` - Merge with branch1
`git push origin master` - commit to master branch



