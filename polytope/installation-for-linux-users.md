# Installation For Linux Users

On Linux it is easiest to install the appropriate binaries directly using the following commands.&#x20;

### Figure Out Which Architecture Your Processor Has

The following command will return the machine hardware name. For example, `x86_64` indicates that you're running on a AMD 64.&#x20;

```bash
uname -m
```

We currently only support AMD 64 for Linux. Please let us know if you have a ARM64 processor, so we know that we should increase priority for supporting ARM64 processors for Linux.&#x20;

### Install Polytope CLI Binaries

```bash
curl -s https://polytope.com/install.sh | sh -s
```

### Docker&#x20;

**This section is not applicable to Windows users, since they should already have followed the Docker Desktop instructions for Windows.** \
\
Ensure that docker is installed and up-to-date. Polytope does not support old versions of Docker.&#x20;

Docker needs to run in rootless mode on Linux. Otherwise files created in mounted directories by code running in containers will be owned by the root user so the user will not have access to the created files.&#x20;

#### Rootless Docker on Ubuntu

This assumes that you have Ubuntu version 24+.

**Install Prerequisites**

```bash
sudo apt -y install uidmap
```

**Create an AppArmor Profile for rootlesskit by running the following block of commands.**

```bash
APPARMOR_FILE="/etc/apparmor.d/home.$USER.bin.rootlesskit"
USER_HOME=$(eval echo ~$USER)

cat <<EOT | sudo tee "$APPARMOR_FILE"
# ref: https://ubuntu.com/blog/ubuntu-23-10-restricted-unprivileged-user-namespaces
abi <abi/4.0>,
include <tunables/global>

~/bin/rootlesskit flags=(unconfined) {
  userns,

  # Site-specific additions and overrides. See local/README for details.
  include if exists <local/home.$USER.bin.rootlesskit>
}
EOT
```

**Enable unpriviledeged user namespaces**

```bash
echo 0 | sudo tee /proc/sys/kernel/apparmor_restrict_unprivileged_userns
```

**Install rootless Docker**

```bash
curl -fsSL https://get.docker.com/rootless | sh
```

**Add the following lines to `~/.bashrc`**

```bash
export PATH="$HOME/bin:$PATH"
export DOCKER_HOST="unix:///run/user/$UID/docker.sock"
```

**Load the \~/.bashrc**

```bash
source ~/.bashrc
```

**Start the rootless Docker daemon**

```bash
systemctl --user start docker
```

**Test the Docker daemon**

```bash
docker info
docker run hello-world
```



#### **Docker Desktop**

[Installing Docker Desktop](https://docs.docker.com/desktop/install/linux-install/) is optional for Linux users.
