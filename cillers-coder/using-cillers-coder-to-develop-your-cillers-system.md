# Using Cillers Coder To Develop Your Cillers System

The recommended workflow is to focus on one module of your Cillers Stack at a time, such as the web app or API. Navigate to the module's code directory (e.g., `code/api-python-graphql`) and use the `cillers implement` command, providing your instructions via the `.cillers/coder/instructions` file.

Module-specific policies and facts reside in the `.cillers/coder/policies` and `.cillers/coder/facts` directories within each module. For policies and facts that span across modules, place them in the corresponding directories at the project root. Restrictions are specified per module in the `.cillers/coder/restrictions` file.
