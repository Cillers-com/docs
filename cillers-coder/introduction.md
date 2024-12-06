# Introduction

Welcome to Cillers Coder - a powerful software development tool that allows you to harness the capabilities of Large Language Models (LLMs) to create robust, enterprise-grade software systems. Think of it as your AI pair programming assistant, ready to help you turn your ideas into high-quality code.

### How it Works

At its core, Cillers Coder operates similarly to other code generation tools you may have used. You start by specifying your current development goal or the changes you want to make to your codebase. Cillers Coder then generates a proposed set of code changes that align with your intention.

But here's where Cillers Coder really shines - before automatically applying any changes, it provides you with full visibility into all the files that will be created or modified, along with git-style diffs showing the exact changes for existing files. This allows you to review and confirm the changes, ensuring they meet your expectations.

### Generating Code That Fits Your Needs

Cillers Coder offers several key features to help you generate code that precisely matches your requirements and coding standards:

* **Policies**: You can define policies that guide Cillers Coder to generate code aligned with your team's preferences and guidelines. Policies are organized into groups which can be scoped to apply in specific situations.
* **Facts**: Sometimes the LLM may not be aware of recent developments that impact your code, like a newly deprecated package. With Facts, you can provide up-to-date information to ensure Cillers Coder uses the latest best practices. Like policies, facts can be grouped and scoped.
* **Restrictions**: To maintain control over your codebase, you can set restrictions that Cillers Coder must adhere to. For example, you can specify that changes must be contained within certain directories, or that specific files or directories are off-limits for modifications.

Cillers Coder also allows you to designate files to exclude when generating the context for the LLM, such as image files or package directories. This helps keep the prompts focused and relevant.

### Handling Large Codebases

Despite LLM limitations on output token counts, Cillers Coder is designed to work effectively with sizeable codebases - up to around 50,000 lines of code, assuming an average of 20 characters per line. It achieves this through intelligent LLM interaction techniques.

### Integration with Cillers Stack

Cillers Coder is purpose-built to enable development of enterprise systems on the Cillers Stack. When you create a new Cillers Stack, Cillers Coder comes integrated out of the box.

