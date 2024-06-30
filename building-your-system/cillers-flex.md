# Cillers Flex

You may want to add some infrastructure capabilities that are not within the current scope of Cillers Core. You can then extend the system by creating adding a new Polytope module to your stack.&#x20;

The Cillers system infrastructure is specified in the `/polytope.yml` file. We look forward to having better documentation to offer on how to do this. For now, we will leave you with checking out how we use Polytope. Polytope are also working on improving their documentation. You can find it here: [https://polytope.com/docs](https://polytope.com/docs)

### High Level Description Of Polytope

We specify what should be run in our stack in the `templates` section.  The `modules` that the `templates` are comprised of are specified in the `modules` section. Each module is an extension of another module that is called with the `args` field. The base module is called `polytope/container`.&#x20;

Modules that should run our code have a `code` field with the path to the code that should be run and a `cmd` field with the entry point command that should be called to run our code.&#x20;

Modules for services, such as databases, contain configuration for how the service should be run including which specific container image should be used.&#x20;

Module can be specified to take params which define the interface for the module. They can be specified my extending modules through the args field. And they can be specified when the module is invoked through the Polytope Container Runtime UI.&#x20;
