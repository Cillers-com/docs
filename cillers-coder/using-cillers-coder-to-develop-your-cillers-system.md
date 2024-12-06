# Using Cillers Coder To Develop Your Cillers System

The recommended workflow is to focus on one module of your Cillers Stack at a time, such as the web app or API. Navigate to the module's code directory (e.g., `code/api-python-graphql`) and use the `cillers implement` command, providing your instructions via the `.cillers/coder/instructions` file.

Module-specific policies and facts reside in the `.cillers/coder/policies` and `.cillers/coder/facts` directories within each module. For policies and facts that span across modules, place them in the corresponding directories at the project root. Restrictions are specified per module in the `.cillers/coder/restrictions` file.

Try the following instructions in the `code/api-python-graphql`module:&#x20;

<pre><code><strong>Change the hello resolver. Append a '1' to the returned message.
</strong></code></pre>

<pre><code><strong>Add a hello2 resolver. It should respond with the same message as the hello
</strong><strong>resolver but with a '2' at the end.
</strong></code></pre>

<pre><code><strong>Add a hello3 resolver in a new file 'hello3.py'. It should respond with the 
</strong><strong>same message as the hello resolver but with a '3' at the end.
</strong></code></pre>

<pre><code><strong>Change the hello3 resolver. Make it create a document in the Couchbase
</strong><strong>items collection. Add a parameter 'name' to the resolver and use
</strong><strong>this as the name value for the item. 
</strong></code></pre>

You can try the changes using the [GraphQL API client](../getting-started/accessing-and-using-the-services/web-ui-services/graphql-client.md).



