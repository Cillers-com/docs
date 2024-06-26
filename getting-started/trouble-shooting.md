# Trouble Shooting

## General

* Make sure that OrbStack (MacOS users) or Docker Desktop (Linux/Windows users) is running. The `pt run stack` command will otherwise wait until one of them is running.&#x20;
* Running other services that occupy the same ports as are used by Cillers.&#x20;

## Windows

* Windows users that have an old version of WSL installed. Make sure you have the latest version of WSL2 installed. Polytope will likely fail otherwise.&#x20;
* Docker socket permission error: "permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get "http://%2Fvar%2Frun%2Fdocker.sock/v1.45/containers/json": dial unix /var/run/docker.sock: connect: permission denied". This can be solved by running the following commands:&#x20;

```bash
sudo usermod -aG docker $(whoami)
newgrp docker
```

## MacOS

* MacOS users that run Docker Desktop instead of OrbStack. Docker Desktop is way more inefficient and will very likely cause problems for you.&#x20;
