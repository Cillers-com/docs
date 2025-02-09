# Hardware And OS Requirements

## RAM Requirements

Which components you choose to include in your Cillers system will affect the hardware requirements for being able to run the system on your computer smoothly. With a minimal configuration you will not need much, but if you're building an enterprise-grade system you would need at least 16GB of RAM. &#x20;

If you want to run a heavy stack, but you don't have enough RAM, we recommend that you run memory heavy services in the cloud, e.g. we have support for connecting your local development stack with Couchbase's cloud service Capella which includes a free tier, but it will take slightly more effort to configure your development environment.

## Processor Requirements

Some processors that are older than around 2015 may have issues.&#x20;

## OS Requirements

Cillers runs on the latest versions of macOS, Windows and Linux.&#x20;

<table><thead><tr><th width="171">OS</th><th>Versions</th><th>Processors</th></tr></thead><tbody><tr><td>macOS</td><td>Latest version of macOS. Currently, macOS Sonoma. </td><td>AMD 64 (Intel) and ARM 64 (M1, M2, M3)</td></tr><tr><td>Windows</td><td>Latest version of Windows. Currently, Windows 11. </td><td>AMD 64.  Please let us know if you have a ARM 64 processor, so we can prioritize this.</td></tr><tr><td>Linux</td><td>Cillers generally operates well across most Linux distributions, but you may encounter issues depending on the version and distribution you are using. In particular, there is an outstanding problem with running our Identity Provisioning Service, Curity, on Arch Linux and on machines with an extremely high ulimit. </td><td>AMD 64. Please let us know if you have a ARM 64 processor, so we can prioritize this. </td></tr></tbody></table>
