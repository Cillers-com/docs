# Trouble Shooting

## Getting Started With Cillers Should Be Trouble Free. <a href="#getting-started-with-cillers-should-be-trouble-free" id="getting-started-with-cillers-should-be-trouble-free"></a>

We provide free support! You can book a free support call here if you run into any issues: [https://calendly.com/cillers/free-support](https://calendly.com/cillers/free-support)

You can also reach us at our [Discord server](https://discord.gg/awFYddKwCw) or check out our [Trouble Shooting Guide](https://docs.cillers.com/getting-started/trouble-shooting).

## General

* Make sure that OrbStack (MacOS users) or Docker Desktop (Linux/Windows users) is running. The `pt run stack` command will otherwise wait until one of them is running.&#x20;
* Insufficient memory allocated to OrbStack/Docker Desktop.&#x20;
* Running other services that occupy the same ports as are used by Cillers.&#x20;
* Old processors. Polytope may have problems running on processors older than 2015.&#x20;
* Polytope doesn't start because another old command called pt installed since before. Read the error message of the brew install polytope command.&#x20;

Run the Polytope doctor command to see if there are any problems with the basic installation. This command will provide warnings if anything that Polytope depends on is not installed in alignment with their recommendations.

```bash
pt debug doctor
```

## Windows

* Running an old version of Windows. Polytope requires Windows 11 at least.&#x20;
* Windows users that have an old version of WSL installed. Make sure you have the latest version of WSL2 installed. Polytope will likely fail otherwise.&#x20;
* Docker socket permission error: "permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get "http://%2Fvar%2Frun%2Fdocker.sock/v1.45/containers/json": dial unix /var/run/docker.sock: connect: permission denied". This can be solved by running the following commands:&#x20;

```bash
sudo usermod -aG docker $(whoami)
newgrp docker
```

## MacOS

* Running an old version of MacOS. Polytope requires the lastet version.&#x20;
* MacOS users that run Docker Desktop instead of OrbStack. Docker Desktop is way more inefficient and will very likely cause problems for you.&#x20;
