# Getting Started

To start using Cillers Coder, you'll need to install an API key which you can obtain by contacting Cillers at hello@cillers.com. Once you have your key, run `cillers set-api-key` and paste in the provided key when prompted. The key is stored in `~/.cillers/api_key.txt` and will be used across all your projects, so you only need to set it once.

If you are using Cillers Coder to develop your Cillers System, you can read more about how to do that in the section about that[ here](using-cillers-coder-to-develop-your-cillers-system.md). Cillers Coder is integrated in new Cillers Systems out of the box.

You can also use Cillers Coder to develop any software project. To initialize Cillers Coder for your code project, call `cillers coder-init` in the root source code directory of your project. That will result in a `.cillers/coder` directory being created with the needed files and directories.&#x20;

Open the `.cillers/coder/instructions` file and specify what you want to build or change. Save the file and run `cillers implement` or `cillers i` for short. You will then be presented with a Change Proposal that you can review before applying it to your project.&#x20;



