# The Language and Engine of Data-Driven APIs

### _DataHeretic is currently a work-in-progress. We're happy to answer any questions!_

## What is DataHeretic?

DataHeretic is both a *language*, and an *engine* to help you expose a data-source over the network. DataHeretic treats the web application layer as a *solved problem* and as *infrastructure*, providing an optimized implementation for free.

## Why DataHeretic?

In recent years, web application building has converged around a set of well-known best-practices. Ironically, these best-practices are being re-implemented again and again each time a new web application is created. While the industry is attempting to solve web application development, no other framework has yet to capture the scope of DataHeretic.

#### It is Declarative
The `.dh` _(.DataHeretic)_ format attempts to capture the *essence* of the API relationship, not the *implementation*, enabling the engine to hide the details, *continuously improve* and add new functionality, while drastically reducing the size of the codebase (and its bug count!) In practice, this means that each new version of the engine will improve the performance, stability, and feature richness of your code - without any effort from the app developers.

#### It Treats Data as First Class
While most web application frameworks attempt to _put some clothes on_ the underlying data format (e.g. SQL,) DataHeretic _celebrates_ the naked data format, while enriching it with integrated migrations, templating, and full testability. In fact, we believe that due to those features, application developers would find it much easier to encode business logic in stored functions and procedures - and reap the performance benefits of co-located logic and data.

#### It is Performant
The secondary aim of the *DataHeretic* engine is to squeeze every ounce of performance, while maintaining a minimal (and predictable) memory footprint (The primary aim is to flawlessly execute the spec!) 

#### It Runs on the Cloud and on Premises
While *serverless*, in its many manifestations, attempts to deliver many of the same benefits, it is most-often hosted as PaaS behind paywalls, on shared servers. DataHeretic is easily deployable to any server or Docker environment.

#### It is Open-Source
DataHeretic wishes to enrich and contribute back to the developer community, while maintaining a high level of rigor and auditability.

## Developer Experience

We deeply care about developer experience and ergonomics. Schema migrations, endpoints and tests will reside in close proximity, reducing the cognitive burden on the developer. Its rich CLI interface includes both facilitates code creation, as well as all commands to operate the DataHeretic engine.  plugin will be developed to streamline developer exprience.

## An Example Simple Endpoint
Without further ado, we're proud to present the (_really simple_) `foos_by_id.dh`:
```
ENDPOINT selects a foo by id
GET SINGLE /foos/{id}
PARAMS
    id uint64
FROM
    select top 1 from foos where id={id};
CACHE
	table	[foos]
	key 	[id]

ENSURING
>   it shouldn't find results
    given
        truncate foos;
    when
        id = 1
    then
        code 404
    
>   it should find a record
    given
        truncate foos;
        insert into foo (id, name) values (1, 'ice'), (2, 'cream');
    when
        id = 1
    then
        code 200
        results
            id  name
            1   ice
```
The above encapsulates:
* A succinct description of the API endpoint
* An obvious connection to the underlying datastore
* Declarative tests, to be executed on the test database
* In-memory caching
* Support for GZIP
* Support for JSON, CSV, XML result format
* Logging: access, application, telemetry (ms in each compute stage)
* _... and other cross-cutting concerns, as the engine evolves._


## _Addendum: Feature Bucket-List / Wish-List_

- [x] High-performance Engine
	- [x] streaming, non-blocking architecture
	- [x] constant memory utilization
	- [x] stability in production
	- [x] high-throughput
- [x] Built-in DB migrations
	- [x] integrated UP and DOWN scripts
	- [x] testing of stored functions/procs directly in migrations
- [x] API endpoints
	- [x] very small code footprint
	- [x] advanced parameter validation
	- [x] built-in pagination
	- [x] automatic multiple response formats
	- [x] auto-GZIP compression
	- [x] direct mapping between API and DB queries
	- [x] API test framework
	- [x] Create/Update/Delete endpoints wrapped in a transaction
	- [x] automatically discoverable API
		- [x] Swagger/RAML
		- [x] HATEOAS
- [x] Extensibility
	- [x] custom webhook integration
		- [x] for filtering, transformations, and reporting
	- [x] custom code plugins
		- [x] request filters
		- [x] request transformation
		- [x] result transformation
		- [x] result folding/aggregation
		- [x] integrated testing
- [x] Security
	- [x] HTTPS termination
	- [x] support for role-based access-controls
- [x] Automatic Logging
	- [x] JSON format for indexing in Lucene/Kibana/Splunk/Mongo/etc.
	- [x] access logs
	- [x] application logs
	- [x] telemetry logs for performance analysis

