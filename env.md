---
---

### About Macbook

1 The Macbook, power on, created computer name, created user, setup keyboard, 
language, timezone, wifi, familair with the machine, attached mouse, adjusted
"natural scroll" of the mouse, learned how to use the touchpad.

2 Learned concepts such as Dock, Launchpad, Apple, Setup, restart, sleep.

3 To check the machine is new, checked the battery cycle is 0 by 
[Mac notebooks: Determining battery cycle count](http://support.apple.com/en-us/HT201585).

4 To learn how to reinstall the os, tried reinstall OS X by 
[OS X Yosemite: Reinstall OS X](http://support.apple.com/kb/PH18872).
It took about 1-2 hours.

5 Did system updates.

### Install and config

##### Github
1 Created Github account, created a repository for the account by 
[Github Pages](https://pages.github.com/).

2 Github setup, email, verification.

3 For testing, in client side, Ubuntu, apt-get added PPA, installed newer version git,
setup user.name and password.

4 Tested how to work on the files of the repository back and forth.

##### Macbook
1 Installed Xcode command line tools

    xcode-select --install
    xcode-select -p         # check tools location
    gcc --version           # also used to check the installation
    
It took about 20 minutes.
  
2 Installed Homebrew

    ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

It is installed to /usr/local/bin

    brew doctor             # check installation
    brew update
    brew list --version
    echo $PATH              # check that /usr/lcoal/bin is ahead of /usr/bin
    
3 Installed git
It is better to use git installed by brew than Xcode which located in /usr/bin, 
because the former could be updated.

Before the installation:

    git --version           # 1.9.3

    brew install git        # install
    git -- version          # 2.2.1, run in another terminal
    
Setup user.name and user.email by [Categories/Setup](https://help.github.com/categories/setup/)

    git config --global user.name "xxx"
    git config --global user.email "xxx@email.com"

Cache password by [Caching your GitHub password in Git](https://help.github.com/articles/caching-your-github-password-in-git/#platform-mac)
to avoid input user name and password every time.
    
    git config --global credential.helper osxkeychain

### Concept and command

### Tip and trick

### Meta
