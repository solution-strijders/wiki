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
- [x] Implementation of all functional and non-functional requirements as described for your case.
- [ ] Postman or Swagger scripts that trigger the various RESTful Web API's to allow showing that functionality works. So, there's no need to create a GUI in order to save you work.
- [x] Docker image of your application. 
- [x] Motivation of each of the following concepts as applied to your case in a document. Use of these concepts is mandatory. Describe where it is applied and why it is applied:
  - [x] Microservices based on the principles of DDD
  - [x] Eventual consistency
  - [x] Event driven architecture based on messaging
  - [x] Command Query Responsibility Segregation (CQRS)
  - [x] Event Sourcing
  - [x] Enterprise Integration Patterns (at least one)

### Motivatie

- Microservices:
We hebben microservices gebruikt om de applicatie goed schaalbaar te kunnen maken. Het kan zijn dat bepaalde services veel meer gebruikt zullen worden als andere, zoals Check-in. In dat geval is een microservices applicatie de beste oplossing.

- Eventual Consistency:
We passen eventual consistency toe aan de hand van een message broker (RabbitMQ). Elke service heeft zijn aparte database en handelt dus dan ook zijn eigen data.  Als er in een service een aanpassing wordt gedaan, kan er een event naar de message broker worden verstuurd, en kunnen vanaf daar de andere relevante services de event ophalen en hun eigen data aanpassen. Hierdoor hangen de services wel nog steeds van elkaar los, maar delen ze (uiteindelijk) wel dezelfde data.

- Event driven architecture:
Zoals al eerder genoemd maken we gebruik van RabbitMQ. Met RabbitMQ kunnen we aan de hand van events services met elkaar laten communiceren. Na een bepaalde gebeurtenis stuurt een service een event naar RabbitMQ. Andere services kunnen luisteren naar binnenkomende events, en daar op hun eigen manier op reageren. Hierdoor kunnen de services wel met elkaar communiceren, zonder dat ze van elkaar afweten.

- CQRS:
CQRS passen we toe bij de Security service. De security service hebben we opgesplitst tussen read en write. De write service houd de message broker in de gaten en slaat alle relevante data op. De read service haalt de data op uit de db en weergeeft deze. 
Door read en write op te splitsen, kunnen we ervoor zorgen dat de één nog werkt mocht de andere neer gaan. Voor security is het belangrijk dat deze zo veel mogelijk beschikbaar is. Door security op te splitsen, is er dus een grotere kans dat in ieder geval één van de twee online is.

- Event Sourcing:
Met behulp van RabbitMQ kunnen we ook gebruik maken van event sourcing. Security is een service die luistert naar alle events. Deze slaat alle events van alle andere services in zijn eigen database. In de events staan ook de objecten die worden aangemaakt/aangepast. Dit is dan ook meteen onze event store. Als het nodig zou moeten zijn, zouden we met de events die opgeslagen zijn alle data repliceren.


### Non-functional requirements
- **Modularity**: Every service should function without any of the other services
- **Fault tolerance**: When one part of the application goes down, the rest of the app should stay available
- **Scalability**: Any part of the app should be scalable to handle increased traffic
- **Availability**: While a part of the app is maintained, the rest of the app should stay available

### Functional requirements
Functional requirements added to the given requirements, based on assumptions.

- [X] Status of flights can be tracked 
- [X] Plane can't fly before fuel check 
- [X] Plane can't fly or land before permission of the control tower
- [X] Customers will be billed for costs before a flight

### Case
The goal of this application is to allow different staff from an airport to efficiently manage their own specific domains in a modular way. To ensure that the thousands of passengers can get on their hundreds of flights, the application must be able to deal with heavy loads and must be available at all times, even if part of the application stops working for whatever reason. In the application, it is also important to have management tools for all the different domains set by the stakeholders and described in the Archimate model.

Additionally, the application must be able to deal with cancelled tickets, reserved airstrips, tracking of flights, different plane checks like fuel and permission, and full airplanes, namely to prevent overbooking. In order to satisfy the requirements set by the stakeholders and the providers of the assignment, several key concept have to be implemented in the application. Mainly, microservices, eventual consistency, event driven architecture, command query respensibility segregation, event sourcing, and at least oen enterprise integration pattern.

