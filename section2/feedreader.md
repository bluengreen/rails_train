
## Feed reader
This project will demonstrate  creating a new application, configuring that application, using an available gem for interacting with another websites API, rendering the results of using a web service, creating a database and active record model, offer possible alternative ways to work with RESTFUL API's using active resource.

This technique of reading feeds via JSON or XML can also apply to internal web services for our own applications. 

Examples:
- communicating with EX, EQ, or TU. 
- mobile apps
- API communication internally or externally
- NADA book out 

 
```
  - create an application
  - configure your database settings
  - add gems
     - add twitter/google/youtube/rss reader etc
  - bundle install 
  - rake db:create
  - generate a migration
     - for saving the feeds
  - rake db:migrate

  - rails g scaffold feed -s y
  - rails g mailer
  - configure controller to deliver mail
  - configure app to send mail
```
