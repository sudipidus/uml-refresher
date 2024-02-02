### UML Sequence Diagrams

These are useful while designing overall flow and documenting those. (Before writing the actual API)

* Online tools: [planttext](https://www.planttext.com/)

 (project idea -> write a compiler for this which generates diagram based off this code)


![screenshot](https://github.com/sudipidus/uml-refresher/blob/main/screenshot.png)


#### Sample UML Code:
```bash
@startuml
actor User
participant API
participant "Backend Consumer" as BackendConsumer
participant "Payment Gateway" as PaymentGateway
database Database

User -> API: Log into web
activate API

User -> API: Initiate payment
API -> BackendConsumer: Communicate with backend
activate BackendConsumer
BackendConsumer --> Database: initiate transaction
activate Database

BackendConsumer -> PaymentGateway: Call payment gateway
activate PaymentGateway
BackendConsumer <-- PaymentGateway: Response from gateway
deactivate PaymentGateway

BackendConsumer --> API: Response to API
BackendConsumer --> Database: commit the transaction
deactivate Database
deactivate BackendConsumer

API --> User: Send WebSocket update
deactivate API



@enduml

```