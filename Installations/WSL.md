
---

# Installing WSL (Windows Subsystem for Linux)

## Step-by-Step Guide

### 1. Enable the WSL Feature

1. **Open PowerShell as Administrator**:
    
    - Right-click on the Start button and select **Windows PowerShell (Admin)**.
2. **Run the following command to enable WSL**:
    

```sh
   wsl --install
```

This command will enable the required features and install the default Linux distribution.

### 2. Restart Your Computer

- After running the command, you may be prompted to restart your computer. Make sure to save your work and restart.

### 3. Set Up Your Linux Distribution

1. **Launch the Linux distribution**:
    
    - After the restart, open the Start menu and search for your installed Linux distribution (e.g., Ubuntu).
```sh
   wsl
```
2. **Complete the initial setup**:
    
    - Follow the on-screen instructions to complete the setup, which includes creating a user account and setting a password.

### 4. Verify the Installation

1. **Open your Linux distribution**:
    
    - Open the installed Linux distribution from the Start menu.
2. **Check the WSL version**:
    
    - Run the following command to check the WSL version: `sh wsl --list --verbose`
    - Ensure that your distribution is running WSL 2. If not, you can set it to use WSL 2 with: `sh wsl --set-version <distribution-name> 2`

### Additional Resources

For more detailed instructions and troubleshooting, visit the Microsoft documentation.

---

Feel free to let me know if you need any more details or assistance with the installation process!