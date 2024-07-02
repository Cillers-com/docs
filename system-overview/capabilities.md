# Capabilities

Enterprise-grade software systems need to be versatile and powerful enough to handle the increasingly tough demands of modern data-driven organizations, so they need to encompass a large and multifaceted set of capabilities. They manage vast amounts of diverse data, integrate with other system, require robust security measures, and provide the necessary tools for comprehensive software and infrastructure management.

When starting to build an enterprise-grade system, it is impossible to know which specific capabilities will be needed in the future. If your infrastructure doesn't support the capabilities required by future needs, you will need to complicate your infrastructure over time which will lead to slower and slower development with more and more bugs. This insight has been one of the cornerstones of the Cillers platform design. Hence, you are are as future proof as possible when building your system on Cillers, reducing the risk of complexity creep.

The following bullets describe the capabilities and components typically found in enterprise-grade software systems.

* **Data storage and processing** in enterprise-grade systems involve handling diverse types of data, each with unique characteristics and use-cases. Data needs to be stored and indexed in many different ways to support different types of use-cases, including SQL queries, vector search, full-text search, columnar, time-series, geographic and binary formats. Some data needs to be accessible in real-time and other data needs to be accessed in huge quantities in a reasonable amount of time. And, an enormous and increasing amount data need to be stored and made available for many different types of analysis in a timely and cost-effective way.&#x20;
* **Large Language Models (LLMs)** have become essential to most enterprise systems to stay competitive. Due to privacy concerns, many enterprises need to host their own LLMs rather than relying on proprietary cloud-based solutions. Additionally, to effectively support their unique content and service requirements, companies are increasingly training their own specialized LLMs. LLMs also pose a new set of security and privacy challenges.
* **Data integrations** are crucial for maintaining a good exchange of information across different systems. This process involves both ingestion of data from external sources and publishing of data to other systems. Data often needs to be transformed and processed to align with the specific data models of the system and validated to ensure data integrity. As the number of data streams increase, it becomes increasingly challenging to comprehend the data flows, so good data governance tools are essential.
* **APIs**: typically REST, RPC and increasingly GraphQL.&#x20;
* **Web and mobile applications**.
* **Security,** including access control, identity provisioning, integration with other identity providers, as well as protection against a large number of different types of attacks.&#x20;
* **Software and infrastructure management,** including source control, data structure management, provisioning of resources, testing, integration and deployment.&#x20;

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

