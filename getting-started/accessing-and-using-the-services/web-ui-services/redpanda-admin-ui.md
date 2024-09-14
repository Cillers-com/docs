# Redpanda Admin UI

Your Redpanda Admin Web UI is located at: [http://localhost:8079/](http://localhost:8079/).&#x20;

Click on "Topics" in the left pane, and then on our sample "items" topic in the list.&#x20;

<figure><img src="../../../.gitbook/assets/image (5) (1) (1).png" alt=""><figcaption></figcaption></figure>

Click "Actions" and select "Produce Record".&#x20;

<figure><img src="../../../.gitbook/assets/image (6) (1) (1).png" alt=""><figcaption></figcaption></figure>

Type anything in the "Key" textarea. Any key will work as long as it doesn't already exist in Couchbase, since this topic will automatically produce a document there.

<figure><img src="../../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

Select "JSON" as the type and add the product as follows:

<figure><img src="../../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

Click "Produce" at the bottom of the form. Then you can see that the product has been automatically created in the [Couchbase](couchbase-admin-ui.md) "items" collection. Your new item should also automatically show up in your [web app](http://localhost:8080).&#x20;



