# Installation

[[_TOC_]]

## Mac OS X 10.8 installation steps

*Many commands require sudo but many do not this installation documentation is meant to describe a user level install where sudo is needed it is explicitly referenced. Pay attention to not add sudo where it is NOT listed it will affect the permissions negatively*

##### Install Xcode
Xcode is needed for compilers and command line tools 
*this requires a free apple developer account*

http://adcdownload.apple.com/Developer_Tools/xcode_4.4.1/xcode_4.4.1_6938145.dmg

*run the installer - the commandline tools contain the compilers 
install the command line tools from within the xcode application
from xode menu select preferences then select downloads tab, install commandline tools*

##### Install Quartz 
Apple no longer ships an x client, which is required for certain libs being compiled. 
Install xquartz to meet these requirements

http://static.macosforge.org/xquartz/downloads/SL/XQuartz-2.7.2.dmg

##### Install Homebrew

```
# install homebrew  - http://mxcl.github.com/homebrew/
ruby <(curl -fsSkL raw.github.com/mxcl/homebrew/go)

# check brew config
brew doctor

# update brew
brew update

# install packages
brew tap homebrew/dupes
brew install wget
brew install git
brew install imagemagick
brew install mutt
brew install ghostscript
brew install autoconf automake apple-gcc42
```


##### Install MySQL

Download and install mysql 

http://cdn.mysql.com/Downloads/MySQL-5.1/mysql-5.1.65-osx10.6-x86_64.dmg

 ** install mysql pref pane, and make it start on reboot 

```
# set mysql password
mysqladmin -u root password NEWPASSWORD
```

##### Install RVM & Updated Rubies

```
curl -L https://get.rvm.io | bash -s stable --ruby
rvm requirements
rvm pkg install openssl
export CPPFLAGS=-I/opt/X11/include
CC=/usr/local/bin/gcc-4.2 rvm reinstall 1.8.7
CC=/usr/local/bin/gcc-4.2 rvm install 1.9.3
rvm use 1.9.3@custom --create --default
```
##### Update Shell Profile

```
# create and edit .bash_profile for our environment

cat > ~/.bash_profile <<-EOD

#############################################
# GIT completions & highlighted prompt 
#############################################

# Set git autocompletion
if [ -f /usr/local/Cellar/git/1.7.11.4/etc/bash_completion.d/git-completion.bash ]; then
  . /usr/local/Cellar/git/1.7.11.4/etc/bash_completion.d/git-completion.bash 
fi

# PS1 integration
GIT_PS1_SHOWDIRTYSTATE=true
PS1='\[\033[32m\]\u@\h\[\033[00m\]:\[\033[34m\]\w\[\033[31m\]$(__git_ps1)\[\033[00m\]\$ '

#############################################
# Bash ls colors
#############################################

export CLICOLOR=1
export LSCOLORS=DxGxcxdxCxegedabagacad


#############################################
# alias
#############################################

alias ll='ls -l'
alias la='ls -la'
alias apache='sudo bash -x /usr/sbin/apachectl -k ' # (start|stop|restart)

#############################################
# update path for mysql and pear
#############################################

export PATH=/usr/local/mysql/bin:/usr/local/share/pear/bin:$PATH

#############################################
# RVM - for managing versions of ruby
#############################################

[[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm" # Load RVM into a shell session *as a function*

EOD
```
##### Install Rails

```
gem install rails --no-rdoc --no-ri
``` 

