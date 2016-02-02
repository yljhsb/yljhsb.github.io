# tool
### ssh
ssh, client(private key, passphrase) log into server(public key), OpenSSH, PuTTY  

1.  generate keys
    ```
    ssh-keygen -t rsa
    ```  
    input passphrase, private key in ~/.ssh/id_rsa, public key in ~/.ssh/id_rsa.pub
2.  copy the public key into server//~/.ssh/authorized_keys
3.  login `ssh user@server` without password, still passphrase is needed
4.  to test private/public key pair, `ssh-keygen -y -f <private key file>`  
    [How do you test a public/private DSA keypair?]
    (http://stackoverflow.com/questions/274560/how-do-you-test-a-public-private-dsa-keypair)
5.  other security operations: disable root login, disable password login, limit access for ~/.ssh and files

### git
[Pro Git](https://git-scm.com/book/en/v2)  
bare central storage repo + distributed repos  
snapshots, nearly every operation is local, integrity`check-summed`  
three states --- working area + staging area + committed area  
<p align="center">
    <img src="https://git-scm.com/book/en/v2/book/01-introduction/images/areas.png" width="576"/>
</p>
The basic Git workflow goes something like this:

1.  You modify files in your working directory.
2.  You stage the files, adding snapshots of them to your staging area.
3.  You do a commit, which takes the files as they are in the staging area and stores that snapshot permanently to your Git directory.

files --- untracked, tracked (unmodified, modified, staged)
<p align="center">
    <img src="https://git-scm.com/book/en/v2/book/02-git-basics/images/lifecycle.png" width="576"/>
</p>

description | command
------------| -------
setup | git config --list
help | git help config 
init | git init
clone | git clone
ignore | .gitignore
check status | git status
check changes | git diff
staginge | git add
committing | git commit
removing file | git rm, then commit
renaming file | git mv, then commit
view commit history | git log
amend prev commit | git commit --amend
unstage file | git reset
unmodify file | git checkout
remote | git remote
remote add | git remote add
remote fetch | git fetch
remote push | git push
remote inspect | git remote show
tagging | git tag


### command line
key | description
:--- | :---
tab | auto complete
ctrl+a | goto the start of the line
ctrl+e | goto the end of the line
alt+f | forward by a word
alt+b | backward by a word
ctrl+k | cut to the end of the line
ctrl+u | cut the the start of the line
ctrl+w | delete back one word
ctrl+h | delete back one letter (backspace)
ctrl+- | undo cut
ctrl+l | clear the screen

### linux
* apt-get
* ps
* file permission
* top `shift+f`
* less `shift+f`

# env

# app
