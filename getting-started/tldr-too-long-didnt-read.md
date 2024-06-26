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

MacOS users also run the following (Cask only works on MacOS so Linux/Windows users will have to install Kong Insomnia manually).

```bash
brew install --cask orbstack
brew install --cask insomnia 
```

### Installation Alternative 2: Bash

```bash
curl https://polytope.com/releases/polytope-cli-latest-linux-amd64.gz | gzip -d > pt chmod +x pt sudo mv pt /usr/local/bin/
curl https://storage.googleapis.com/cillers-cli/cillers-cli-v0.0.13-linux-amd64.tar.gz --output cillers-cli.tar.gz
tar -xzvf ./cillers-cli.tar.gz
sudo mv cillers-cli /usr/local/bin/cillers
```

Note that you will need to install Kong Insomnia manually using this approach.&#x20;

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
