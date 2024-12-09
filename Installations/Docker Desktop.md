
---

# Installing Docker Desktop on Windows

## Step-by-Step Guide

### 1. Download Docker Desktop

1. **Visit the Docker Website**:
    
- Go to the official Docker website.
    - https://www.docker.com/products/docker-desktop/
2. **Download the Installer**:
    
    - Click the **Download for Windows** button to download the Docker Desktop installer.

### 2. Run the Installer

1. **Locate the Installer**:
    
    - Find the downloaded installer file (usually in your Downloads folder).
2. **Run the Installer**:
    
    - Double-click the `Docker Desktop Installer.exe` file to start the installation process.
3. **Follow the Setup Instructions**:
    
    - Follow the on-screen prompts to proceed with the installation.
    - Accept the license agreement and click **Install**.

### 3. Enable WSL 2 Integration

1. **Enable WSL 2**:
    
    - During the installation, Docker Desktop will prompt you to enable WSL 2. Follow the instructions to download and install the Linux kernel update package if it's not already installed.
2. **Set WSL 2 as the Default**:
    
    - Open PowerShell as Administrator and run the following command to set WSL 2 as the default version: `sh wsl --set-default-version 2`

### 4. Complete the Installation

1. **Finish the Setup**:
    
    - Once the installation is complete, launch Docker Desktop from the Start menu.
2. **Initial Setup**:
    
    - The first time you run Docker Desktop, it might take a few minutes to initialize. Follow any additional setup instructions provided by the application.

### 5. Configure Docker Desktop to Use WSL 2

1. **Open Docker Desktop Settings**:
    
    - Click on the Docker icon in the system tray and select **Settings**.
2. **Enable WSL 2 Based Engine**:
    
    - Go to the **General** tab and ensure that **Use the WSL 2 based engine** is checked.
3. **Integrate with Your Linux Distribution**:
    
    - Navigate to the **Resources** tab, then **WSL Integration**.
    - Enable integration with your installed Linux distribution(s) by toggling the switch next to the distribution name.
4. **Apply and Restart**:
    
    - Click **Apply & Restart** to apply the changes.

### 6. Verify the Installation

1. **Open Your Linux Distribution**:
    
    - Open the installed Linux distribution from the Start menu.
2. **Run Docker Commands**:
    
    - Verify that Docker is running by executing a simple Docker command: `sh docker --version`
    - You should see the Docker version information, indicating that Docker is correctly set up with WSL 2.
