# Introduction

Cillers makes it easy to build great software systems. With Cillers software system platform you can focus your time and brainpower on building the functionality you want instead of your system infrastructure.

A Cillers system is a composition of hierarchical components that run in containers. The lowest-level components run a container image and may be configured to run code in that container, e.g. a component that runs a Python image and mounts your API server code or a script that deploys your system to production. Higher-level components are composed of subcomponents, e.g. a basic web system stack component with a web app, an API server and a database, or a pipeline component with subcomponents for all steps of your CI/CD action steps or AI training processing steps. You create your Cillers system infrastructure by adding, or removing, and configuring components to match your needs. You can add and remove components at any hierarchical level, e.g. you can add a very high-level component with an entire system consisting of a stack component and several pipeline components, or you can add a low-level component such as an AI model server.&#x20;

Cillers provides component templates, so that you can create the entire infrastructure that you need in just one command or enhance your system with a specific capability by adding a lower-level component. We provide simple templates designed for building prototype web systems to enterprise-grade system templates designed to fulfil the highest levels of reliability, scalability, security, compliance and cost-effectiveness with support for all the capabilities you typically need when building an enterprise-grade system. You can then customize your system with configurations as well as adding, or removing, components to match your needs.

You can have different configurations for a component depending on how you want to run it. A Cillers system will, for example, typically have different configurations depending on environment, with hot code reloading in the development environment, and performance optimizations turned on in production. Higher level components typically contain sub-components that are designed to be compatible with each other, e.g. a subcomponent with a GraphQL API server,  a web-app subcomponent with a GraphQL client module. It is our objective to provide most templates with support for all popular programming languages. If there is no template yet for the programming language you prefer, you can relatively easily duplicate a component and convert it to your language using AI.

Cillers is built on [Polytope](https://polytope.com), which makes it easy to configure and maintain container-based systems.  Polytope supports both Docker and Kubernetes and will soon support other popular container types. This means that you can run your stack and pipelines in an optimized way in all of your environments. And, you can run your system on any computer or cloud infrastructure without having to install and manage the different components — all you need is support for Docker or Kubernetes and Polytope. So, with Cillers you avoid all system and programming language versioning and installation headaches. No more need for virtual environments! You can even run a Polytope-based system directly from a remote repository.&#x20;

Cillers systems make use of Polytope's push-to-production functionality, which currently support Google Cloud Platform and AWS. It will soon be extended with support for Azure and other production environments, including on-premise infrastructures. This means that you can deploy your Cillers system to production with a simple command.

With this model of building systems through composition of hierarchical components that run in containers, you can centralize all functionality and configurations for you system in one place. No more need for separate system infrastructures for testing, CI/CD pipeline actions, AI training pipelines, etc. This will not only make it easier for humans to build great systems, it will also make it possible to, in the near-term, build AI generation tools that can build enterprise-grade systems and then make desired improvements.&#x20;









