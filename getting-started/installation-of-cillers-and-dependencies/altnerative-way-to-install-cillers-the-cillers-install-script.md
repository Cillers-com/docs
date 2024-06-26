---
description: >-
  Attention: These instructions are only relevant if you have not already
  installed Cillers using Homebrew.
---

# Altnerative Way To Install Cillers: The Cillers Install Script

### Install Software Dependencies

When installing Cillers with the install script you will first need to install all software dependencies.

| Software Dependency                                                | Installation Instructions                                                                                                      |
| ------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------ |
| Git                                                                | [https://git-scm.com/book/en/v2/Getting-Started-Installing-Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) |
| Docker                                                             | [https://docs.docker.com/engine/install](https://docs.docker.com/engine/install)                                               |
| Polytope                                                           | [https://polytope.com/docs/quick-start](https://polytope.com/docs/quick-start)                                                 |
| Insomnia by Kong                                                   | [https://docs.insomnia.rest/insomnia/install](https://docs.insomnia.rest/insomnia/install)                                     |
| Only for Windows Users: Install Windows Subsystem for Linux (WSL2) | [https://learn.microsoft.com/en-us/windows/wsl/install](https://learn.microsoft.com/en-us/windows/wsl/install)                 |

### Install The Cillers CLI

The Cillers CLI enables you to create a new Cillers system. It will shortly also include support for managing the state of the underlying technologies as well as creating boilerplate code for adding new features to the system.

Download the binary, unpack and make it executable.&#x20;

URLs to the binaries for the different platforms:

* https://storage.googleapis.com/cillers-cli/cillers-cli-v0.0.13-linux-amd64.tar.gz
* https://storage.googleapis.com/cillers-cli/cillers-cli-v0.0.13-linux-arm64.tar.gz
* https://storage.googleapis.com/cillers-cli/cillers-cli-v0.0.13-macos-amd64.tar.gz
* https://storage.googleapis.com/cillers-cli/cillers-cli-v0.0.13-macos-arm64.tar.gz

```bash
curl https://storage.googleapis.com/cillers-cli/cillers-cli-v0.0.13-linux-amd64.tar.gz --output cillers.tar.gz
tar -xzvf ./cillers.tar.gz
sudo mv cillers /usr/local/bin
```

