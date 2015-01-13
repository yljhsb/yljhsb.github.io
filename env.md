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

6 Learned about application
* [How to Install Applications On a Mac: Everything You Need to Know](http://www.howtogeek.com/177619/how-to-install-applications-on-a-mac-everything-you-need-to-know/)
* [Mac 101: The two Applications folders](http://www.tuaw.com/2010/12/03/mac-101-the-two-applications-folders/)

7 [launchd](http://launchd.info)
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

```bash
$ xcode-select --install
$ xcode-select -p         # check tools location
$ gcc --version           # also used to check the installation
```    

It took about 20 minutes.
  
2 Installed Homebrew

```bash
$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

It is installed to /usr/local/bin

```bash
$ brew doctor             # check installation
$ brew update
$ brew list --version
$ echo $PATH              # check that /usr/lcoal/bin is ahead of /usr/bin
```
It is good to run `brew update` whenever install new packages

3 Installed git
It is better to use git installed by brew than Xcode which located in /usr/bin, 
because the former could be updated.

Before the installation:

```bash
$ git --version           # 1.9.3
$ brew install git        # install
$ git -- version          # 2.2.1, run in another terminal
```

Setup user.name and user.email by [Categories/Setup](https://help.github.com/categories/setup/)

```bash
$ git config --global user.name   "xxx"
$ git config --global user.email  "xxx@email.com"
```

Cache password by [Caching your GitHub password in Git](https://help.github.com/articles/caching-your-github-password-in-git/#platform-mac)
to avoid input user name and password every time.

```bash
$ git config --global credential.helper osxkeychain
```
4 Postgresql and PostGis

```bash
$ brew install postgres
```

Directed by Caveats part of brew, to have launchd start postgresql at login:

```bash
$ mkdir -p ~/Library/LaunchAgents
$ ln -sfv /usr/local/opt/postgresql/*.plist ~/Library/LaunchAgents
$ launchctl load ~/Library/LaunchAgents/homebrew.mxcl.postgresql.plist
$ ps auxwww | grep postgres	# to verify that the postgres process is started
```

Use `launchctl unload` to unload Postgresql. 
```bash
$ brew install postgis
```

Took much longer time than Postgresql.

Since the Postgresql has been started and user "xxx" can run

```bash
$ psql postgres
```

To connect to the database, then create user database in psql

```bash
CREATE DATABASE db;
\q
```

```bash
$ psql db
```

```bash
CREARE EXTENSION postgis;
CREATE EXTENSION postgis_topology;
CREATE EXTENSION fuzzystrmatch;
CREATE EXTENSION postgis_tiger_geocoder;
\dx # to list all instlled extensions
```
5 Node and npm

```bash
$ brew install node
$ node -v # check
$ npm -v  # check	
```

### Concept and command

### Tip and trick

### Meta

