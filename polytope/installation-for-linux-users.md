# Installation For Linux Users

On Linux it is easiest to install the appropriate binaries directly using the following commands.&#x20;

### Figure Out Which Architecture Your Processor Has

The following command will return the machine hardware name. For example, `x86_64` indicates that you're running on a AMD 64.&#x20;

```bash
uname -m
```

We currently only support AMD 64 for Linux. Please let us know if you have a ARM64 processor, so we know that we should increase priority for supporting ARM64 processors for Linux.&#x20;

### Install Polytope CLI Binaries

<pre class="language-bash"><code class="lang-bash"><strong>curl https://polytope.com/releases/polytope-cli-latest-linux-amd64.gz | gzip -d > pt 
</strong><strong>chmod +x pt 
</strong><strong>sudo mv pt /usr/local/bin/
</strong></code></pre>

### Docker (Not Applicable For Windows Users That Should Already Have Followed The Docker Desktop Instructions For Windows)

Ensure that docker is installed and up-to-date. Polytope does not support old versions of Docker.&#x20;

[Installing Docker Desktop](https://docs.docker.com/desktop/install/linux-install/) is optional for Linux users.
