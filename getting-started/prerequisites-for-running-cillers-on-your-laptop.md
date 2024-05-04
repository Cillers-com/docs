# Prerequisites For Running Cillers On Your Laptop

For a good experience in getting started with Cillers, please go through this section with prerequisites thoroughly. If you miss something in these instructions, you may face difficulties when trying to launch and work with your Cillers system.&#x20;

### Hardware Requirements

<table><thead><tr><th width="174">Hardware</th><th>Requirement</th></tr></thead><tbody><tr><td>Processor</td><td>We have noticed that some processors that are older than around 2015  have issues. </td></tr><tr><td>Disk space</td><td>You may need up to 30 GB of disk space depending on how many of the prerequisite applications/services, such as Docker, you already have installed. </td></tr><tr><td>RAM</td><td>You may need up to 8GB of RAM depending on which platform you are on. Linux users may get away with only 4GB. </td></tr></tbody></table>

### Software Dependencies

<table><thead><tr><th width="253">Software</th><th>Dependency</th></tr></thead><tbody><tr><td>Polytope<br><a href="https://polytope.com/">https://polytope.com/</a></td><td>Cillers depends on Polytope to run system code and the underlying software technologies. </td></tr><tr><td>Docker<br><a href="https://www.docker.com/">https://www.docker.com/</a></td><td>Polytope depends on Docker to run software on local development computers.</td></tr><tr><td>Git<br><a href="https://git-scm.com/">https://git-scm.com/</a></td><td>The Cillers CLI depends on Git to create new systems.</td></tr><tr><td>OrbStack (only for macOS users)<br><a href="https://orbstack.dev/">https://orbstack.dev/</a></td><td>OrbStack is much more resource efficient than Docker Desktop on macOS. You may experience issues if trying to run Cillers on Docker Desktop because it is much more resource intensive than OrbStack.</td></tr><tr><td>Insomnia by Kong<br><a href="https://insomnia.rest/">https://insomnia.rest/</a></td><td>When working with Cillers, it is very convenient to have a API UI client that has support for GraphQL and setting up oAuth connections to the API. Insomnia by Kong is the best tool we've found for this purpose.</td></tr></tbody></table>

### Supported Operating Systems

<table><thead><tr><th width="167">OS</th><th>Versions</th></tr></thead><tbody><tr><td>macOS</td><td>Latest version of macOS. Currently, macOS Sonoma. </td></tr><tr><td>Windows</td><td>Latest version of Windows. Currently, Windows 11. </td></tr><tr><td>Linux</td><td>Cillers generally operates well across most Linux distributions, but you may encounter specific issues depending on the version and distribution you are using. In particular, there is an outstanding problem with running our Identity Provisioning Service, Curity, on Arch Linux. </td></tr></tbody></table>

