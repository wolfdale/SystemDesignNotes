# System Design Notes/Tips
Condensed Notes/Tips on System design

[How Heroku Patched a Security Vulnerability on entire Redis fleet (HA)](https://blog.heroku.com/rolling-redis-fleet)
> **Immutable infrastructure**, servers are never modified after they're deployed. If we need to change something, we build new servers from a common image and deploy them as replacements.
> **Heroku Redis with HA feature** - When the primary Redis instance fails, it is automatically replaced with a replica, called a standby. Standbys update asynchronously. 
> **Steps Followed** - 
> Created a new server image with fix. Review, test & released that image. Replaced all High Availability standbys with new ones that use the updated image. Once all standbys are patched. Ensure the standby is in sync with the primary. Break the replication link. That means the standby is no longer following the primary, and is now capable of accepting writes. Push a release. As an addon provider, Heroku Redis updates the config vars on your application to point at the new primary. De-provision the old primary and create a new standby.

[Domain-Oriented Microservice Architecture at Uber](https://eng.uber.com/microservice-architecture/)
>Microservices 
> 1. System reliability
> 2. Separation of concerns
> 3. Clear Ownership
> 4. Autonomous execution
> 5. Developer Velocity
> 6. Independent deployments
> 7. Scaling

>Organizations adopt microservices for an operational (deployments | scaling) benefit at the expense of performance.

>DOMA
>**Domain** - Orientation around collections of related microservices.
>**Layers** - Answers “what service can call what other service?” aka dependency management  >(at scale) for microservices. Further divided into Infra, Business, Product, Presentation, Edge(exposed to outside world) layers.
>**Gateways** - API gateway - Act as Single entry-point into a collection of underlying services, which we call a domain.
>**Extension Arch** - For each domain to be agnostic to other domains, Allows domains to extend logic. Act as Provider or Plugin pattern with an interface defined on a service-by-service basis.

[Microservice Architecture at Medium](https://medium.engineering/microservice-architecture-at-medium-9c33805eb74f)
> Medium 2012 -> Monolithic Node.js APP + Satellite services.
> Adopted microservices in 2018.
> Medium idea of Microservices - Multiple loosely coupled services working together. Each service focuses on a single purpose and has a high cohesion of related behaviors and data.
> For medium Node.js monolithic app became bottleneck (Reasons I/O heavy works, deployment problems in-case of bad commit, complexity designing new features, scaling (system became more resource hungry), unable to try new technologies due one giant monolithic app)
> 
> **7 strategies that helped Medium in early stage of adoption** 
> - **Build new services with clear value** 	
>  Avoid massive rewrite.
>  New service must align with core product, technology & engineering value.
> - **Monolithic persistent storage considered harmful** 	
> Must not share database with multiple microservices.
> One service -> One specific type of data.
> Requesting data via APIs.
> - **Decouple "Building a service" and "Running services"** 	
> Containerization, container-orchestration, service mesh, application performance monitoring allow decoupling of "Running service" from "building service".
> Medium uses Istio & Envoy proxy (sidecar design pattern). 	
> Medium uses GRPC (in contras of REST + JSON over HTTP).
> Medium uses (moving to) Kubernetes.
> - **Thorough & consistent observability** 	
>  Observability includes logging, performance tracking, metrics, dashboards, alerting, and is super critical for the microservice architecture to succeed. 	
>   Medium -> uses DataDog dashboards.
> - **Not Every New Service Needs to be Built from Scratch**
> - **Respect Failures Because They Will Happen**
> - **Avoid Microservice Syndromes from Day One** 	
>  Bad Microservices - Poorly Modeled, scattered tech stack, High coupling  	between
> services, lack of observability etc.
> 
> Should We Stop Building Monolithic Services? NO.
> Small teams -> Monolithic
> Early stage startup -> Monolithic
> Low scale -> Monolithic
> Go for Microservices in long Haul.
