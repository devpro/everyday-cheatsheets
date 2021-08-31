# Design Patterns

* [SpringFramework Guru - Gang of Four Design Patterns](https://springframework.guru/gang-of-four-design-patterns/)

## Cloud Patterns

→ [Cloud Design Patterns](https://docs.microsoft.com/en-us/azure/architecture/patterns/)

### Bulkhead

* [docs.microsoft.com](https://docs.microsoft.com/en-us/azure/architecture/patterns/bulkhead)

### Choreography

*-* [docs.microsoft.com](https://docs.microsoft.com/en-us/azure/architecture/patterns/choreography)

### Command and Query Responsibility Segregation (CQRS)

* [docs.microsoft.com](https://docs.microsoft.com/en-us/azure/architecture/patterns/cqrs)
* [Exploring CQRS within the Brighter .NET open source project](https://www.hanselman.com/blog/ExploringCQRSWithinTheBrighterNETOpenSourceProject.aspx)
* [Example Code - Opinionated ContosoUniversity on ASP.NET Core 2.0's Razor Pages](https://www.hanselman.com/blog/ExampleCodeOpinionatedContosoUniversityOnASPNETCore20sRazorPages.aspx)

### Event sourcing

* [docs.microsoft.com](https://docs.microsoft.com/en-us/azure/architecture/patterns/event-sourcing)

### Saga

* [docs.particular.net/nservicebus](https://docs.particular.net/nservicebus/sagas/)

### Strangler

* [docs.microsoft.com](https://docs.microsoft.com/en-us/azure/architecture/patterns/strangler)

## Software Design Patterns

→ [Software design pattern](https://en.wikipedia.org/wiki/Software_design_pattern)

### Inversion of control & dependency injection

* [Martin Fowler website page](https://www.martinfowler.com/articles/injection.html) - January 23, 2004

### Microservice

> Microservices are small, modular, and independently deployable services. Docker containers (for Linux and Windows) simplify deployment and testing by bundling a service and its dependencies into a single unit, which is then run in an isolated environment.

[source](https://blogs.msdn.microsoft.com/wriju/2017/12/18/microservices-docker-architecture-for-apps/) ([GitHub](https://github.com/dotnet-architecture/eShopOnContainers))

Articles:

* [Design a microservice-oriented application](https://docs.microsoft.com/en-us/dotnet/architecture/microservices/multi-container-microservice-net-applications/microservice-application-design)

### DDD (Domain Driven Design)

Read:

* Definition on [wikipedia](https://en.wikipedia.org/wiki/Domain-driven_design)
* Starting point with [Tackle Business Complexity in a Microservice with DDD and CQRS Patterns](https://docs.microsoft.com/en-us/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/)

Code examples:

* [citerus/dddsample-core](https://github.com/citerus/dddsample-core)
* [kgrzybek/modular-monolith-with-ddd](https://github.com/kgrzybek/modular-monolith-with-ddd)

### Hexagonal Architecture

* [Netflix Technology Blog](https://netflixtechblog.com/ready-for-changes-with-hexagonal-architecture-b315ec967749)
* [Wikipedia](https://en.wikipedia.org/wiki/Hexagonal_architecture_(software))
* [fideloper.com](https://fideloper.com/hexagonal-architecture)

If you're French, you can look at this article from [Octo](https://blog.octo.com/architecture-hexagonale-trois-principes-et-un-exemple-dimplementation/).

### Feature flags

Feature flags are a great way to do continuous delivery with the latest source code and activate when needed new functionalities. But there is a cost that is described in an article from [opensource](https://opensource.com/article/18/7/does-progressive-exposure-really-come-cost).

### Communication

Two standards are recommended:

* [REST](https://fr.wikipedia.org/wiki/Representational_state_transfer)
* gRPC

As of 2019, REST is still more widely used but gRPC contains great improvements and will be used more and more for new microservices.

You can easily find comparison between REST and gRPC on the internet, for example [code.tutsplus.com](https://code.tutsplus.com/tutorials/rest-vs-grpc-battle-of-the-apis--cms-30711). There is an interesting summary on [docs.microsoft.com](https://docs.microsoft.com/en-us/aspnet/core/grpc/comparison?view=aspnetcore-3.0).

### Active Record Patterns

* [Martin Fowler](https://martinfowler.com/eaaCatalog/activeRecord.html)
* [Wikipedia](https://en.wikipedia.org/wiki/Active_record_pattern)

### Autentication

* Refresh tokens: [auth0.com](https://auth0.com/learn/refresh-tokens/)

## Table Data Gateway

* [Martin Fowler](https://martinfowler.com/eaaCatalog/tableDataGateway.html)

### Row Data Gateway

* [Martin Fowler](https://martinfowler.com/eaaCatalog/rowDataGateway.html)
