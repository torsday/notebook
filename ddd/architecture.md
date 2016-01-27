# Architecture

## **Domain** layer
Where the business logic of the application resides. As we’ve seen over the last couple of weeks, this is where you have Domain Objects (i.e. models) such as your ```User``` Entity or ```Email``` and ```Username``` Value Objects.

## **Application** layer
How the outside world communicates with the model.

e.g. HTTP requests, an API or through an automated messaging service.

## **Infrastructure** layer
How the actions of the model are executed. 

e.g. persisting data to a database, queuing jobs, or sending email notifications.