# TLDR (Too Long; Didn't Read)

Here is all you typically need to do to get started with Cillers, but you may want to read through the full Getting Started documentation to ensure a smooth experience.&#x20;

```bash
brew update
brew install polytopelabs/tap/polytope-cli
brew install cillers-com/tap/cillers
brew install --cask insomnia
brew install --cask orbstack # if you are a macOS user
cillers new my-system
cd my-system
pt run stack
```

Make sure that OrbStack or Docker Desktop is running. The `pt run stack` command will otherwise wait until one of them is running.&#x20;

Note that Windows users will need to install WSL2 (Windows Subsystem For Linux) first, and run the commands specified above in the Linux environment.&#x20;

And, if you don't have [Homebrew](http://brew.sh) installed, you will need to install that first to be able to run the above commands. The documentation includes instructions on how to install Cillers without Homebrew as well.&#x20;

### Special Instructions For Windows users

Make sure you have the latest version of WSL2 installed.&#x20;

Execute the following instructions in your WSL2 shell. These instructions assume you are on a amd64 architecture.&#x20;

#### Install Polytope

```bash
curl https://polytope.com/releases/polytope-cli-latest-linux-amd64.gz | gzip -d > pt chmod +x pt sudo mv pt /usr/local/bin/
```

#### &#x20;Install The Cillers CLI

```bash
curl https://storage.googleapis.com/cillers-cli/cillers-cli-v0.0.13-linux-amd64.tar.gz --output cillers-cli.tar.gz
tar -xzvf ./cillers-cli.tar.gz
sudo mv cillers-cli /usr/local/bin/cillers
```
