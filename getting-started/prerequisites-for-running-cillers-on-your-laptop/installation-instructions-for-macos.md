# Installation Instructions For macOS

Here are the instructions for how to install the prerequisites that are needed to run Cillers on a macOS machine.&#x20;

### Update Your Operating System

We only support the latest version of macOS. Currently, macOS Sonoma.&#x20;

### Install Homebrew

Homebrew allows you to easily install, update, and manage software packages and their dependencies from the command line. Website: [https://brew.sh/](https://brew.sh/)

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### Install Git

Git is a distributed version control system that helps developers manage changes to source code over time. It allows you to track modifications, revert to previous versions of your code, and collaborate with others on the same project. Website: [https://git-scm.com/](https://git-scm.com/)

```bash
brew install git
```

### Install OrbStack (Docker Desktop drop-in replacement).&#x20;

Docker enables developers to package software systems and applications into containers that include everything needed to run an application: code, runtime, libraries, and system tools.&#x20;

OrbStack is a fast, light, and easy way to run Docker containers on macOS. OrbStack is much more resource efficient than Docker Desktop. You may experience issues if trying to run Cillers on Docker Desktop. It is possible to run Cillers on Docker Desktop if you have a powerful machine, but why waste the energy?! Website: [https://orbstack.dev/](https://orbstack.dev/)

```bash
brew install orbstack  
```

### Install Polytope

Polytope enables you to run and manage your software, underlying databases, pipelines and other software services. It makes it possible to seamlessly run your system anywhere, e.g. on your laptop, on your own servers, in your cloud or with any hyperscalar. Website: [https://polytope.com/](https://polytope.com/)

```bash
brew tap polytopelabs/tap
brew install polytope-cli
```

### Install Kong Insomnia

With Kong Insomnia you can create, organize, share, and execute any type of API call, including HTTP, REST, GraphQL, gRPC, SOAP, WebSockets. And especially important for the Cillers stack, it supports easy set up of oAuth-secured connections to APIs. Website: [https://insomnia.rest/](https://insomnia.rest/)

```bash
brew install insomnia
```

### Enable access to self-signed certificates on localhost

The Cillers stack is secured with https connections by default. But, to simplify development on your local development machine, e.g. laptop, you can disable certificate validations for localhost connections. Otherwise, you will need to set up and manage certificates on your development machine which can be a lot of work and offers no benefits for most scenarios.&#x20;

There are two applications that you need to do this in: your browser and your API client UI applications. Here are instructions for how to do this in our preferred browser, Chrome, and our preferred API client UI application, Insomnia. &#x20;

#### Insomnia

Uncheck "Validate certificates" in Settings.&#x20;

<figure><img src="../../.gitbook/assets/image (1) (1).png" alt="" width="227"><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (1).png" alt="" width="190"><figcaption></figcaption></figure>

#### Chrome

Go to [chrome://flags/#allow-insecure-localhost](chrome://flags/#allow-insecure-localhost) and click enable.&#x20;

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>
