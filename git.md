# Git in PowerShell

posh-git

https://git-scm.com/book/en/v2/Appendix-A%3A-Git-in-Other-Environments-Git-in-PowerShell
https://github.com/dahlbyk/posh-git

# Useful git commands

### Update git

PS>git update-git-for-windows

### View git configuration

PS>git config --list

### Configure name and email address for commits

PS>git config [--global] user.name "Full Name"
PS>git config [--global] user.email "email@address.com"

### View remote origin

PS>git remote -v

### List all branches

To see local branches \
`PS>git branch`

To see remote branches \
`PS>git branch -r`

To see all local and remote branches
`PS>git branch -a`

Create a new branch
`PS>git checkout -b <my-branch-name>`

Switch to a branch in local repo
`PS>git checkout <my-branch-name>`

<pre><code>
PS>git init
PS>git remote add origin <b>remote repository url</b> 
PS>git remote -v
PS>git add .
PS>git commit -m "Initial commit"
</code></pre>

PS>git clone
