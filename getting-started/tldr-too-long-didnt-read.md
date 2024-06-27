# TLDR (Too Long; Didn't Read)

Here is all you typically need to do to get started with Cillers, but you may want to read through the full Getting Started documentation to ensure a smooth experience.&#x20;

## Special Preparations For Windows Users

Note that Windows users will need to install WSL2 (Windows Subsystem For Linux) first, and run the commands below in the WSL2 shell. &#x20;

Windows users also need to enable Docker Desktop WSL2 Backend. See instructions here: [https://docs.docker.com/desktop/wsl/](https://docs.docker.com/desktop/wsl/)&#x20;

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
</strong>curl https://storage.googleapis.com/cillers-cli/cillers-cli-v0.0.13-linux-amd64.tar.gz --output cillers-cli.tar.gz
tar -xzvf ./cillers-cli.tar.gz
sudo mv cillers-cli /usr/local/bin/cillers
</code></pre>

#### Install ARM 64 Linux Binaries

Not supported yet by Polytope.&#x20;

#### Install AMD 64 MacOS Binaries

<pre class="language-bash"><code class="lang-bash"><strong>curl https://polytope.com/releases/polytope-cli-latest-macos-amd64.gz | gzip -d > pt 
</strong><strong>chmod +x pt 
</strong><strong>sudo mv pt /usr/local/bin/
</strong>curl https://storage.googleapis.com/cillers-cli/cillers-cli-v0.0.13-macos-amd64.tar.gz --output cillers-cli.tar.gz
tar -xzvf ./cillers-cli.tar.gz
sudo mv cillers-cli /usr/local/bin/cillers
</code></pre>

#### Install ARM 64 MacOS Binaries

<pre class="language-bash"><code class="lang-bash"><strong>curl https://polytope.com/releases/polytope-cli-latest-macos-arm64.gz | gzip -d > pt 
</strong><strong>chmod +x pt 
</strong><strong>sudo mv pt /usr/local/bin/
</strong>curl https://storage.googleapis.com/cillers-cli/cillers-cli-v0.0.13-macos-arm64.tar.gz --output cillers-cli.tar.gz
tar -xzvf ./cillers-cli.tar.gz
sudo mv cillers-cli /usr/local/bin/cillers
</code></pre>



## Running Cillers

```bash
cillers new my-system
cd my-system
pt run stack
```

## Common Problems

* Windows users that have an old version of WSL installed. Make sure you have the latest version of WSL2 installed. Polytope will likely fail otherwise.&#x20;
* MacOS users that run Docker Desktop instead of OrbStack. Docker Desktop is way more inefficient and will very likely cause problems for you.&#x20;
* Make sure that OrbStack (MacOS users) or Docker Desktop (Linux/Windows users) is running. The `pt run stack` command will otherwise wait until one of them is running.&#x20;
* Running other services that occupy the same ports as are used by Cillers.&#x20;
