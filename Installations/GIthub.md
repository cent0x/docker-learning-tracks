
---

# Installing Git on Windows

## Step-by-Step Guide

### 1. Download Git

1. **Visit the Git Website**:
    
    - Go to the official Git website.
2. **Download the Installer**:
    
    - Click the **Download for Windows** button to download the Git installer.

### 2. Run the Installer

1. **Locate the Installer**:
    
    - Find the downloaded installer file (usually in your Downloads folder).
2. **Run the Installer**:
    
    - Double-click the `Git-2.x.x-64-bit.exe` file to start the installation process.
3. **Follow the Setup Instructions**:
    
    - Follow the on-screen prompts to proceed with the installation.
    - Accept the license agreement and click **Next**.
4. **Select Installation Location**:
    
    - Choose the destination folder for the installation and click **Next**.
5. **Select Components**:
    
    - Choose the components you want to install, such as additional icons or third-party software. The default options are usually sufficient. Click **Next**.
6. **Choose the Default Editor Used by Git**:
    
    - Select your preferred text editor for Git. If you're unsure, you can stick with the default option (Vim). Click **Next**.
7. **Adjust Your PATH Environment**:
    
    - Choose the option to use Git from the command line and also from third-party software. This is the recommended option. Click **Next**.
8. **Choose HTTPS Transport Backend**:
    
    - Select the option to use the OpenSSL library. Click **Next**.
9. **Configure the Line Ending Conversions**:
    
    - Choose the option to check out Windows-style, commit Unix-style line endings. Click **Next**.
10. **Configure the Terminal Emulator**:
    
    - Select the option to use MinTTY (the default terminal emulator for Git Bash). Click **Next**.
11. **Choose the Default Behavior of `git pull`**:
    
    - Select the default option (simple mode). Click **Next**.
12. **Choose Credential Helper**:
    
    - Select the Git Credential Manager Core. Click **Next**.
13. **Configure Extra Options**:
    
    - Enable file system caching and Git Credential Manager. Click **Next**.
14. **Configure Experimental Options**:
    
    - You can leave these options unchecked unless you have specific needs. Click **Install**.

### 3. Complete the Installation

1. **Finish the Setup**:
    - Once the installation is complete, click **Finish** to exit the setup wizard.

### 4. Verify the Installation

1. **Open Git Bash**:
    
    - Open Git Bash from the Start menu or by searching for it.
2. **Check the Version**:
    
    - Type the following command to check the Git version: `sh git --version`
    - You should see the version information, indicating that Git is correctly installed.


## If you're having trouble running Git commands inside the VSCode terminal

### 1. Git is Not Installed or Not in PATH

**Issue**: VSCode can't find Git because it's not installed or not added to the system PATH.

**Solution**:

- **Install Git**: Make sure Git is installed on your system. You can download it from the official Git website.
- **Add Git to PATH**: During the Git installation, ensure you select the option to add Git to your system PATH. If Git is already installed, you can manually add it to the PATH:
    1. Open **System Properties** > **Advanced** > **Environment Variables**.
    2. Find the `Path` variable in the **System variables** section and click **Edit**.
    3. Add the path to your Git `bin` and `cmd` directories (e.g., `C:\Program Files\Git\bin` and `C:\Program Files\Git\cmd`).

### 2. Configure Git Path in VSCode

**Issue**: VSCode is not configured to use the correct Git executable path.

**Solution**:

- Open VSCode and go to **File** > **Preferences** > **Settings**.
- Search for `git.path` and set it to the path of your Git executable. For example:

```json
  "git.path": "C:\\Program Files\\Git\\bin\\git.exe"
```

### 3. Use Git Bash as the Default Terminal

**Issue**: The default terminal in VSCode is not set to Git Bash, which might be more compatible with Git commands.

**Solution**:

- Open VSCode and go to **File** > **Preferences** > **Settings**.
- Search for `terminal.integrated.defaultProfile.windows`.
- Set it to `Git Bash`. If it's not listed, you can add it manually by editing your `settings.json`:

```json
  "terminal.integrated.profiles.windows": {
    "Git Bash": {
      "source": "Git Bash"
    }
  },
  "terminal.integrated.defaultProfile.windows": "Git Bash"
```

### 4. Restart VSCode

**Issue**: Changes to settings or PATH are not recognized until VSCode is restarted.

**Solution**:

- After making changes to your system PATH or VSCode settings, restart VSCode to ensure the changes take effect.