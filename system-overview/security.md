# Security

Security is a top priority for Cillers. We have worked with some of the world's leading security experts to figure out how to make Cillers extremely secure straight out of the box, without sacrificing the developer experience.&#x20;

### The Security Architecture

We have implemented the [Token Handler](https://curity.io/resources/learn/the-token-handler-pattern/) and [Phantom Token](https://curity.io/resources/learn/phantom-token-pattern/) patterns to secure the applications, API gateway and APIs. Here are the main highlights of this approach:&#x20;

⭐ No JWT with personal information is sent to the applications. Instead opaque access tokens, which have no more info than random strings, are used. We don't want to serve JWTs to the applications because they tend to include sensitive personal information, such as personal identifiers. And although JWTs are encoded, so they cannot be read by a human directly, they are not encrypted, so a cyber criminal can easilty decode them to get the sensitive information.\
\
⭐ For web applications, the access and CSRF tokens are stored in http-only 1st party cookies, which means that javascript doesn't have access to them, which is a good mitigation for XSS and CSRF attacks as well as token theft. Hence, you can serve your Web Application using a Content Delivery Network (CDN), without sacrificing security. \
\
⭐ The complexity of the security implementation is to a great extent moved from the application to our OAuth Agent service, with the result that the implementation becomes trivial in the applications and you don't need a dependency on an OAuth library. \
\
⭐ It becomes easy to support Financial-Grade API Security (FAPI), you just need to install your certificates.\
\
⭐ The opaque tokens are exchanged for JWTs in our Kong API Gateway, to provide a great developer experience in the API authorization layer.

To provide a great developer experience when testing or exploring APIs, we provide a turn-key GraphQL Client Web UI that operates in the same auth environment as the web app, which means that developers can easily try out their GraphQL queries before using them in the web app.&#x20;

### Complete Freedom To Run Your Infrastructure Where You Want

We decided to use a Access Control Management and Identity Provisioning System that can be run anywhere: as a cloud service, on-prem or even on your laptop. Therefore Cillers users can easily stay in compliance with privacy regulations and optimize their use-cases. This also means that developers can run their entire system totally sandboxed on their laptops, so they have minimal risk of causing problems and can work effectively.

We chose [Curity](https://curity.io/), because it fulfills the above requirements, is the most capable and has the best developer experience. &#x20;

### Credits

Huge special thanks to [Daniel Lindau](https://www.linkedin.com/in/daniel-lindau-8891ab24/), Nikos Anestos and [André Eriksson](https://www.linkedin.com/in/andr%C3%A9-eriksson-5866ba28/) for their patience and guidance!
