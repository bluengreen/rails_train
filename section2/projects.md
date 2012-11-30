# Projects

[[_TOC_]]



## [[Form Emailer|section2/formemailer]]

This project will demonstrates creating a new application, configuring the new application, creating a database and active record model, scaffolding an active record model, and creating a mailer.    


## [[Feed reader|section2/feedreader]]
This project will demonstrate  creating a new application, configuring that application, using an available gem for interacting with another websites API, rendering the results of using a web service, creating a database and active record model, offer possible alternative ways to work with RESTFUL API's using active resource.


## RESTFUL API
This project will use the 2 applications above to create an API interface to use the data we collected above. 

This project will demonstrate creating a new application, configuring that application, querying the database using active record.

Examples:
        
- mobile apps
- API communication internally or externally
- cross system communication between 
 - RateGenius 
 - FInanceGenius
 - FG & RG customers
 - Partner interaction with our system
   (marketing, sales, etc) 
 - allow customers to submit applications
 - allow customers to query the system
 - allow applicants to submit applications      
 - allow applicants to review app status 
 - allow applicants to get documents 

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

