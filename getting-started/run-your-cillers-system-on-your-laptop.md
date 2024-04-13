# Run Your Cillers System On Your Laptop

**Run the following commands in your terminal:**

```bash
cd my_system
pt run stack
```

This will take a little while the first time (depending on your network speed) as all the components of the stack are downloaded.

**Open the web UIs:**&#x20;

Web frontend: http://localhost/ (Create new account)&#x20;

GraphQL: http://localhost:4000/api ({ "Authorization": "Bearer xxx" })&#x20;

Curity: https://localhost:6749/admin (username: admin, password: password)&#x20;

Mailpit: http://localhost:8025/&#x20;

Couchbase: http://localhost:8091/ (username: admin, password: password)

You will of course want to change the above passwords.
