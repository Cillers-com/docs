# Capabilities

Enterprise-grade software systems need to be versatile and powerful enough to handle the increasingly tough demands of modern data-driven organizations, so they need to encompass a large and multifaceted set of capabilities. They manage vast amounts of diverse data, integrate with other systems, require robust security measures, and depend on comprehensive software, data structure and infrastructure management.

When starting to build an enterprise-grade system, it is impossible to know which specific capabilities will be needed in the future. If your infrastructure doesn't support the capabilities required by future needs, you will need to complicate your infrastructure by integrating more technologies over time which will lead to slower and slower development with more and more bugs.&#x20;

Cillers is designed to be complexity resistant, meaning that you will not need to complicate the infrastructure much when you need to add new functionality. To achieve this resistance we have mapped our all of the capabilities that most enterprise-grade systems need and designed the Cillers platform to be able to support all of those with a minimum of complexity and with minimum overhead from the capabilities that you don't need.&#x20;

The following bullets describe the capabilities and components that most enterprise-grade software systems are comprised of. The Cillers platform is designed to already provide great turn-key support for most of these capabilities, and to be easy to extend with more comprehensive support in future releases.&#x20;

* **Data storage and processing** in enterprise-grade systems involve handling diverse types of data, each with unique characteristics and use-cases. Data needs to be stored and indexed in many different ways to support different types of use-cases, including SQL queries, vector search, full-text search, columnar, time-series, geographic and binary formats. Some data needs to be accessible in real-time and other data needs to be accessed in huge quantities in a reasonable amount of time. And, an enormous and increasing amount data need to be stored and made available for many different types of analysis in a timely and cost-effective way.&#x20;
* **Large Language Models (LLMs)** have become essential to most enterprise systems to stay competitive. Due to privacy concerns, many enterprises need to host their own LLMs rather than relying on proprietary cloud-based solutions. Additionally, to effectively support their unique content and service requirements, companies are increasingly training their own specialized LLMs. LLMs also pose a new set of security and privacy challenges.&#x20;
* **Data integrations** are crucial for maintaining a good exchange of information across different systems. This involves both ingestion of data from external sources and publishing of data to other systems. Data often needs to be transformed and processed to align with the specific data models of the system and validated to ensure data integrity. As the number of data streams increase, it becomes increasingly challenging to comprehend the data flows, so good data governance tools are essential.
* **APIs** must be secured against unauthorized access and attacks as well as serve a diverse set of needs of different types clients with a wide range of requirements. Many different programming languages serve different API use-case priorities and developer preferences. And, it is crucial that the API provides a good developer experience both for internal and external developers.
* **Web and mobile application** demands are similar to those of the APIs, in terns of security and privacy threats, as well as the need for a diverse set of programming languages and frameworks that serve different use-cases and developer preferences.
* **Security** is becoming increasingly challenging as cyber criminals are becoming more sophisticated. If a system doesn't stay up to date with the best practices and tools for cyber security, it falls behind in the protection agains new threats that arise from increasingly competent attackers. Third-party code dependencies are among the most severe vulnerabilities that are most likely to get exploited, and controlling dependencies is one of the hardest problems.
* **Software and infrastructure management,** is a jungle that often requires entire teams (dev ops) and a myriad of different tools and services that need to be set up, integrated and maintained for source control, data structure management, provisioning of resources, testing, integration and deployment.

The [Cillers Core](../building-your-system/cillers-core/) platform includes support for most of these capabilities, and will soon support even more. And,  [Cillers Flex](../building-your-system/cillers-flex.md) makes it easy for you to integrate any additional infrastructure capabilities that may be needed for your specific needs.

The Cillers platform is designed to provide robust support for the broad capabilities described above as well as to facilitate easy expansion for more specialized needs. By building your system on the Cillers platform, you place your system on a future-proof foundation, minimizing the risk of complexity creep and setting the stage for sustained innovation and growth.

### Current Cillers Support For The Capabilities Described Above

Here is a overview of which technologies we use to support the most common requirements for a enterprise-grade software system.&#x20;

### Data Storage, Processing and Integration

<table><thead><tr><th width="163">Capability</th><th width="122">Technology</th><th>Motivation</th></tr></thead><tbody><tr><td>Operational Data Store</td><td><a href="https://www.couchbase.com/">Couchbase</a></td><td>Couchbase makes handling active data incredibly easy. It also scales incredibly well and is used for many of the world's most demanding and critical systems. </td></tr><tr><td>Event Streaming And Integrations</td><td><a href="https://redpanda.com/">Redpanda</a></td><td>Redpanda is a drop-in replacemet for Kafka. It is much more efficient, scalable and performant than Kafka. And, it is much easier to manage. Redpanda also makes it incredibly easy to integrate with other systems. </td></tr><tr><td>Big Data</td><td><a href="https://www.databricks.com/">Databricks</a></td><td>Databricks has little competition when it comes to managing large amounts of data. They support transactions over S3, GCS and Azure Blob Storage. They make it easy to visualize large result sets, and have a large eco system of tools for other big data purposes. They make it easy to build AI solutions on your own data. </td></tr></tbody></table>



### API, Access Control, And Attack Protection

<table><thead><tr><th width="167">Capability</th><th width="127">Technology</th><th>Motivation</th></tr></thead><tbody><tr><td>Access Control And Identity Management</td><td><a href="https://curity.io/">Curity</a></td><td>Curity can be run as a cloud service, on-prem and on your laptop. It is also incredibly flexible so you can easily build support for any usecase. It has a great management UI. </td></tr><tr><td>API Gateway</td><td><a href="https://konghq.com/">Kong</a></td><td>Kong is very easy to integrate with other system. Curity has built an integration with Kong that we depend on. </td></tr><tr><td>API</td><td><a href="https://strawberry.rocks/">Strawberry GraphQL</a> (Python), <a href="https://fastapi.tiangolo.com/">FastAPI</a>, <a href="https://www.uvicorn.org/">Uvicorn</a> </td><td>Python is the top language that is easiest to get started with for most programmers. Strawberry makes it incredibly easy to add GraphQL operations. And Strawberry is best served with FastAPI and Uvicorn. </td></tr></tbody></table>

We currently only support Python GraphQL in the API layer, but we plan to support all popular languages and the best frameworks in the near future. You can easily add support for other languages and frameworks using [Cillers Flex](../building-your-system/cillers-flex.md).&#x20;

### Frontend Applications

<table><thead><tr><th width="176">Capability</th><th width="126">Technology</th><th>Motivation</th></tr></thead><tbody><tr><td>Single Page Web Applications</td><td><a href="https://react.dev/">React</a></td><td>React is very versatile and great for building anything from a simple to a highly complex web application. </td></tr></tbody></table>

We currently only support React for single-page web applications on the frontend, but we plan to add support for all of the best frameworks and mobile shortly. You can easily add support for other frameworks using [Cillers Flex](../building-your-system/cillers-flex.md).&#x20;

### Software And Infrastructure Management

<table><thead><tr><th width="175">Capability</th><th width="130">Technology</th><th>Motivation</th></tr></thead><tbody><tr><td>Container Management</td><td><a href="https://polytope.com/">Polytope</a></td><td>Polytope makes it increadibly easy to package and run an enterprise-grade software system. Using Polytope a system can easily be made to run anywhere, such as on your laptop, on-prem and in any hyperscaler. In runs interchangably on Docker and Kubernetes, and will soon run on other types of containers. </td></tr></tbody></table>

