---
description: >-
  This section outlines how to recognise and resolve issues caused by incorrect
  Polytope or Bluetext setup.
---

# Common Issues

## Incorrect Configuration

If Polytope and Bluetext are not set up correctly, your configuration or output files will look different from the expected structure. The examples below illustrate common signs of incorrect setup, so you can quickly identify and fix any issues before proceeding.

An indicator that there is an issue either with the Polytope setup or Bluetext repository file is that cline will start to generate code, but the polytope UI will remain empty.&#x20;

A valid setup includes a **modules** folder. If your project appears without it, Polytope and/or Bluetext are not configured correctly. The image below demonstrates the expected project structure when the setup is successful.

<div data-full-width="true"><figure><img src="../.gitbook/assets/Screenshot 2025-10-23 at 12.57.33.png" alt="" width="563"><figcaption></figcaption></figure></div>



An example of the file structure resulting from an incorrect configuration may look similar to the following:&#x20;

<figure><img src="../.gitbook/assets/Screenshot 2025-10-23 at 13.25.32.png" alt=""><figcaption></figcaption></figure>



Most of the time, scripts will not be executed when using Bluetext. If Bluetext is configured correctly, the coding agent will primarily use tool calls to interact with the running application. If it is not configured correctly, you might see the coding agent attempt to execute commands directly on your machine. The only commands you should see running locally are curl commands.

The sole purpose of running curl commands directly on your machine is to test whether your services are reachable from outside the containers.
