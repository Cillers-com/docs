# Creating And Launching A Cillers System

Make sure that OrbStack (MacOS users) or Docker Desktop (Linux/Windows users) is running. The `cillers run` command will just wait for it to start otherwise.&#x20;

Create and launch your Cillers system by running the following commands.

```bash
cillers new my-system
cd my-system
```

### Create A Free Couchbase Capella Cluster

Go to [https://www.couchbase.com/downloads/?family=capella](https://www.couchbase.com/downloads/?family=capella) and sign up. No credit card is required. Couchbase Capella offers a free tier that you can use.&#x20;

Once you are logged in, create a cluster.&#x20;

<figure><img src="../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

Select "Free Tier"&#x20;

<figure><img src="../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

Select your preferred cloud and click "Create Cluster".

<figure><img src="../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

It will take a few minutes to launch your cluster. When it is ready, add client access credentials so you can access it. Select "All Buckets", "All Scopes", "Read/Write".&#x20;

<figure><img src="../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

Run the following command in your terminal in your project directory (the my-system directory if you didn't choose a different name).&#x20;

```bash
pt secret set couchbase-username-dev api
pt secret set couchbase-password-dev "<your password>"
```

Now, you need to open your cluster for access from your IP.&#x20;

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

The easiest option is to click "Allow Access from Anywhere", which is ok for development purposes. For production purposes

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

Type "confirm" and click "Allow Access from Anywhere". You then also need to click "Add Allowed IP". ![](<../.gitbook/assets/image (2).png>)



Update your `polytope.yml`file and specify the connection string. You can find it in the "Connection" view.&#x20;

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

Copy the connection string and change the `couchbase-host`setting at the top of the `polytope.yml`file. Strip the `couchbases://` prefix.&#x20;

Last step is to create a Couchbase bucket under the Data Tools tab. Click "New" under step 1 Bucket. Name the bucket "main". Also click the "Use system generated \_default for scope and collection". Then, click "Create".

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

Now, your Capella cluster and your connection to it are ready.&#x20;

### Launch The Stack

```
cillers run dev
```

### Polytope

You should now see the Polytope Container Runtime UI.

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

Just like in any operating system, some processes run to completion and some should be kept running.&#x20;

Use the guide at the bottom of the Polytope UI to navigate. You will find the Polytope UI to be incredibly helpful and powerful.&#x20;

**Attention!** If you are on a slow network, you may have to restart the "cillers run dev" command to get the initialization to complete.&#x20;

### The Default Stack

By default your stack consists of a React web app, a Python GraphQL API, A GraphQL API web client and a Couchbase Capella connection. The React web app and the GraphQL API has some example code that will help you see how to structure your code.&#x20;

You can modify your stack by editing the polytope.yml file. By default the polytope.yml file is a softlink to the default sample config. We recommend that you replace this softlink with the polytope.yml config that suits your needs best. Initially you can just copy the config file that you like in the samples/config\_files directory to your project's root directory.

By default the API and webb app code is loaded from the samples directory. We recommend that you create your own api and web app directories in the code directory and work on your code there. You need to change the api and web-app modules in the polytope.yml file and specify where their respective code should be loaded from.&#x20;

We are working on making all of the above more streamlined.&#x20;

### Getting Started With Cillers Should Be Trouble Free.

We provide free support! You can book a free support call here if you run into any issues: [https://calendly.com/cillers/free-support](https://calendly.com/cillers/free-support)

You can also reach us at our [Discord server](https://discord.gg/awFYddKwCw) or check out our [Trouble Shooting Guide](trouble-shooting.md).&#x20;



