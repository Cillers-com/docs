# System Services

You will typically access your system services from within other containers, which means that you will not be able to use localhost or 127.0.0.1 as hostname, but will instead be able to use their service id as hostname, e.g. The Curity Identity Service is accessible at http://curity from within other services started in the same stack.&#x20;

[Curity](curity-identity-server.md)

[Couchbase](couchbase-data-platform.md)

[Redpanda](redpanda-event-streaming-platform.md)
