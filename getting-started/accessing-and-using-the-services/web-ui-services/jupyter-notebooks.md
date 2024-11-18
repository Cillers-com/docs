# Jupyter Notebooks

Your Jupyter app is located at [http://localhost:8888](http://localhost:8888).&#x20;

Jupyter is a great way to get familiar with software technologies because of its flexible environment where users can write and execute code in small, manageable chunks, immediately seeing the results in combination with its ability to combine code with rich text explanations.&#x20;

The Cillers Jupyter app closely mimics the code environment that the Cillers API app runs in. So, you can experiment with how to build your API code by first trying it out in a Jupyter notebook.&#x20;

You can also try out our growing library of tutorials for how to build different functionalities into your API.&#x20;

## Credentials And Config

Credentials and config can be loaded with the `env.py` module in the Jupyter `\tutorials` directory. This module supports loading the default public credentials for localhost setups and secret credentials that should not be checked in to the git repository.  It also supports loading default shared config and local config.&#x20;

The default public credentials for localhost, which are provided to enable a turn-key developer experience, are loaded from the `/conf/jupyter/credentials-public.yml` file. And, the shared configs are loaded from the `/conf/jupyter/config-shared.yml` file. Both of these files are provided out of the box and are checked in to the git repository. So, be mindful not to put any secret info in one of these files.

The secret credentials and local configs are loaded from the `credentials.yml` and `config-local.yml` files in the `conf/jupyter/secrets_and_local_config` directory. All files in this directory are ignored by git. You will need to create these files. You will be able to edit them in Jupyter or in your code editor of choice.&#x20;

The contents of the secret credentials and local config files override any values specified in their shared counterparts.&#x20;

## The 'work' Directory

The purpose of the Jupyter work directory is for developers to create their own notebooks that are not shared with others, but that are persisted to their local disk.

The Cillers Jupyter setup adheres to these semantics in the following way. Any files that you create in the Jupyter `work` directory will be ignored by your git repository, but will be persisted to your disk in the `cillers/jupyter/work` directory.&#x20;

## Tutorials

We have created a growing library of Jupyter tutorials that is accessible in the `/tutorials` directory.&#x20;

<figure><img src="../../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

## Mounted Directories

The `/tutorial`, `/work` and`/config`directories are mounted from your Cillers project directory into the container running Jupyter. This means that you can edit these files in Jupyter or using your favorite code editor.&#x20;

But, note that the Cillers Jupyter app is intended to be run in a container that is closely equivalent to the the API app container. The Jupyter notebooks are not intended to be executed on your local operating system, so you should not expect them to execute properly in your code editor.&#x20;

Here is a table for which directories are mounted:&#x20;

| Jupyter Directory | Cillers Project Directory |
| ----------------- | ------------------------- |
| /tutorials        | cillers/jupyter/tutorials |
| /work             | cillers/jupyter/work      |
| /config           | conf/jupyter/             |

