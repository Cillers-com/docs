# Accessing And Using The Services

Your Cillers systems consists of two different types of services:  Web UI Services and System Services. Here is an overview of the different services with info on how to access and use them.

## Web UI Services

| Web UI                                                      | URL                                                        | Credentials                                                                         |
| ----------------------------------------------------------- | ---------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| [Web frontend](web-ui-services/web-app.md)                  | [http://localhost:11000](http://localhost:11000)           | Create a new user in the Curity UI that you are redirected to when clicking login.  |
| [GraphQL Client](web-ui-services/graphql-client.md)         | [http://localhost:11001](http://localhost:11001)           | Same auth mechanism as for the web frontend.                                        |
| [Curity Admin UI](web-ui-services/curity-admin-ui.md)       | [http://localhost:6749/admin](http://localhost:6749/admin) | <p>Username: admin<br>Password: password</p>                                        |
| [Couchbase Admin UI](web-ui-services/couchbase-admin-ui.md) | [http://localhost:8091](http://localhost:8091/)            | <p>Username: admin<br>Password: password</p>                                        |
| [Redpanda Admin UI](web-ui-services/redpanda-admin-ui.md)   | [http://localhost:8079](http://localhost:8079/)            | N/A                                                                                 |
| [Jupyter](web-ui-services/jupyter-notebooks.md)             | [http://localhost:8888](http://localhost:8888)             | N/A                                                                                 |

## System Services

You will typically access your system services from within other containers, which means that you will not be able to use localhost or 127.0.0.1 as hostname, but will instead be able to use their service id as hostname, e.g. The Curity Identity Service is accessible at http://curity from within other services started in the same stack.&#x20;

| System Service                                                   | Service ID |
| ---------------------------------------------------------------- | ---------- |
| [Curity](system-services/curity-identity-server.md)              | curity     |
| [Couchbase](system-services/couchbase-data-platform.md)          | couchbase  |
| [Redpanda](system-services/redpanda-event-streaming-platform.md) | redpanda   |







