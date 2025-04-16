# Installation For Windows Users

### Install WSL2 (Windows Subsystem For Linux)

To run Cillers on Windows you need the latest version of WSL2.&#x20;

**Attention!** If you already have WSL installed on your computer, make sure you have the **latest version**!&#x20;

Here are the official [installation instructions](https://learn.microsoft.com/en-us/windows/wsl/install).&#x20;

To avoid memory contraint issues, allocate at least 12GB of RAM in the .wslconfig. To avoid very slow startup allocate at least 4 CPUs.&#x20;

### Install Docker Desktop&#x20;

[Install Docker Desktop](https://docs.docker.com/desktop/install/windows-install/) or check that your current installation is up-to-date.&#x20;

**Attention!** We do not support old versions of Docker.&#x20;

### Enable Docker Desktop WSL2 Backend.&#x20;

See instructions here: [https://docs.docker.com/desktop/wsl/](https://docs.docker.com/desktop/wsl/). **Attention!** Make sure you have the **latest version** of Docker.&#x20;

### Ensure that you have enough memory allocated for Docker

Instructions: [https://mrakelinggar.medium.com/set-up-configs-like-memory-limits-in-docker-for-windows-and-wsl2-80689997309c](https://mrakelinggar.medium.com/set-up-configs-like-memory-limits-in-docker-for-windows-and-wsl2-80689997309c)

### Continue with the Installation Guide For Linux Users

You can now follow the [Installation Guide For Linux Users](installation-for-linux-users.md). Launch the WSL2 Shell and run the installation commands in there.&#x20;

### Important Special Git Instruction For Windows Users <a href="#important-special-git-instruction-for-windows-users" id="important-special-git-instruction-for-windows-users"></a>

Make sure your git client is committing UNIX-style line endings. Otherwise you will have problems working with developers on other operating systems.&#x20;

We recommend that you use the [Git for Windows](https://git-scm.com/download/win) client.
