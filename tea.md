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
bare central storage repo + distributed repos  
layers --- working area + staging area + committed area  
files --- untracked, tracked (unmodified, modified, staged)

<p align="center">
    <img src="https://git-scm.com/book/en/v2/book/02-git-basics/images/lifecycle.png" width="576"/>
</p>

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
