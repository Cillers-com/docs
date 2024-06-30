# Adding A GraphQL Operation

In GraphQL, there are three types of operations: queries, mutations and subscriptions. Queries are used to fetch data and are similar to GET requests in RESTful APIs. Mutations change data, akin to POST, PUT, or DELETE actions in REST, allowing clients to insert, update, or delete data. Subscriptions provide a way to maintain real-time data flow, enabling clients to receive updates as they happen, which is particularly useful for dynamic user interfaces where data needs to reflect changes as they occur.

#### Let's start by adding a query operation.&#x20;

Open the `code/app-api/app/graphql.py` file and scroll to the `class Query` declaration. All query operations are defined in this class. To add a new query you can copy one of the existing operations and change it as you please. Save the file and open Insomnia to see that your new operation works. Duplicate the "Hello" query and modify it to call you new operation instead.&#x20;

<figure><img src="../../../.gitbook/assets/image.png" alt="" width="375"><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (1).png" alt="" width="375"><figcaption></figcaption></figure>

If you are having trouble with how to structure your query, you can paste your GraphQL operation into ChatGPT.&#x20;

<figure><img src="../../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

Click "Send"! If all is well, you will receive a 200 OK response.&#x20;

<figure><img src="../../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

You can similarily add Mutation and Subscription operations.&#x20;
