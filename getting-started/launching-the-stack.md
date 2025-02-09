# Launching The Stack

Make sure that OrbStack (MacOS users) or Docker Desktop (Linux/Windows users) is running. The `cillers run` command will just wait for it to start otherwise.&#x20;

Run the following command in your project's directory (the `my-system` directory unless you named it otherwise).

```
cillers run dev
```

You should now see the Polytope Container Runtime UI.

<figure><img src="../.gitbook/assets/image (5) (1).png" alt=""><figcaption></figcaption></figure>

Just like in any operating system, some processes, such as init scripts, run to completion and some, such as databases, should be kept running.&#x20;

Use the guide at the bottom of the Polytope UI to navigate. You will find the Polytope UI to be incredibly helpful and powerful.&#x20;

**Attention!** If you are on a bad network, you may have to restart the "cillers run dev" command to get the initialization to complete, because of problems to load container images.
