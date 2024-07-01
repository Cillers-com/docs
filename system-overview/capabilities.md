# Capabilities



Most enterprise-grade software systems are comprised of or depend on the following capabilities:&#x20;

* Data storage and processing, including handling lots of different types of data, with different characteristics and use-cases, such as real-time, geographic, time-series, text, vector, columnar. And, now pretty much every system needs to be upgraded with AI capabilities to stay competitive.&#x20;
* Data integrations with both ingestion from and publishing to other systems.
* APIs, typically REST, RPC and increasingly GraphQL.&#x20;
* Web and mobile user-facing applications.
* Security, including access control, identity provisioning, integration with other identity providers, as well as protection against a large number of different types of attacks.&#x20;
* Software and infrastructure management, including source control, data structure management, provisioning of resources, testing, integration and deployment.&#x20;

The [Cillers Core](../building-your-system/cillers-core/) platform includes support for most of these, and will soon support even more. And,  [Cillers Flex](../building-your-system/cillers-flex.md) makes it easy for you to integrate any additional infrastructure capabilities that may be needed for your specific system.&#x20;

Here is a overview of which technologies we use to support the most common demands of a enterprise-grade software system:&#x20;

### Data Storage, Processing and Integration

<table><thead><tr><th>Capability</th><th width="227">Technology</th><th>Motivation</th></tr></thead><tbody><tr><td>Active Data Store</td><td><a href="https://www.couchbase.com/">Couchbase</a></td><td>Couchbase makes handling active data incredibly easy. It also scales incredibly well and is used for many of the world's most demanding and critical systems. </td></tr><tr><td>Event Streaming And Integrations</td><td><a href="https://redpanda.com/">Redpanda</a></td><td>Redpanda is a drop-in replacemet for Kafka. It is much more efficient, scalable and performant than Kafka. And, it is much easier to manage. Redpanda also makes it incredibly easy to integrate with other systems. </td></tr><tr><td>Big Data</td><td><a href="https://www.databricks.com/">Databricks</a></td><td>Databricks has little competition when it comes to managing large amounts of data. They support transactions over S3, GCS and Azure Blob Storage. They make it easy to visualize large result sets, and have a large eco system of tools for other big data purposes. They make it easy to build AI solutions on your own data. </td></tr></tbody></table>



### API, Access Control, And Attack Protection

<table><thead><tr><th>Capability</th><th width="227">Technology</th><th>Motivation</th></tr></thead><tbody><tr><td>Access Control And Identity Management</td><td><a href="https://curity.io/">Curity</a></td><td>Curity can be run as a cloud service, on-prem and on your laptop. It is also incredibly flexible so you can easily build support for any usecase. It has a great management UI. </td></tr><tr><td>API Gateway</td><td><a href="https://konghq.com/">Kong</a></td><td>Kong is very easy to integrate with other system. Curity has built an integration with Kong that we depend on. </td></tr><tr><td>API</td><td><a href="https://strawberry.rocks/">Strawberry GraphQL</a> (Python), <a href="https://fastapi.tiangolo.com/">FastAPI</a>, <a href="https://www.uvicorn.org/">Uvicorn</a> </td><td>Python is the top language that is easiest to get started with for most programmers. Strawberry makes it incredibly easy to add GraphQL operations. And Strawberry is best served with FastAPI and Uvicorn. </td></tr></tbody></table>

We currently only support Python GraphQL in the API layer, but we plan to support all popular languages and the best frameworks in the near future. You can easily add support for other languages and frameworks using [Cillers Flex](../building-your-system/cillers-flex.md).&#x20;

### Frontend Applications

<table><thead><tr><th>Capability</th><th width="227">Technology</th><th>Motivation</th></tr></thead><tbody><tr><td>Single Page Web Applications</td><td><a href="https://react.dev/">React</a></td><td>React is very versatile and great for building anything from a simple to a highly complex web application. </td></tr></tbody></table>

We currently only support React single-page web applications on the frontend, but we plan to add support for all of the best frameworks and mobile shortly. You can easily add support for other frameworks using [Cillers Flex](../building-your-system/cillers-flex.md).&#x20;

### Software And Infrastructure Management

<table><thead><tr><th>Capability</th><th width="227">Technology</th><th>Motivation</th></tr></thead><tbody><tr><td>Container Management</td><td><a href="https://polytope.com/">Polytope</a></td><td>Polytope makes it increadibly easy to package and run an enterprise-grade software system. Using Polytope a system can easily be made to run anywhere, such as on your laptop, on-prem and in any hyperscaler. In runs interchangably on Docker and Kubernetes, and will soon run on other types of containers. </td></tr></tbody></table>

