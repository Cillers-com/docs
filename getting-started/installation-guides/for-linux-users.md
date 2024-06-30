# For Linux Users

On Linux it is easiest to install the appropriate binaries directly using the following commands.&#x20;

### Figure Out Which Architecture Your Processor Has

The following command will return the machine hardware name. For example, `x86_64` indicates that you're running on a AMD 64.&#x20;

```bash
uname -m
```

We currently only support AMD 64 for Linux. Please let us know if you have a ARM64 processor, so we know that we should increase priority for supporting ARM64 processors for Linux.&#x20;

### Install Polytope And Cillers CLI Binaries

<pre class="language-bash"><code class="lang-bash"><strong>curl https://polytope.com/releases/polytope-cli-latest-linux-amd64.gz | gzip -d > pt 
</strong><strong>chmod +x pt 
</strong><strong>sudo mv pt /usr/local/bin/
</strong>curl https://storage.googleapis.com/cillers-cli/cillers-cli-v0.0.13-linux-amd64.tar.gz | tar -xzvf -
sudo mv cillers-cli /usr/local/bin/cillers
</code></pre>

### Install Kong Insomnia

Use the [official installation instructions.](https://insomnia.rest/download)&#x20;

### Ensure You Have The Latest Version Of Docker Installed (Not For Windows Users)

[Install Docker Desktop](https://docs.docker.com/desktop/install/linux-install/) or check that your installation is up-to-date. Polytope does not support old versions of Docker.&#x20;

Ensure you have at least 8GB memory allocated to Docker Desktop.&#x20;

1. Open the Docker Desktop dashboard

<figure><img src="../../.gitbook/assets/image (12).png" alt="" width="339"><figcaption></figcaption></figure>

2. Open settings

<figure><img src="../../.gitbook/assets/image (1) (1) (1).png" alt="" width="302"><figcaption></figcaption></figure>

3. Open Resources

<figure><img src="../../.gitbook/assets/image (2) (1) (1).png" alt="" width="250"><figcaption></figcaption></figure>

4. Increase memory limit to at least 8 GB

<figure><img src="../../.gitbook/assets/image (3) (1) (1).png" alt="" width="375"><figcaption></figcaption></figure>
