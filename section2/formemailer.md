# Form Emailer

This project will show you how to create a new application, configuring the new application for sending email, creating a database and activerecord model, scaffolding an activerecord model, and creating a mailer.    

This application demonstrates techniques that can be applied to web projects within any organization. 

Examples:
- forms for users to input information
- marketing page (sign up, optin/optout, support)
- email notifications


```
# create an application
$ rails new tutorial
$ cd tutorial

# configure your database settings
# open config/database.yml 
# update the settings to connect
# to your database

# open the Gemfile 
# add the mysql gem
# save

# run bundle install
# to install the gems

$ bundle install 

# create the database
$ rake db:create

# create a migration defining our table

$ rails g migration customer email:string name:string

# run the migration to create the table

$ rake db:migrate

# generate a scaffold of the model
$ rails g scaffold customers email name -s y
$ rails g mailer

# configure app to send mail
# edit config/environment

# generate mailer

$ rails g mailer 

# edit customers controller to deliver mail
# Notification.newoptin.deliver



```
