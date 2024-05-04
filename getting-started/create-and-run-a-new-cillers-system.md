# Create And Run A New Cillers System

Run the following command in your terminal in the directory where you want your Cillers system to be created. You can change "my\_system" to whatever you like.&#x20;

```bash
cillers new my-system
cd my-system
pt run stack
```

This will take a little while the first time (depending on your network speed) as all the components of the stack are downloaded.

Watch the logs to see when the system is up and running. The last thing to come up is usually Curity.

### Web User Interfaces

When the system has fully initialized you will be able to reach the following web UIs.

| Web UI       | URL                                                          | Credentials                                  |
| ------------ | ------------------------------------------------------------ | -------------------------------------------- |
| Web frontend | [http://localhost:8080/](http://localhost:8080/)             |                                              |
| Curity Admin | [https://localhost:6749/admin](https://localhost:6749/admin) | <p>Username: admin<br>Password: password</p> |
| Couchbase    | [http://localhost:8091/](http://localhost:8091/)             | <p>Username: admin<br>Password: password</p> |
| Redpanda     | [http://localhost:8079/](http://localhost:8079/)             |                                              |

### API UI Client

Open insomnia and import the following collection, if you haven't already: [https://cillers-com.github.io/insomnia-cillers-graphql-client/localhost.json](https://cillers-com.github.io/insomnia-cillers-graphql-client/localhost.json)

Send the hello request. Insomnia should open up a Curity web login page for you. Create an account on your local Curity server using this page, if you haven't already. If you have already created an account, you can just log in.&#x20;
