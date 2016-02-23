Table of Contents
=================
* [app](#app)  
* [env](#env)  
* [tool](#tool)  
    * [ssh](#ssh)
    * [git](#git)
    * [vim](#vim)
    * [command](#commandline)
    * [linux](#linux)




# app

<a name="commands"/>
### commands
```
# generate controller
rails generate controller StaticPages home help
# undo
rails destroy controller StaticPages home help
```
1. manually added action about, contact by modifying app/controllers/static_pages_controller.rb
   and config/routes.rb
2. app/helpers/application_helper.rb helper functions
3. css, bootstrap, modify Gemfile, bundle install, create app/assets/stylesheets/custom.css.scss
4. app/views/layout application.html.erb, _shim.html.erb, _header.html.erb, _footer.html.erb

http://guides.rubyonrails.org/asset_pipeline.html  
http://stackoverflow.com/questions/17350524/how-do-i-add-jquery-plugins-on-my-rails-app  
http://railsapps.github.io/rails-javascript-include-external.html  
http://railscasts.com/episodes/279-understanding-the-asset-pipeline?view=asciicast  

# env
<a name="ror"/>
### ror setup
https://www.digitalocean.com/community/tutorials/how-to-install-ruby-on-rails-with-rbenv-on-ubuntu-14-04  
https://www.digitalocean.com/community/tutorials/how-to-deploy-a-rails-app-with-unicorn-and-nginx-on-ubuntu-14-04  
https://www.digitalocean.com/community/tutorials/how-to-use-postgresql-with-your-ruby-on-rails-application-on-ubuntu-14-04
```
sudo apt-get update
sudo apt-get install git-core curl zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev python-software-properties libffi-dev

cd
git clone git://github.com/sstephenson/rbenv.git .rbenv
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bash_profile
echo 'eval "$(rbenv init -)"' >> ~/.bash_profile

git clone git://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build
echo 'export PATH="$HOME/.rbenv/plugins/ruby-build/bin:$PATH"' >> ~/.bash_profile
source ~/.bash_profile
# Note: On Ubuntu Desktop, replace all occurrences .bash_profile in the above code block with .bashrc.

# used 2.1.2 per http://stackoverflow.com/questions/23155289/rbenv-build-failed-on-ubuntu-14-04
rbenv install -v 2.2.1
rbenv global 2.2.1
echo "gem: --no-document" > ~/.gemrc
gem install bundler
gem install rails
rbenv rehash

# install rails with specific version per http://stackoverflow.com/questions/9771172/rbenv-surviving-without-gemsets?lq=1
gem install rails -v 4.2.2
cd ~/projects
rails _4.2.2_ new hello_app
```
<a name="project.setup"/>
### project setup
one server for dev, git, web. simple  
```
cd ~\projects
rails _4.2.2_ new project
cd project
rails server # now the app is running at http://localhost:3000
# config nginx as reverse proxy to localhost:3000 and restart nginx
# then the app is accessible at http://ip/app

# commands
# Gemfile
bundle install --without production
rails server
# scaffolding
rails generate scaffold User name:string email:string
# rake
```
https://www.nginx.com/resources/admin-guide/  
http://stackoverflow.com/questions/33403358/multiple-rails-apps-over-nginx-reverse-proxy

<a name=""/>
### project structure
RESTful, request ---> resource ---> response  
```
resource ___ router ( config/routes.rb )  
         |__ controller ( app/controllers/users_controller.rb )  
         |__ model ( app/models/user.rb )  
         |__ view (app/views/users/index.html.erb, edit.html.erb, show.html.erb, new.html.erb ...)  
```         
RESTful routes: HTTP request --- URL --- Controller Action           

<a name="naming"/>
### naming

# tool
<a name="ssh"/>
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

<a name="git"/>
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

branch, a movable pointer (HEAD) to one of these commits, default branch: master  
commit object --- pointer to snapshot, email/name/message, pointer to parents commits  

description | command
------------| -------
creating new branch | git branch xxx
switching branch | git checkout xxx
merging branch | git merge xxx
listing | git branch -v --merged, --no-merged

branching workflow:  
master branch --- stable code  
dev branch --- work, test,when stabled, merged into master  
topic branch --- issues, bugs, hotfix, single feature, could be deleted after merging into main branch  
* [google git branching model](https://www.google.com/search?q=successful+git+branching+model&ie=utf-8&oe=utf-8)
* [a successful git branching model](http://nvie.com/posts/a-successful-git-branching-model/)
* [comparing workflows](https://www.atlassian.com/git/tutorials/comparing-workflows/centralized-workflow)  

remote branch  
rebasing  

git process:

1.  config, user name, email
2.  determine central repo, github, bitbucket or local folder
3.  create a new repo, or convert an existing working folder into a git repo or clone a repo from a remote repo
4.  start working, create/copy .gitignore file
5.  work flow
        1. git status
        2. git add .
        3. git commit -m "comment"
        4. git log
6.  branching work flow
        1. git checkout -b new-branch
        2. normal work flow
        3. git checkout master
        4. git merge new-branch
7.  after config remote repo
        1. git pull
        2. git push

<a name="commandline"/>
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
alt+d  | delete foward one word
ctrl+h | delete back one letter (backspace)
ctrl+- | undo cut
ctrl+l | clear the screen

http://askubuntu.com/questions/45521/how-to-navigate-long-commands-faster

<a name="vim"/>
### vim
installation, vim --version, sudo apt-get install vim  

move  

1.  hjkl
2.  ctrl+f: down full screen, crtl+b: up full screen, crtl+d down half, ctrl+u: up half, ctrl+e: down, crtl+y: up
3.  gg: start, G:end, NG: goto line N, N%: go by percent, ctrl+G: current position, HML
4.  '' or `` move cursor to last position, :help mark-motions
4.  w/e, W/E, b, B, ^, 0, $, %
5.  /pattern search, n/N
6.  u: undo, crtl+r: redo
7.  d: delete, y: copy, p:paste, r: replace, s: substitute
8.  i, a, o
9.  ctrl+z, fg
10. indent, N>>, visual >
11. w,e->, b,ge<-
12. W,E, B,gE
13. f{char}, find by char, ; forward, , backward, F back find
14. t/T

text object selection  

1.  i: inside, diw, a: inclusive, daw
2.  html tag, cit/cat, vit/vat
3.  parenthesis block, vib/vab
4.  curly braces block, viB/vaB
5.  i)/a), i]/a], i'/a', i"/a"
6.  )/b, }/B, ], >, ', ", `, t, p (paragraph), w, W, s (sentence)
7.  delete around - daw, change inside - ciw

vim 风格 act/repeat/reverse  

1.  change . u
2.  f{c} ; ,
3.  t{c} ; ,
4.  /pattern n N
5.  ?pattern n N
6.  :s/target/replace & u
7.  * n N

operator + motion  
c, d, y, g~, gu gU, >, <, =, !

one key to move, one key to execute  

case (operator + movement)  

1.  g~ toggle
2.  gU uppercase
3.  gu lowercase
4.  ~ toggle char under the cursor
5.  3~ toggle next three chars
6.  g~iw toggle case of current word
7.  g~~ toggle case of current line

normal mode  

1.  u: undo
2.  daw, repeatable
3.  <c-a> plus, <c-x> minus, css editing
4.  dw, ., not count
5.  c3w count
6.  operator + motion = action

insert mode  

1.  change without leave: backspace, <c-h>(backspace), <c-w>(delete back one word), <c-u>(delete back to start)
2.  <c-o> enter insert normal mode, like <c-o>ZZ, after y <c-r>o
3.  R replace mode
4.  r single replace mode

visual mode  

1.  v: char visual mode
2.  V: line visual mode
3.  <c-v>: block visual mode
4.  gV: reselect last visual selection
5.  o: goto the other end of selection
6.  . for repeat
7.  block visual selection, column selection
8.  c, A, I

command line mode  

1.  : :[range]command[address]
2.  range: !, $, 0, ., 'm, '<, '>, %
3.  command: delete, yank, put, copy, move, join
4.  t - copy, m - move

multiple files  

1.  netrw plugin
2.  vim . file explorer
3.  :e / :E
4.  multiple tabs, each tab has multiple windows, :set mouse=a enable mouse
5.  :tabedit {file}
6.  <c-w>T (shift-t) multiple win to multiple tab
7.  :tabc[lose] close current tab
8.  :tabo[nly] keep the current tab
9.  switch tab: gt, gT
9.  switch and move use mouse
10. <c-w>s, <c-w>v, :split {file}, :vsp[lit] {file}
11. <c-w>w cycle or <c-w><c-w>
12. <c-w>hjkl
13. <c-w>c close
14. <c-w>o only keep current one
15. resize use mouse
16. qa, wqa to quit all tabs

work flow  

1.  multiple tab/multiple win
2.  explorer
3.  matchit, tag
4.  collapse/expand
5.  page up/down

indent  

1.  :filetype indent on
2.  :set filetype=html
3.  set smartindent
4.  gg=G

fold/unfold, outline  

1.  za/zc/zo, zR/zM, zj/zk

:%s/old/new/gc

ref  

1.  help, :help <command>, :h, /quick quick help, ctrl+I enter, crtl+T exit
2.  reference manual - basic editing
3.  book: practical vim

<a name="linux"/>
### linux
* apt-get
* ps
* file permission
* top `shift+f`
* less `shift+f`
* kill -9 (force) -15 (gracefully) pid

### markdown
* https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet
* https://github.github.com/github-flavored-markdown/sample_content.html
* https://guides.github.com/features/mastering-markdown/#intro
