# Couchbase

Couchbase can be added using the `add-couchbase` tool. It is an enterprise-ready, feature-complete document database capable of handling millions of requests per second. Couchbase also provides a web-based UI that allows you to manually perform CRUD operations, inspect documents and collections, and monitor performance.

Once Couchbase is added, you can call the `<your-api-name>-add-couchbase-client` tool to programmatically interface with the database from your API.

For development purposes, the Couchbase credentials are:

* **Username:** `user`
* **Password:** `password`

You can access the Couchbase UI at:

```
http://localhost:8091
```

### Couchbase Client

A client library that is added to the project to configure and enable API-level access to Couchbase. The tool can be ran with **api-add-couchbase-client**

### Config Manager

The Config Manager is responsible for configuring Couchbase and other services so they are ready for use. In most cases, it does not require any code changes. You can inspect the configuration it applies to a given service (such as Couchbase) to understand how the service is set up.
