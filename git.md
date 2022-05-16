# Git in PowerShell
posh-git

https://git-scm.com/book/en/v2/Appendix-A%3A-Git-in-Other-Environments-Git-in-PowerShell
https://github.com/dahlbyk/posh-git

# Useful git commands

### Check git version
PS> git --version

### Update git
PS>git update-git-for-windows

### View git configuration
PS>git config --list

### Configure name and email address for commits
PS>git config [--global] user.name "Full Name"
PS>git config [--global] user.email "email@address.com"


### View remote origin
PS>git remote -v


PS>git branch


<pre><code>
PS>git init
PS>git remote add origin <b>remote repository url</b> 
PS>git remote -v
PS>git add .
PS>git commit -m "Initial commit"
</code></pre>


PS>git clone 


### Gitflow
flow for deployment is as follows:
1.	4 branches.
    i.	Main
    ii.	Test/Release
    iii.Develop
    iv.	Feature
 
1.	Decide on feature will go in release/prod
2.	Feature branch is created from develop branch.
3.	Work on new feature on separate Feature branch
4.	Feature branch that will go on release will be merged to the Develop branch
5.	Future features won't be merged to the Develop branch.
6.	Testing
7.	If all feature for release are complete and merged with Develop, 
8.	This will be cut-off/no new feature will go on.
9.	Merge Develop branch to the Test/Release branch
10.	Release branch is deployed to the Managed Test
11.	Testing, any issues will be fixed in release branch
12.	Release branch is merged to the Main and deployed to the Prod.
13.	Release branch is merged to the Develop.

Reference:
https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow