# Installation of Cillers and Dependencies

The easiest way to install Cillers is with Homebrew.&#x20;

Alternatively, you can use our installation shell script, but then you will have to install all software dependencies yourself.  If you want to use our installation shell script, follow these [instructions](altnerative-way-to-install-cillers-the-cillers-install-script.md).&#x20;

### Installation With Homebrew

Here are the instructions for how to install Cillers and all software dependencies using Homebrew.

### 1. Update Homebrew&#x20;

```bash
brew update
```

If you don't already have Homebrew installed, you can install it with the following command.&#x20;

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### 2. Install Cillers And Dependencies

```bash
brew install polytopelabs/tap/polytope-cli
brew install cillers-com/tap/cillers
brew install --cask insomnia
brew install --cask orbstack # if you are a macOS user
```

