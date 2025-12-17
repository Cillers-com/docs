# Polytope & MCPs

**Polytope** is responsible for running your application inside containers and orchestrating them. You define what runs and how it runs (for example, your frontend) in configuration files such as `polytope.yml`. In most cases, this setup is handled automatically through Bluetext. You only need to modify these configurations if you want to change container behavior, such as injecting environment variables.

Within Polytope, you can inspect which containers are running, view their logs, and see which services your application exposes and on which ports. Polytope also provides built-in development tools that are exposed to the coding agent, as well as support for custom, self-defined tools.

Bluetext is built on top of this infrastructure. It defines higher-level tools for scaffolding code, running services through Polytope, and supporting day-to-day development workflows
