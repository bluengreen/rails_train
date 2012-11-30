## [[Form Emailer|section2/formemailer]]

This project will demonstrates creating a new application, configuring the new application, creating a database and active record model, scaffolding an active record model, and creating a mailer.    

This technique applies to internal web projects within  our organization. 

Examples:
- marketing 
- optin/optout
- email notifications
- forms


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
