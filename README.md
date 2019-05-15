# Wiki

# Case 5 – Airport<br>
#### Customer: Saibot International Airport. <br>
The different processes as described by various stakeholders:<br>
The airport serves multiple airlines with hundreds of flights and thousands of passengers each day.<br>
These flights are registered with and scheduled by the airport. <br>
Gates and check-in counters are assigned on a per-flight basis.<br>
Passengers are informed of departure gates and check-in counters.<br>
Baggage is transferred to a departing plane cargo hold from the check-in counter. <br>
Baggage is transferred to baggage claim from an arriving plane.<br>
The control tower manages all incoming and outgoing flights.<br>
Ground personnel fuels up the planes. <br>
Border security is informed of all incoming and outgoing passengers.<br>
Shops and restaurants rent a space in tax-free zones.<br>
Security is notified of all events within the airport.<br>
All airport customers are billed through the airport financial department.<br>

#### Azure
https://dev.azure.com/SolutionStrijders/Airport

#### Deliverables
~~ArchiMate model of the enterprise architecture.~~ <br>
~~Context map.~~<br>
Non-functional requirements.<br>
Functional requirements added to the given requirements, based on assumptions.<br>
Implementation of all functional and non-functional requirements as described for your case.<br>
Postman or Swagger scripts that trigger the various RESTful Web API’s to allow showing that functionality works. So, there’s no need to create a GUI in order to save you work.<br>
Docker image of your application. <br>
Motivation of each of the following concepts as applied to your case in a document. Use of these concepts is mandatory. Describe where it is applied and why it is applied:<br>
Microservices based on the principles of DDD<br>
Eventual consistency<br>
Event driven architecture based on messaging<br>
Command Query Responsibility Segregation (CQRS)<br>
Event Sourcing<br>
Enterprise Integration Patterns (at least one)<br>


#### Non functionals

Modularity<br>
Fault tolerance<br>
Scalability<br>
Availability<br>
Maintainability<br><br>

Every service should function without any of the other services<br>
When one part of the application goes down, the rest of the app should stay available<br>
Any part of the app should be scalable to handle increased traffic<br>
While a part of the app is maintained, the rest of the app should stay available<br>

### Functional requirements 

Tickets can be cancelled by the customer <br>
Airstrips can be reserved for flights <br>
Status of flights can be tracked <br>
Plane can’t fly before fuel check <br>
Plane can’t fly or land before permission of the control tower<br>
Customer can’t book a flight if it’s full<br>
