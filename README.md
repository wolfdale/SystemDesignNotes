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

