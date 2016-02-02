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
4.  other security operations: disable root login, disable password login, limit access for ~/.ssh and files

### git
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
