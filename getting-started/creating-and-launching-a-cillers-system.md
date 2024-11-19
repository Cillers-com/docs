# Creating And Launching A Cillers System

Make sure that OrbStack (MacOS users) or Docker Desktop (Linux/Windows users) is running. The `cillers run` command will just wait for it to start otherwise.&#x20;

Create and launch your Cillers system by running the following commands.

```bash
cillers new my-system
cd my-system
cillers run
```

### The Default Stack

When executing `cillers run` you will start the default stack, `stack-graphql-local`, which includes a React web app, a Python GraphQL API, the Couchbase data platform, Redpanda event streaming service, including Redpanda Connect for data processing and integrations, OAuth Access Control with Phantom Token Handler pattern using a combination of Curity and Kong.&#x20;

### Alternative Stacks

<table><thead><tr><th width="320">Id</th><th></th></tr></thead><tbody><tr><td>stack-rest-local</td><td>The same as the default stack, but with a REST API instead of a GraphQL API.</td></tr><tr><td>stack-local-low-memory</td><td>For computers with less than 16GB of RAM. It is much slower to start but has a higher chance of successfully starting on machines with low memory. </td></tr><tr><td>stack-local-without-redpanda</td><td>The same as the stack-local-low-memory, but also not running Redpanda to further reduce the memory load. </td></tr></tbody></table>

### Polytope

You should now see the Polytope Container Runtime UI.

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

Just like in any operating system, some processes run to completion and some should be kept running. You should expect that the following steps should continue to be in the "Running" state: app-api, couchbase, curity, curity-db, kafka-connect, oauth-agent, kong, redpanda, redpanda-console and web-app.&#x20;

Use the guide at the bottom of the Polytope UI to navigate. You will find the Polytope UI to be incredibly helpful and powerful.&#x20;

The start up will take a few minutes extra during the first startup of your system, due to downloads of Docker containers and package installations. The first startup run takes around 5 to 10 minutes.&#x20;

**Attention!** If you are on a slow network, you may have to restart the "pt run stack" command to get the initialization to complete.&#x20;

When the system is fully initialized, you have a super scalable, reliable, secure and cost-effective system infrastructure that can easily be scaled up to serving 100 million requests per second running on your computer. All you need to do now is to add the specific logic that you want for your system. We will soon also make it easy to push your system to production.&#x20;

### Getting Started With Cillers Should Be Trouble Free.

We provide free support! You can book a free support call here if you run into any issues: [https://calendly.com/cillers/free-support](https://calendly.com/cillers/free-support)

You can also reach us at our [Discord server](https://discord.gg/awFYddKwCw) or check out our [Trouble Shooting Guide](trouble-shooting.md).&#x20;



