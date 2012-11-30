Form Emailer 
  - this project will demonstrate  
creating a new application, configuring that application, using an available gem for interacting with another websites API, rendering the results of using a web service, creating a database and active record model, offer possible alternative ways to work with RESTFUL API's using active resource.     





  - create an application
  - configure your database settings
  - add gems
  - bundle install 
  - rake db:create
  - generate a migration
  - rake db:migrate

  - rails g scaffold form  -s y
  - rails g mailer
  - configure controller to deliver mail
  - configure app to send mail
  
 



Feed reader
  - this technique of reading feeds via JSON or XML can also apply to internal web services for our own applications. 


       - examples of this:
           - communicating with EX, EQ, or TU. 
           - mobile apps
           - API communication internally or externally
           - NADA book out 
 
  - this project will demonstrate  
creating a new application, configuring that application, using an available gem for interacting with another websites API, rendering the results of using a web service, creating a database and active record model, offer possible alternative ways to work with RESTFUL API's using active resource.     


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





RESTFUL API
  - this project will use the 2 applications above to create an API interface to the data we collected above. 


  - examples of how this can be used within our organization:
           - mobile apps

           - API communication internally or externally
           - cross system communication between 
                    - RateGenius 
                    - FInanceGenius
                    - FG & RG customers
                    - Partners (marketing, sales, etc) 
           - allow customers to submit applications, and query the system
           - allow applicants to submit applications and review their application status, get documents 


   - this project will demonstrate  
creating a new application, configuring that application, querying the database using active record, .     


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


