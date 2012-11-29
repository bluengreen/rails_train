# Installation

[[_TOC_]]


## Mac Installation


Mac OS X 10.8 installation steps

#====================================================================================
# ** many commands require sudo but many do not
# ** this installation documentation is meant to describe a user level install 
# ** where sudo is needed it is explicitly referenced 
# ** pay attention to not add sudo where it is NOT listed
# ** it will affect the permissions negatively  
#====================================================================================

# prepare mac for installations and configuration
# changes have been made to 10.8, that require 
# modification in order tp configure the way we want

# make the ~/Library directory visible so we can move bbedit customizations into it
chflags nohidden ~/Library/

# make directories for our projects
mkdir -p ~/Sites/shared/vhosts
mkdir ~/Sites/shared/logs


# install xcode - needed for compilers and command line tools 
# **this requires an apple developer account 
http://adcdownload.apple.com/Developer_Tools/xcode_4.4.1/xcode_4.4.1_6938145.dmg

# run the installer - the commandline tools contain the compilers 
# install the command line tools from within the xcode application
# from xode menu select preferences then select downloads tab, install commandline tools 


# ** Apple no longer ships an x client, which is required for certain libs being compiled 
# ** install xquartz to meet these requuirements
http://static.macosforge.org/xquartz/downloads/SL/XQuartz-2.7.2.dmg


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

# configure git
git config --global color.ui true
git config --global core.editor bbedit


# create new github account for user @ http://github.com

# create keys for new computer / user
 ssh-keygen -t rsa -C "<your_email_username>@rategenius.com"
 pbcopy < ~/.ssh/id_rsa.pub

# copy new keys to new user account @ http://github.com
https://help.github.com/articles/generating-ssh-keys


# edit local hosts file 
# **add new entries below last line 
# **add each new entry on a new line 
# ** 127.0.0.1 rg.local  
# ** 127.0.0.1 fg.local
# ** 127.0.0.1 test.local
sudo vi /private/etc/hosts 

# flush DNS cache
sudo killall -HUP mDNSResponder 

# edit httpd.conf file 
# ** update to include all vhost conf files 
sudo vi /private/etc/apache2/httpd.conf

# ** locate and uncomment the php module 
>>>>>
LoadModule php5_module libexec/apache2/libphp5.so
<<<<<

>>>>>
<Directory "/Users/<mac_account_username>/Sites/">
  Options Indexes MultiViews
  AllowOverride All
  Order allow,deny
  Allow from all
</Directory>

Listen 0.0.0.0:80
Listen 0.0.0.0:443
NameVirtualHost *:80
NameVirtualHost *:443

# vhosts
Include /Users/pnovess/Sites/shared/vhosts/*.conf
<<<<<<

# doanload and install mysql 
http://cdn.mysql.com/Downloads/MySQL-5.1/mysql-5.1.65-osx10.6-x86_64.dmg

# ** install mysql pref pane, and make it start on reboot 

# set mysql password
mysqladmin -u root password NEWPASSWORD




# edit php.ini file 
sudo vi /private/etc/php.ini

# ** change the time zone 
date.timezone = 'America/Chicago'

# ** mysql socket is located in a different location than listed in php.ini
# ** locate and change these lines to match below
pdo_mysql.default_socket=/tmp/mysql.sock

mysql.default_socket = /tmp/mysql.sock

mysqli.default_socket = /tmp/mysql.sock


# create a php info page to verify the installation of apache / php
mkdir ~/Sites/test/
echo '<?php phpinfo(); ?>' > ~/Sites/test/index.php

# create a vhost file for test.local

cat > ~/Sites/shared/vhosts/test.conf <<-EOD
<VirtualHost *:80>
  DocumentRoot "/Users/<username>/Sites/test/"
  ServerName  test.local
  ServerAdmin <username>@rategenius.com
  Options Indexes MultiViews Includes +FollowSymlinks +SymLinksIfOwnerMatch
  CustomLog "/Users/<username>/Sites/shared/logs/test_access.log" common
  ErrorLog "/Users/<username>/Sites/shared/logs/test_error.log"
</VirtualHost>
EOD

# start apache with verbose messages
sudo bash -x /usr/sbin/apachectl -k start

#  review the install with your browser 

http://test.local/


# install RVM and rubies 
curl -L https://get.rvm.io | bash -s stable --ruby
rvm requirements
rvm pkg install openssl
export CPPFLAGS=-I/opt/X11/include
CC=/usr/local/bin/gcc-4.2 rvm reinstall 1.8.7
CC=/usr/local/bin/gcc-4.2 rvm install 1.9.3
rvm use 1.9.3@custom --create --default


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


##### rateGenius specific

# install pear
# ** choose path for pear - /usr/local/share/pear/
wget http://pear.php.net/go-pear.phar
sudo php -d detect_unicode=0 go-pear.phar
sudo pear install Mail_Mime


# ** tar compress and download a backup version of the database
# ** and uncompress and load the database locally

# create a database 
mysql> CREATE DATABASE rateGenius;
mysql> exit;


# load the backup DB locally
mysql -u root -p rateGenius < <backup_db_name>.sql

# clone source code from github
cd ~/Sites
git clone https://github.com/RateGenius/rateGenius.git

