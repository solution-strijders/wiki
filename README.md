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

### Deliverables
- [x] ArchiMate model of the enterprise architecture.
- [x] Context map.
- [x] Non-functional requirements.
- [x] Functional requirements added to the given requirements, based on assumptions.
- [ ] Implementation of all functional and non-functional requirements as described for your case.
- [ ] Postman or Swagger scripts that trigger the various RESTful Web API's to allow showing that functionality works. So, there's no need to create a GUI in order to save you work.
- [x] Docker image of your application. 
- [ ] Motivation of each of the following concepts as applied to your case in a document. Use of these concepts is mandatory. Describe where it is applied and why it is applied:
  - [ ] Microservices based on the principles of DDD
  - [ ] Eventual consistency
  - [ ] Event driven architecture based on messaging
  - [ ] Command Query Responsibility Segregation (CQRS)
  - [ ] Event Sourcing
  - [ ] Enterprise Integration Patterns (at least one)

### Concept Motivation
Microservices was included in our case to provide excellent modularity of the differing services and providing a level of fault tolerance with independent down-time required for guaranteeing the most depended upon services the airport application must provide.

Eventual consistency is useful in an application where all the different services are distant from each other and operate apart from each other. Using events, the central data storage can be updated according to generated events later to not impair the functionality of the microservices.

In the airport application it is imperative that all different targets are notified as soon as possible of the latest changes within the application. Therefor implementing event driven architecture patterns based on messaging is a useful solution to the problem. This way, the different microservices can get dynamically notified of the different changes within other context of the application.

To ensure that different queries will provide the data that is requested by the part of the application, using CQRS is the ideal solution to the problem of interconnecting the different services the airport application uses.

Implementing event sourcing is useful for guaranteeing that different access requests are logged for further audits, this might be useful for the context of a flight tower auditing the historical flight data and making further plans based on already available data through event sourcing (and therefor logging).

### Non-functional requirements
- **Modularity**: Every service should function without any of the other services
- **Fault tolerance**: When one part of the application goes down, the rest of the app should stay available
- **Scalability**: Any part of the app should be scalable to handle increased traffic
- **Availability**: While a part of the app is maintained, the rest of the app should stay available

### Functional requirements
Functional requirements added to the given requirements, based on assumptions.

- Status of flights can be tracked 
- Plane can't fly before fuel check 
- Plane can't fly or land before permission of the control tower
- Customers will be billed for costs before a flight

### Case
The goal of this application is to allow different staff from an airport to efficiently manage their own specific domains in a modular way. To ensure that the thousands of passengers can get on their hundreds of flights, the application must be able to deal with heavy loads and must be available at all times, even if part of the application stops working for whatever reason. In the application, it is also important to have management tools for all the different domains set by the stakeholders and described in the Archimate model.

Additionally, the application must be able to deal with cancelled tickets, reserved airstrips, tracking of flights, different plane checks like fuel and permission, and full airplanes, namely to prevent overbooking. In order to satisfy the requirements set by the stakeholders and the providers of the assignment, several key concept have to be implemented in the application. Mainly, microservices, eventual consistency, event driven architecture, command query respensibility segregation, event sourcing, and at least oen enterprise integration pattern.

