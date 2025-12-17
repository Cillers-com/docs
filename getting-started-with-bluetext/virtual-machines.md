---
description: A description on how to work with the virtual machine setup
---

# Virtual Machines

## 1. Logging in

You will receive an e-mail with log in credentials for Vscode-server and Chromium. We recommend logging into both and keeping the tabs open.&#x20;

## 2. Creating a directory for your project

When you open vscode-server you will be at the root directory by default. Navigate to Development and create a new directory here. This is how to create one.

```
root@dino360:~# cd ./Development/
root@dino360:~/Development# mkdir testproject
root@dino360:~/Development# cd testproject
root@dino360:~/Development/testproject# code .
```

then, click enter. The vs-code interface will refresh and you  should see your project name at the top in the search bar like this:

<figure><img src="../.gitbook/assets/Screenshot 2025-12-17 at 17.38.41.png" alt=""><figcaption></figcaption></figure>

Repeat these steps when creating a new project, so that you do not create multiple Bluetext projects in the same directory

## 3. View running services in Chromium

Once you have started running tools with Bluetext in Polytope, you can access them in Chromium. In the Polytope TUI, you will find a services section. Instead of clicking the adresses where they are being hosted, you must copy and paste them into chromium to view them.
