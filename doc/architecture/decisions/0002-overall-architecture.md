# 2. Overall architecture

Date: 2017-11-08

## Status

Proposed

## Context

A local copy shop chain wants to offer its customers an 'all-in-one' computing experience: document creation, editing, storage, and printing

### Users
 * initially, thousands in the local city, but potentially millions if the demand grows
### Requirements:
 * browser-based or delivered documents
 * word processing
 * presentations
 * document templates (as start points)
 * versioning
 * print scheduling
 * automatic and manual payment for storage, printing, etc.
### Additional Context:
 * Main reason for this initiative is better customer engagement and loyalty
 * for historical reasons, operations is handled by another company and isn't very responsive
 
## Decision

The team wants to create an architecture that is capable of scaling to millions of users without burdening the company with the cost of scale to start with.  We have chosen the following architecture pattern

 * The application as a whole will initially be a modular monolith
 * Each module within the monolith will communicate using an event bus (in memory, initially)
 * Each module will use the same physical database with its own schema
 * The two UI's (customer and shop) will be SPAs with their own BFF APIs that expose functionality by acting as a mediator over the underlying components
 
If the service attracts the millions of users we hope to, then we will be able to scale up by

 * Giving each component its own physical database, clustering if necessary
 * Replacing the in memory event bus with a clustered message broker
 * Moving each component onto its own machine, using multiple machines if necessary

## Consequences

 * The proposed architecture will keep the costs and complexity of the MVP low, until the service is proven.  As uptake increases the team will need to take the scaling actions in the decision section well before the monolith starts to struggle.
 * The team must be disciplined in keeping the components separate.

