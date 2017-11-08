# 3. Integrating with an External Word Processor

Date: 2017-11-08

## Status

Accepted

## Context

The copy shop would like to offer users the ability to create and edit documents in a web application. 

### Developing a New Word Processor
We could develop our own processor as part of our customer UI. This would take several developers a long time to develop, but it could have the exact functionality required by the users.

### Integrating with an Existing Word Processor
There are existing web based word processors, such as Google Docs or Office 365 that web applications can integrate with. There would be less control over the functionality of the processor that is available to users. These existing processors have a large development base who are continually improving and extending functionality.

## Decision

We will integrate with external word processors. 

## Consequences

We could extend the application to support other word processors to offer customers a choice of the processor they would like to use. 
We may need to upgrade our integration code to react to any changes made by the external processor API.
