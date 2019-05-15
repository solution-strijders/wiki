# Wiki: Case 5 – Airport

### Customer: Saibot International Airport. 
The different processes as described by various stakeholders:
- The airport serves multiple airlines with hundreds of flights and thousands of passengers each day.
- These flights are registered with and scheduled by the airport. 
- Gates and check-in counters are assigned on a per-flight basis.
- Passengers are informed of departure gates and check-in counters.
- Baggage is transferred to a departing plane cargo hold from the check-in counter. 
- Baggage is transferred to baggage claim from an arriving plane.
- The control tower manages all incoming and outgoing flights.
- Ground personnel fuels up the planes. 
- Border security is informed of all incoming and outgoing passengers.
- Shops and restaurants rent a space in tax-free zones.
- Security is notified of all events within the airport.
- All airport customers are billed through the airport financial department.

### Azure
https://dev.azure.com/SolutionStrijders/Airport

### Deliverables
- [x] ArchiMate model of the enterprise architecture.
- [x] Context map.
- [ ] Non-functional requirements.
- [ ] Functional requirements added to the given requirements, based on assumptions.
- [ ] Implementation of all functional and non-functional requirements as described for your case.
- [ ] Postman or Swagger scripts that trigger the various RESTful Web API's to allow showing that functionality works. So, there's no need to create a GUI in order to save you work.
- [ ] Docker image of your application. 
- [ ] Motivation of each of the following concepts as applied to your case in a document. Use of these concepts is mandatory. Describe where it is applied and why it is applied:
  - [ ] Microservices based on the principles of DDD
  - [ ] Eventual consistency
  - [ ] Event driven architecture based on messaging
  - [ ] Command Query Responsibility Segregation (CQRS)
  - [ ] Event Sourcing
  - [ ] Enterprise Integration Patterns (at least one)

### Non functionals
Modularity
Fault tolerance
Scalability
Availability
Maintainability

Every service should function without any of the other services
When one part of the application goes down, the rest of the app should stay available
Any part of the app should be scalable to handle increased traffic
While a part of the app is maintained, the rest of the app should stay available

### Functional requirements 
Tickets can be cancelled by the customer 
Airstrips can be reserved for flights 
Status of flights can be tracked 
Plane can't fly before fuel check 
Plane can't fly or land before permission of the control tower
Customer can't book a flight if it's full
