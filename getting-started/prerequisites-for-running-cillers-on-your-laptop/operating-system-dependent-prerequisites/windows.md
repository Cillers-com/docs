# Windows

You need Windows Subsystem for Linux (WSL) to run Cillers. We recommend that you get WSL by installing Ubuntu from the Microsoft Store.&#x20;

Make sure that your WSL is up to date.&#x20;



INSTRUCTIONS

#### Step 1: Enable the Windows Subsystem for Linux

1. **Open PowerShell as Administrator**:
   * Right-click the Start button, select “Windows PowerShell (Admin)” or “Command Prompt (Admin)”.
2. **Enable the WSL feature**:
   * In the PowerShell window, type the following command and press Enter:
   *



```
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

#### Step 2: Enable Virtual Machine Feature (if on Windows 10)

If you're using Windows 10, you'll also need to enable the Virtual Machine Platform:

*   In the same PowerShell (Admin) window, type the following command and press Enter:

    ```bash
    bashCopy codedism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
    ```

#### Step 3: Download and Install a Linux Distribution

1. **Open the Microsoft Store**:
   * You can do this by clicking on the Store icon in your taskbar, or by searching for “Microsoft Store” in the start menu.
2. **Search for Linux**:
   * In the Microsoft Store, search for “Linux”. You will see various distributions available such as Ubuntu, Debian, or Kali Linux.
3. **Choose a distribution and install**:
   * Click on the Linux distribution you want to install, and then click “Get” or “Install”.

#### Step 4: Set up Your Linux Distribution

1. **Launch the newly installed Linux application**:
   * After installation, you can launch the Linux distribution via the Start menu.
2. **Follow the on-screen instructions**:
   * The first time you launch a new Linux distribution, a console window will open, and you’ll need to wait for files to de-compress and be stored on your machine. Then, you will need to create a user account and password for your new Linux distribution.

#### Step 5: Update and Upgrade (Optional but Recommended)

*   It's a good idea to update and upgrade your new Linux distribution. To do so, open your Linux distribution via the Start menu and run:

    ```bash
    bashCopy codesudo apt update && sudo apt upgrade
    ```

#### Step 6: Install WSL 2 (Optional, for Windows 10 and Recommended for Windows 11)

If you want to use WSL 2, which provides a more feature-complete and faster environment, ensure you have Windows 10 version 1903 or higher or any version of Windows 11, then run:

1. **Open PowerShell as Administrator again**.
2.  **Set WSL default version to 2**:

    ```bash
    bashCopy codewsl --set-default-version 2
    ```
3. **Download the Linux kernel update package** (for Windows 10):
   * Visit Microsoft’s official WSL2 kernel update page and download the latest WSL2 Linux kernel update package. Install it by following the instructions on the page.
4.  **Verify WSL version**:

    ```bash
    bashCopy codewsl --list --verbose
    ```

After these steps, you should have WSL installed and ready to use on your Windows laptop. If you encounter any issues during installation, checking Microsoft's official documentation or their support forums can be helpful.
