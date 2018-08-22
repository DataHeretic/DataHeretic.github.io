# The Language of Data-Driven APIs

## What is DataHeretic?

DataHeretic will provide a full-fledged framework to expose arbitrary data sources over the network, 
without requiring the application developer to write a single line of web-application code.

## Why make DataHeretic?

Many applications are more-or-less simple interfaces to the underlying data-source.
There is no "completely ready" web-framework to wrap around a data-source, and many 
applications suffer from code-bloat, re-inventing the wheel, and incomplete adherence
to standards. On the other hand, most data-sources are hard to version and test for 
integrity vis-a-vis the application code. DataHeretic is aiming to solve these by exposing 
hooks to the underlying data-source, making it inherently testable, versionable, and 
wrapping it in best-in-class tooling and network-interface standards.

## In-Depth

DataHeretic will act as a passthrough of predefined parametrized data-source queries 
through a network interface. The core server itself will be written entirely in a 
streaming, reactive, non-blocking way, only acting as glue-code for the network calls. 
Each data-source will be manually added using custom drivers to conform to a regular 
interface. This regularization will allow integrating many web-framework and 
application-server best-practices as cross-cutting concerns. The notions of data 
migration and API versioning will be merged, to allow easy upgrades and rollbacks. 
Developers will be defining the business domain in the native data-source language, 
as well as turning configuration knobs to best suite their needs.

## Developer Experience

Developers will be maintaining YAML files where schema migrations, endpoints and tests 
will reside in close proximity. A rich CLI interface will be developed to facilitate 
quick actions and control the code-base. A _popular-code-editor_ plugin will be developed
to streamline developer exprience.

## Features

	- [x] High-performance
		- [x] streaming, non-blocking architecture
		- [x] constant memory utilization
		- [x] stability in production
		- [x] high-throughput
	- [x] Built-in DB migrations
		- [x] 
		- [x] testing of stored functions/procs, and indices directly in migrations
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

