# Setting Up WSL2
WSL stands for Windows Subsystem for Linux. It is a feature that lets you run Linux programs on your Windows system. You can use WSL to run Git commands in a Linux environment. You can learn more about WSL from this website: https://docs.microsoft.com/en-us/windows/wsl/

## Step 1: Enable Windows Virtualization Features
To use WSL2, you need to ensure that Windows virtualization features are enabled. Follow these steps:

1. Search for "Turn Windows features on or off" in the Windows search bar and open it.
2. In the Windows Features dialog, scroll down and check the box next to "Virtual Machine Platform."
3. Underneath "Virtual Machine Platform", you should also find "Windows Hypervisor Platform", check that also.
4. Also, check the box next to "Windows Subsystem for Linux", to find that, go down a little bit.
5. Click "OK" and restart your computer when prompted.

## Step 2: Install WSL and Ubuntu
Once virtualization features are enabled, follow these steps to install WSL and Ubuntu:

1. Open PowerShell or CMD/Terminal as an administrator.
2. Type the following command to install WSL and set it to use the Ubuntu distribution:
   ```bash
   wsl --install -d Ubuntu
   ```
3. If for any reason that did not succeed, head to Microsoft Store and download the "WSL" package by searching for it.
4. After installation, you can find the Ubuntu application in the Microsoft Store. Search for "Ubuntu" in the Store and install it.

## Step 3: Update WSL to WSL2
Sometimes by default, WSL1 is installed. To update to WSL2, perform the following steps:

1. Open PowerShell or CMD/Terminal as an administrator.
2. Set WSL2 as the default version by running:
   ```bash
   wsl --set-default-version 2
   ```
3. Check the status of your WSL distributions to ensure that WSL2 is set as the default:
   ```bash
   wsl --status
   ```
4. Convert the Ubuntu distribution to WSL2 by running:
   ```bash
   wsl --set-version Ubuntu 2
   ```
5. You can verify that the conversion was successful by listing all WSL distributions and their versions:
   ```bash
   wsl --list --verbose
   ```

# Node.js on WSL

## Step 1: Update Ubuntu and Install Node.js using NVM
Before installing Node.js, make sure your system is up to date. Open your Ubuntu terminal and run the following commands:

1. Update the package list and upgrade existing packages:
   ```bash
   sudo apt update && sudo apt upgrade
   ```

2. If you don't have cURL already installed, install it:
   ```bash
   sudo apt-get install curl
   ```

3. Install NVM (Node Version Manager) using cURL:
   ```bash
   curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/master/install.sh | bash
   ```

4. Verify nvm installed, by entering: `command -v nvm` ...this should return 'nvm', if you receive 'command not found' or no response at all, close your current terminal, reopen it, and try again. [Learn more in the nvm github repo](https://github.com/nvm-sh/nvm).
5. If you still not able to verify nvm for some reason, try the following on the terminal:
   ```sh
   export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
   [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
   ```
   
7. Close and reopen your terminal or run `source ~/.bashrc` to load NVM.

## Step 2: Install Node.js using NVM
Now that NVM is installed, you can easily install Node.js:

1. Install the current sable version (LTS) of Node.js:
   ```sh
   nvm install --lts
   ```


2. List which versions of Node are currently installed (should be none at this point): `nvm ls`

    ![NVM list showing no Node versions](https://user-images.githubusercontent.com/75049983/254376881-4706a05a-ff82-422a-ae1b-ed0826d5f48b.png)

3. Verify that Node.js is installed correctly by checking its version:
   ```sh
   node -v
   ```

# VS Code on WSL

## Step 1: Install VS Code in Windows and Add to Path
Before setting up VS Code in WSL, make sure you have Visual Studio Code installed in your Windows environment:

1. Download and install VS Code from the official website: https://code.visualstudio.com/

2. During the installation, ensure the option "Add to PATH" is selected.

## Step 2: Install the Remote Development Extension
To work with VS Code in WSL, you need to install the Remote Development Extension. Follow these steps:

1. Open VS Code in Windows.

2. Go to the Extensions view by clicking on the Extensions icon in the Activity Bar on the side of the window.

3. Search for "Remote Development" in the Extensions view search bar.
![Screenshot 2023-07-18 211143](https://user-images.githubusercontent.com/75049983/254362244-5ac71d09-3f47-476f-980f-3222c222034a.png)

4. Start installing it.

## Step 3: Open a WSL Project in VS Code
Now, you're ready to open a project within WSL in VS Code:

1. Open your WSL terminal.

2. Navigate to your project's directory using the Linux file path.

3. Launch VS Code in WSL with the current directory loaded:
   ```bash
   code .
   ```

# Git on WSL and VS Code

## What is Git and why do you need it?

Git is a tool called Version/Source Control System (VCS). It helps you keep track of the changes you make to your code files. It also lets you work with other people on the same code files. You can learn more about Git from its official website: https://git-scm.com/

**Before** you can use Git with VS Code, you need to install Git on your Windows system. Here are the steps to do that:

## Step 1: Install Git on Windows
Before using Git within VS Code, you need to install it on your Windows system:

1. Download the Git installer for Windows from https://git-scm.com/download/win

2. Run the installer and follow the on-screen instructions to complete the installation.

3. After installation, you can access Git commands from both the Windows Command Prompt and WSL.

## Step 3: Configure Global Settings
Before you start using Git, you need to set your global configuration:

1. Open your WSL terminal.

2. Set your name for commit transactions:
   ```bash
   git config --global user.name "Your Name"
   ```

3. Set your email address for commit transactions:
   ```bash
   git config --global user.email "your.email@example.com"
   ```

4. Optionally, enable helpful colorization of command line output:
   ```bash
   git config --global color.ui auto
   ```

## Step 4: Git Basic Commands
Here are some essential Git commands to get you started:

- **`git init`**: Initialize a new Git repository.
- **`git clone [repository_url]`**: Clone a remote repository to your local machine.
- **`git add [file]`**: Add changes in a file to the staging area.
- **`git commit -m "Commit message"`**: Commit the staged changes with a descriptive message.
- **`git status`**: View the status of your repository and staged changes.
- **`git push`**: Push your committed changes to a remote repository.
- **`git pull`**: Pull changes from a remote repository to update your local repository.
- **`git branch`**: List branches in the repository.
- **`git checkout [branch_name]`**: Switch to a different branch.

Remember to consult the [GitHub Git Cheat Sheet](https://github.github.com/training-kit/downloads/github-git-cheat-sheet.pdf) for additional commands and best practices.

**With this simple guide, you should now be well-equipped to start coding, version-controlling, and collaborating on your projects using WSL, Node.js, VS Code, and Git. Happy coding!**

### This work is licensed under the MIT License - see the [MIT License](https://mit-license.org/) for details.
