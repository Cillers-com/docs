# Setting Up A Free Couchbase Capella Cluster

Go to [https://www.couchbase.com/downloads/?family=capella](https://www.couchbase.com/downloads/?family=capella) and sign up. No credit card is required. Couchbase Capella offers a free tier that you can use.&#x20;

## Create Cluster

Once you are logged in, create a cluster.&#x20;

<figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

Select "Free"&#x20;

<figure><img src="../../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

Select your preferred cloud and click "Create Cluster".

<figure><img src="../../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

It will take a few minutes to launch your cluster.&#x20;

## Create Cluster Access

When your cluster is ready, add client access credentials so you can access it. Select "All Buckets", "All Scopes", "Read/Write".&#x20;

<figure><img src="../../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

Now, you need to open your cluster for access from your IP.&#x20;

<figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

The easiest option is to click "Allow Access from Anywhere", which can be ok for development purposes. For proper security you would select a restricted set of IP addresses.&#x20;

Type "confirm" and click "Allow Access from Anywhere".&#x20;

<figure><img src="../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

You then also need to click "Add Allowed IP".&#x20;



![](<../../.gitbook/assets/image (2) (1).png>)



## Create Bucket

Navigate to the "Data Tools" tab. Click "New" under step 1 Bucket. Name the bucket "main". Also click the "Use system generated \_default for scope and collection" checkbox under step 2 Scope. Then, click "Create".

<figure><img src="../../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>

You have now created a cluster, created a bucket called main and configured the access to the server so it is ready to use.



