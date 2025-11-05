---
description: >-
  In this section, we will introduce Couchbase, demonstrate how it can be used
  in context, and explain how it is configured within Bluetext.
---

# Couchbase

## 1. Couchbase

Couchbase is a high-performance NoSQL document database built for scale, low latency, and rapid development. It stores data as flexible JSON documents, making it easy to evolve data models as requirements change. Unlike many NoSQL systems, Couchbase combines key-value storage, indexing, querying, caching, and persistence in one platform. Its memory-first architecture and shared-nothing clustering let you scale horizontally without sacrificing performance. Couchbase can be used in high-volume, real-time environments like e-commerce, social platforms, and financial systems.&#x20;

In Couchbase, a **bucket** is the top-level container that holds data and defines memory, replication, and persistence settings. Within a bucket, a **scope** acts as a namespace to group related collections, providing logical organization and isolation. A **collection** sits inside a scope and stores JSON documents of a similar type, similar to a table in relational databases.

In the context of an online clothing store, the data could be organized with a main **bucket** containing two **scopes**: inventory and customer. The inventory **scope** would hold **collections** like products warehouses, and suppliers, while the customer **scope** would include users, orders, and reviews. This structure keeps related data grouped and easy to manage.

In the below snapshot of the Couchbase UI, you can see what a collection that sits in the **default** scope of the **main** bucket looks like, with a preview of the JSON data being stored on the right.&#x20;

<figure><img src="../.gitbook/assets/Screenshot 2025-11-05 at 10.26.58.png" alt=""><figcaption></figcaption></figure>

## 2. Couchbase in Bluetext

In Bluetext, Couchbase is integrated into a project through a three-phase tool discovery system. First, **add-couchbase** starts the Couchbase server and Couchbase UI, aswell as the config manager, which  sets up the initial database structure, then stops running. This is followed by the **add-couchbase-client** tool, which adds the Couchbase library to the project, and adds **add-couchbase-collection** as a discoverable tool. The **add-couchbase-collection** tool creates the actual collection in Couchbase. By default with Bluetext, collections are created in the main bucket, under the default scope.&#x20;

