# Installation With The Cillers Install Script

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

```bash
curl -O https://github.com/Cillers-com/cillers-cli/install.sh
chmod +x install.sh
./install.sh
```

