---
description: >-
  Quick reference guide covering what Bluetext is, how it works with Polytope
  and your coding agent, and how to get everything set up so you can start
  building full-stack apps in minutes.
---

# Bluetext Cheat Sheet

## Bluetext, Polytope & The Coding Agent

**Bluetext** is a tool that enables coding agents (and experienced developers) to quickly scaffold an infrastructure ready for enterprise adoption. It is a repository of tools that are given to the coding agent for disposal through the **Polytope** MCP server. **Polytope** ensures proper containerization, environment management, and dependency handling for every service created through these tools.&#x20;

Once a coding agent is configured to use Bluetext, it interprets your high-level requirements and automatically calls the appropriate tools to scaffold your application.&#x20;

<div data-with-frame="true"><figure><img src=".gitbook/assets/Gemini_Generated_Image_fxjv6sfxjv6sfxjv (1).png" alt="" width="563"><figcaption></figcaption></figure></div>

The diagram above illustrates how these three components work together. When you describe what you want to build, the coding agent interprets your requirements and sends structured tool calls to Polytope's MCP server. Polytope acts as the orchestration layer, translating these requests into concrete actions by accessing Bluetext's repository of templates and scaffolding tools. Bluetext provides the infrastructure blueprints—FastAPI services, React frontends, database configurations—which Polytope then deploys as containerized services.&#x20;

## Setting up your Environment for Bluetext

**Bluetext** does require you to have a number of tools installed on your machine, however your virtual machines come pre-installed with these! These tools include:

* Docker
* Docker Desktop
* Cline (Coding Agent)
* Polytope

There are also a few things you need to do to configure Vscode-server for generating with Bluetext, however the Bluetext Extension automates the process. All you need to do is create an empty working directory, using the following command in the vscode terminal:

```markdown
mkdir projectname
```

then navigate to it:

\
Then, when sitting in the new empty directory, open the Bluetext Extension from the activity bar of your Vscode:

<div data-with-frame="true"><figure><img src=".gitbook/assets/Screenshot 2025-11-28 at 13.33.02 (1).png" alt=""><figcaption></figcaption></figure></div>

Press "continue to workspace" and the extension will quickly check if the prerequisites are installed on the machine. Because these come pre-installed on your machines, these tests will pass. Then, because our project is not setup for bluetext, the Quick Setup-wizard will show up on your screen. You can select "run quick setup" to do so. this initialises the git repository (to ...), creates a polytope.yml file (which makes the bluetext tools accessible to polytope), checks if docker daemon is currently running, and configures a coding agent (we will choose Cline)

After this, we will be taken to the MCP tools section. Press  "start MCP server" at the top, and now, your setup should look something like this, with Polytope open in a terminal window at the bottom, and the tools available on the left.&#x20;

<div data-with-frame="true"><figure><img src=".gitbook/assets/Screenshot 2025-11-28 at 13.47.18.png" alt=""><figcaption></figcaption></figure></div>

## Common Terminal Commands

To make a new directory: `mkdir` &#x20;

To&#x20;

