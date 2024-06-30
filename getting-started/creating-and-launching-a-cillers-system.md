# Creating And Launching A Cillers System

Make sure that OrbStack (MacOS users) or Docker Desktop (Linux/Windows users) is running. The `pt run stack` command will just wait for it to start otherwise.&#x20;

Create and launch your Cillers system by running the following commands.

```bash
cillers new my-system
cd my-system
pt run stack
```

You will now see the Polytope Container Runtime UI.

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

Just like in any operating system, some processes run to completion and some should be kept running. You should expect that the following steps should continue to be in the "Running" state: app-api, couchbase, curity, curity-db, kafka-connect, oauth-agent, kong, redpanda, redpanda-console and web-app.&#x20;

Use the guide at the bottom of the Polytope UI to navigate. You will find the Polytope UI to be incredibly helpful and powerful.&#x20;

The start up will take a few minutes extra during the first startup of your system, due to downloads of Docker containers and package installations. The first startup run takes around 5 to 10 minutes.&#x20;

**Attention!** If you are on a slow network, you may have to restart the "pt run stack" command to get the initialization to complete.&#x20;

When the system is fully initialized, you have a super scalable, reliable, secure and cost-effective system infrastructure that can easily be scaled up to serving 100 million requests per second running on your computer. All you need to do now is to add the specific logic that you want for your system. We will soon also make it easy to push your system to production.&#x20;

### Getting Started With Cillers Should Be Trouble Free.

Please reach out for support on our [Discord server](https://discord.gg/awFYddKwCw) if you run into any issues.&#x20;

You can also use our [Trouble Shooting Guide](trouble-shooting.md).&#x20;

### Web Frontend

Our sample frontend app is located at: [http://localhost:8080/](http://localhost:8080/). Click the 'Login' link and you will be redirected to a standard Curity login form. Click the "Create account" link under the form.&#x20;

When logged in you get a form to add products. Test adding a product.&#x20;

<figure><img src="../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>

Now, open the Couchbase admin web UI to view the product that you created in the db.&#x20;

### Couchbase Admin Web UI

Your Couchbase Admin Web UI is located at: [http://localhost:8091/](http://localhost:8091/). The default username is "admin" and your password is "password".&#x20;

Click the "Documents" link in the left pane and select "products" in the right-most drop-down under "Keyspace". The product that you added should be in the results.&#x20;

<figure><img src="../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>

Now, let's try adding a product through our event streaming service, Redpanda.&#x20;

### Redpanda Admin Web UI

Your Redpanda Admin Web UI is located at: [http://localhost:8079/](http://localhost:8079/).&#x20;

Click on "Topics" in the left pane, and then on "products" in the topics list.&#x20;

<figure><img src="../.gitbook/assets/image (5) (1).png" alt=""><figcaption></figcaption></figure>

Click "Actions" and select "Produce Record".&#x20;

<figure><img src="../.gitbook/assets/image (6) (1).png" alt=""><figcaption></figcaption></figure>

Type anything in the "Key" textarea.&#x20;

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

Select "JSON" as the type and add the product as follows:

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

Click "Produce" at the bottom of the form. Then you can see that the product has been automatically created in the Couchbase "products" collection. And, that it shows up in the list of products the web frontend.&#x20;

Now, let's add a product using the API Exploration UI, Kong Insomnia.&#x20;

### Kong Insomnia API Exploration UI

Open the Kong Insomnia application. Click the "Create" button, select "Import.&#x20;

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

Click "Url" and paste the following URL: [https://cillers-com.github.io/insomnia-cillers-graphql-client/localhost.json](https://cillers-com.github.io/insomnia-cillers-graphql-client/localhost.json)

<figure><img src="../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

Now, let's add a product. Click "Add Product" in the left pane and click "Send".  Insomnia should open up a Curity login pop-up for you. You can use the username and password that you created for the web frontend. You should get a green 200 OK response. The product should now show up in the web frontend.&#x20;

<figure><img src="../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

### Now, you are ready to move on to make some changes to the system.&#x20;

### Web UI Reference&#x20;

When the system has fully initialized you will be able to reach the following web UIs.

| Web UI       | URL                                                          | Credentials                                                                         |
| ------------ | ------------------------------------------------------------ | ----------------------------------------------------------------------------------- |
| Web frontend | [http://localhost:8080/](http://localhost:8080/)             | Create a new user in the Curity UI that you are redirected to when clicking login.  |
| Curity Admin | [https://localhost:6749/admin](https://localhost:6749/admin) | <p>Username: admin<br>Password: password</p>                                        |
| Couchbase    | [http://localhost:8091/](http://localhost:8091/)             | <p>Username: admin<br>Password: password</p>                                        |
| Redpanda     | [http://localhost:8079/](http://localhost:8079/)             | N/A                                                                                 |



