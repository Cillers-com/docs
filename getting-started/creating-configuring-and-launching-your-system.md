# Creating, Configuring And Launching Your System

To create a Cillers system, run the following command in your terminal. You can change 'my-system' to whatever you would like to name your system. Windows users should run this command in their WSL2 terminal. Make sure you have good internet access when you run this command because it fetches the code for your system from Github.&#x20;

```bash
cillers new my-system
```

This command creates a new directory, `my-system`  or whatever you named it, in the same directory as you ran the command.&#x20;

## How Your Cillers System Is Structured

Open the `my-systems` directory in your favorite code editor and have a quick look at the directory structure and the `polytope.yml`file in your system's root directory.

As you can see in the `polytope.yml`file your system is preconfigured with a demo which consists of a web app, an API and a Couchbase Capella component. You can also see that these components are provided with the parameters they need to connect with your Couchbase Capella cluster.&#x20;

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption><p>polytope.yml</p></figcaption></figure>

Further down in the `polytope.yml`file you can see how the web app and API components load their  code from the `code` directory.&#x20;

<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

Now, expand the directory with your API component's code to see the basic structure. As you can see this is a Python app with Poetry as package manager. This is where you will make changes to build your API. We have a whole separate documentation section on how to work with your API component that we will get to later.&#x20;

<figure><img src="../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

If you look around you may notice that the API and the web app communicate using GraphQL. You can learn how to change to REST in the [Reconfiguring Your Cillers System](reconfiguring-your-cillers-system.md) section.&#x20;

## Configuring Your Cillers System

Your system is configured a) in the `polytope.yml`file, b) with Polytope secrets and c) in component-specific configuration files.&#x20;

### The `polytope.yml` File&#x20;

Cillers has a specific structure for the `polytope.yml`file to make it easy to configure and maintain Cillers systems.&#x20;

Polytope has a different terminology than Cillers for components. Cillers components are made up of Polytope 'modules' and 'templates'. The lowest-level Cillers components are Polytope modules. The higher-level Cillers components are Polytope templates. And, you might find it a bit confusing but, Polytope templates are a completely different concept than Cillers templates. Cillers also uses Polytope templates to encapsulate different configurations for different environments. We are discussing with Polytope how to resolve these differences.

The ENVIRONMENTS section contains a set of Polytope templates with environment specific configurations. Different environments may also run slightly different components. E.g. some dev tool components may run in the development environment but not in other environments.&#x20;

```yaml
#################################
# ENVIRONMWENTS                 #
#################################

- id: dev
  run:
  - template: stack
    args:
      couchbase-host: cb.qdwkspgkf0h5rpzo.cloud.couchbase.com
      couchbase-username: "#pt-secret couchbase-username-dev"
      couchbase-password: "#pt-secret couchbase-password-dev"
  - dev-tools
```

The STACK VARIANTS section contains a set of Polytope templates. The reason we have variants of the stack is that you may want to run slightly different stacks in different environments, e.g. you may want to run a locally hosted database on your development machine, but a cloud-hosted database in production. Polytope will soon build support for template branching which will enable us to collapse all stacks variants into one stack template for all environments with conditional component variants.

```yaml
##################################
# STACK VARIANTS                 #
##################################

- id: stack
  params: 
  - { id: couchbase-host, type: str }
  - { id: couchbase-username, type: str }
  - { id: couchbase-password, type: str }
  run:
  - template: couchbase-capella
    args:
      couchbase-host: "#pt-param couchbase-host"
      couchbase-username: "#pt-param couchbase-username"
      couchbase-password: "#pt-param couchbase-password"
  - template: web-app
  - template: api
    args:
      couchbase-host: "#pt-param couchbase-host"
      couchbase-username: "#pt-param couchbase-username"
      couchbase-password: "#pt-param couchbase-password"
```

The MODULES section contains the lowest level Cillers components which are implemented as Polytope modules. A Polytope module may extend another module to provide some specialization of the submodule, but cannot contain multiple submodules.&#x20;

```yaml
#####################################
# MODULES                           #
#####################################

modules:
  - id: web-app-react-graphql
    info: The Web App
    module: polytope/node
    params:
      - { id: api-protocol-host-port, type: [default, str, http://localhost:4000] }
    args:
      id: web-app-react-graphql 
      image: gcr.io/arched-inkwell-420116/node:21.7.0-slim
      code: { type: host, path: ./code/web-app }
      cmd: ./bin/run
      env:
        - { name: PORT, value: 11000 } 
        - { name: HOST, value: 0.0.0.0 } 
        - { name: REACT_APP_API_BASE_URL, value: "#pt-js params['apiProtocolHostPort'] + '/api/graphql'" }
      restart:
        policy: on-failure
      services:
        - { id: web-app, ports: [{protocol: http, port: 11000}] }
      mounts:
        - { path: /root/.cache/, source: { type: volume, scope: project, id: dependency-cache }}
        - { path: /root/.npm/, source: { type: volume, scope: project, id: npm-cache }} 
        - { path: /app/node_modules/, source: { type: volume, scope: project, id: npm-modules }}
```



If a module mounts code to run within the container, you need to make sure that the `code`parameter is correctly configured. Here is an example of a module that mounts the `./code/web-app`directory. This means that the web-app code should be located in this directory in your project.&#x20;

```yaml
code: { type: host, path: ./code/web-app }
```

So, if you add a template component that consists of a Polytope module that loads code, you need to add the module to the `polytope.yml`file and copy the templates code directory to the specified directory (or change the configured location).&#x20;

## Integrating With A Cloud Service

You can integrate your system with external services, including cloud-hosted databases. Let's configure our system to integrate with Couchbase Capella as an example for how to do this.&#x20;

First, you need a Couchbase Capella cluster. [Follow these instructions on how to set that up](installation-guide/setting-up-a-free-couchbase-capella-cluster.md). If you already have a cluster you can just continue.&#x20;

Go to your Capella admin web UI to look up the connection string to your cluster. Click on your cluster and enter the "Connect" view. Copy the "Public Connection String."&#x20;

<figure><img src="../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>

Run the following command in your terminal in your project directory (the `my-system` directory if you didn't choose a different name).&#x20;

```bash
pt secret set couchbase-username-dev api
pt secret set couchbase-password-dev "your password"
```

Paste the connection string into the`couchbase-host`setting at the top of the `polytope.yml`file. Strip the `couchbases://` prefix. Here is an excerpt from the ENVIRONMENTS section example provided above.&#x20;

```yaml
couchbase-host: cb.qdwkspgkf0h5rpzo.cloud.couchbase.com
```

Now, your system is ready to connect to your Couchbase Capella cluster.&#x20;

## The Default Demo Stack

By default your system comes with a demo stack which consists of a React web app, a Python GraphQL API, A GraphQL API web client and a Couchbase Capella connection. The React web app and the GraphQL API has some example code that will help you see how to structure your code.&#x20;

By default the API and web app code is loaded from the `samples/code` directory. We recommend that you create your own api and web app directories in the code directory and work on your code there. You need to change the api and web-app modules in the polytope.yml file and specify where their respective code should be loaded from.&#x20;

### Our top priority now is to make all of the above more streamlined!&#x20;

### Getting Started With Cillers Should Be Trouble Free.

We provide free support! You can book a free support call here if you run into any issues: [https://calendly.com/cillers/free-support](https://calendly.com/cillers/free-support)

You can also reach us at our [Discord server](https://discord.gg/awFYddKwCw) or check out our [Trouble Shooting Guide](trouble-shooting.md).&#x20;



