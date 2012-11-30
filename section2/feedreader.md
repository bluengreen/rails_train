# Feed Reader
This project will build on the form emailer tutorial and will show you how to using gems to extend what Rails can do, consuming a webservice, creating a database and activerecord model for storing the ws results,rendering the web service results, offer possible alternative ways to work with RESTFUL API's using active resource.

This technique of reading feeds via JSON, XML, RSS can also apply projects in common web applications. 

Examples:
- mobile apps
- API communication internally or externally
- NADA book out 
- communicating with EX, EQ, or TU. 
 
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
