# Cillers Core

Cillers Core is designed to enable developers to build super capable, scalable, reliable, secure and cost-effective systems incredibly quickly. We have analyzed which capabilities are needed for most enterprise-grade systems and selected the technologies that are best for each area of capabilities.&#x20;

We have also stitched those technologies together so that a Cillers system infrastructure is out-of-the-box more capable, scalable, reliable, secure and cost-effective than almost all systems that we have seen in production.

Here is an overview of the infrastructure capabilities that Cillers support and the technologies that we have selected for each area.

<table><thead><tr><th>Capability</th><th width="227">Technology</th><th>Motivation</th></tr></thead><tbody><tr><td>Active Data Store</td><td><a href="https://www.couchbase.com/">Couchbase</a></td><td>Couchbase makes handling active data incredibly easy. It also scales incredibly well and is used for many of the world's most demanding and critical systems. </td></tr><tr><td>Event Streaming And Integrations</td><td><a href="https://redpanda.com/">Redpanda</a></td><td>Redpanda is a drop-in replacemet for Kafka. It is much more efficient, scalable and performant than Kafka. And, it is much easier to manage. Redpanda also makes it incredibly easy to integrate with other systems. </td></tr><tr><td>Access Control And Identity Management</td><td><a href="https://curity.io/">Curity</a></td><td>Curity can be run as a cloud service, on-prem and on your laptop. It is also incredibly flexible so you can easily build support for any usecase. It has a great management UI. </td></tr><tr><td>API Gateway</td><td><a href="https://konghq.com/">Kong</a></td><td>Kong is very easy to integrate with other system. Curity has built an integration with Kong that we depend on. </td></tr><tr><td>API</td><td><a href="https://strawberry.rocks/">Strawberry GraphQL</a> (Python), <a href="https://fastapi.tiangolo.com/">FastAPI</a>, <a href="https://www.uvicorn.org/">Uvicorn</a> </td><td>Python is probably the top language that is easiest to get started with for most programmers. Strawberry makes it incredibly easy to add GraphQL operations. And Strawberry is best served with FastAPI and Uvicorn. </td></tr><tr><td>Big Data</td><td><a href="https://www.databricks.com/">Databricks</a></td><td>Databricks has little competition when it comes to managing large amounts of data. They support transactions over S3, GCS and Azure Blob Storage. They make it easy to visualize large result sets, and have a large eco system of tools for other big data purposes. They make it easy to build AI solutions on your own data. </td></tr><tr><td>Single Page Web Applications</td><td><a href="https://react.dev/">React</a></td><td>React is very versatile and is great for building anything from a simple to a highly complex application. </td></tr></tbody></table>

The Cillers Core documentation is divided into the following main sections.&#x20;

* Quick Start Guide: How make your first functionality additions to a Cillers system.&#x20;
* Testing
* Data Structure Management
* Provisioning Your System Infrastructure
* Deploying To Production
