# Accessing And Using The Services

Your Cillers systems consists of two different types of services:  Web UI Services and System Services. Here is an overview of the different services with info on how to access and use them.

## Web UI Services

<table><thead><tr><th width="217">Web UI</th><th width="283">URL</th><th>Credentials</th></tr></thead><tbody><tr><td><a href="web-ui-services/web-app.md">Web frontend</a></td><td><a href="http://localhost:11000">http://localhost:11000</a></td><td>Click login. Create a new user in the Curity UI.</td></tr><tr><td><a href="web-ui-services/graphql-client.md">GraphQL Client</a></td><td><a href="http://localhost:11001">http://localhost:11001</a></td><td>Same auth mechanism as for the web frontend.</td></tr><tr><td><a href="web-ui-services/rest-client.md">REST API Client</a></td><td><a href="http://localhost:11002">http://localhost:11002</a></td><td>Same auth mechanism as for the web frontend.</td></tr><tr><td><a href="web-ui-services/curity-admin-ui.md">Curity Admin UI</a></td><td><a href="http://localhost:6749/admin">http://localhost:6749/admin</a></td><td>Username: admin<br>Password: password</td></tr><tr><td><a href="web-ui-services/couchbase-admin-ui.md">Couchbase Admin UI</a></td><td><a href="http://localhost:8091/">http://localhost:8091</a></td><td>Username: admin<br>Password: password</td></tr><tr><td><a href="web-ui-services/redpanda-admin-ui.md">Redpanda Admin UI</a></td><td><a href="http://localhost:8079/">http://localhost:8079</a></td><td>N/A</td></tr><tr><td><a href="web-ui-services/jupyter-notebooks.md">Jupyter</a></td><td><a href="http://localhost:8888">http://localhost:8888</a></td><td>N/A</td></tr></tbody></table>

## System Services

You will typically access your system services from within other containers, which means that you will not be able to use localhost or 127.0.0.1 as hostname, but will instead be able to use their service id as hostname, e.g. The Curity Identity Service is accessible at http://curity from within other services started in the same stack.&#x20;

| System Service                                                   | Service ID |
| ---------------------------------------------------------------- | ---------- |
| [Curity](system-services/curity-identity-server.md)              | curity     |
| [Couchbase](system-services/couchbase-data-platform.md)          | couchbase  |
| [Redpanda](system-services/redpanda-event-streaming-platform.md) | redpanda   |







