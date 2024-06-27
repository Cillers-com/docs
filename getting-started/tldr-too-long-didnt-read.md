# TLDR (Too Long; Didn't Read)

Here is all you typically need to do to get started with Cillers, but you may want to read through the full Getting Started documentation to ensure a smooth experience.&#x20;

## Special Preparations For Windows Users

Note that Windows users will need to install WSL2 (Windows Subsystem For Linux) first, and run the commands below in the WSL2 shell. Here are the official [installation instructions](https://learn.microsoft.com/en-us/windows/wsl/install).&#x20;

Windows users also need to enable Docker Desktop WSL2 Backend. See instructions here: [https://docs.docker.com/desktop/wsl/](https://docs.docker.com/desktop/wsl/)&#x20;

Ensure that you have enough memory allocated for Docker: [https://mrakelinggar.medium.com/set-up-configs-like-memory-limits-in-docker-for-windows-and-wsl2-80689997309c](https://mrakelinggar.medium.com/set-up-configs-like-memory-limits-in-docker-for-windows-and-wsl2-80689997309c)

## Installation&#x20;

### Installation Alternative 1: Brew

```bash
brew update
brew install polytopelabs/tap/polytope-cli
brew install cillers-com/tap/cillers
```

MacOS users also run the following:

```bash
brew install --cask orbstack
brew install --cask insomnia 
```

Cask only works on MacOS, so Linux/Windows users will have to install [Kong Insomnia](https://insomnia.rest/download) manually.

### Installation Alternative 2: Bash

You can install the Polytope and Cillers CLI binaries directly using the following commands. This process requires that you know which processor architecture you are running on to download the appropriate binaries.&#x20;

Note that you will need to install [Kong Insomnia](https://insomnia.rest/download) manually using this approach.&#x20;

#### Figure out which architecture your processor has

```bash
uname -m
```

This command will return the machine hardware name. For example, `x86_64` indicates that you're running on a AMD 64.&#x20;

#### Install AMD 64 Linux Binaries

<pre class="language-bash"><code class="lang-bash"><strong>curl https://polytope.com/releases/polytope-cli-latest-linux-amd64.gz | gzip -d > pt 
</strong><strong>chmod +x pt 
</strong><strong>sudo mv pt /usr/local/bin/
</strong>curl https://storage.googleapis.com/cillers-cli/cillers-cli-v0.0.13-linux-amd64.tar.gz | tar -xzvf -
sudo mv cillers-cli /usr/local/bin/cillers
</code></pre>

#### Install ARM 64 Linux Binaries

Not supported yet by Polytope.&#x20;

#### Install AMD 64 MacOS Binaries

<pre class="language-bash"><code class="lang-bash"><strong>curl https://polytope.com/releases/polytope-cli-latest-macos-amd64.gz | gzip -d > pt 
</strong><strong>chmod +x pt 
</strong><strong>sudo mv pt /usr/local/bin/
</strong>curl https://storage.googleapis.com/cillers-cli/cillers-cli-v0.0.13-macos-amd64.tar.gz | tar -xzvf -
sudo mv cillers-cli /usr/local/bin/cillers
</code></pre>

#### Install ARM 64 MacOS Binaries

<pre class="language-bash"><code class="lang-bash"><strong>curl https://polytope.com/releases/polytope-cli-latest-macos-arm64.gz | gzip -d > pt 
</strong><strong>chmod +x pt 
</strong><strong>sudo mv pt /usr/local/bin/
</strong>curl https://storage.googleapis.com/cillers-cli/cillers-cli-v0.0.13-macos-arm64.tar.gz | tar -xzvf -
sudo mv cillers-cli /usr/local/bin/cillers
</code></pre>

## Running Cillers

Make sure that OrbStack (MacOS users) or Docker Desktop (Linux/Windows users) is running. The `pt run stack` command will otherwise wait until one of them is running.&#x20;

&#x20;And, ensure that you have enough memory allocated for OrbStack/Docker Desktop, at least 8GB.&#x20;

```bash
cillers new my-system
cd my-system
pt run stack
```

The start up will take a few minutes extra the during the first startup, due to downloads of Docker containers and package installations. The first startup run takes around 5 to 10 minutes.&#x20;

### Web User Interfaces

When the system has fully initialized you will be able to reach the following web UIs.

| Web UI       | URL                                                          | Credentials                                                                         |
| ------------ | ------------------------------------------------------------ | ----------------------------------------------------------------------------------- |
| Web frontend | [http://localhost:8080/](http://localhost:8080/)             | Create a new user in the Curity UI that you are redirected to when clicking login.  |
| Curity Admin | [https://localhost:6749/admin](https://localhost:6749/admin) | <p>Username: admin<br>Password: password</p>                                        |
| Couchbase    | [http://localhost:8091/](http://localhost:8091/)             | <p>Username: admin<br>Password: password</p>                                        |
| Redpanda     | [http://localhost:8079/](http://localhost:8079/)             | N/A                                                                                 |

### API UI Client

Open Insomnia and import the following collection, if you haven't already: [https://cillers-com.github.io/insomnia-cillers-graphql-client/localhost.json](https://cillers-com.github.io/insomnia-cillers-graphql-client/localhost.json)

Send the hello request. Insomnia should open up a Curity web login page for you. Create an account on your local Curity server using this page, if you haven't already. If you have already created an account, you can just log in.&#x20;

## Common Problems

Use our [Trouble Shooting Guide](trouble-shooting.md) if you run into problems. And, please post any issues that you run into on our [Discord server](https://discord.gg/awFYddKwCw).&#x20;
