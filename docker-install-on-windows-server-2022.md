### Step 1: Enable Required Features

Docker relies on several features that need to be enabled on your system:

1. **Open PowerShell as Administrator** and run the following commands to enable necessary features:
   ```powershell
   Install-WindowsFeature -Name Containers, Hyper-V
   ```
   - This command enables both the Containers and Hyper-V features, which are required for Docker.

2. **Reboot** the server after enabling the features:
   ```powershell
   Restart-Computer
   ```

### Step 2: Install Docker

1. **Download the DockerMsftProvider module** to install Docker on Windows Server:
   ```powershell
   Install-Module -Name DockerMsftProvider -Repository PSGallery -Force
   ```

2. **Install Docker**:
   ```powershell
   Install-Package -Name docker -ProviderName DockerMsftProvider
   ```

3. After installation, **restart** the system again:
   ```powershell
   Restart-Computer
   ```

4. **Verify Docker is installed** by checking the version:
   ```powershell
   docker version
   ```

### Step 3: Configure Docker to Use WSL 2 (Optional)

If you want to use **WSL 2** as your Docker backend, make sure you have it enabled:

1. Install WSL if it's not already installed:
   ```powershell
   wsl --install
   ```

2. Set WSL 2 as the default version:
   ```powershell
   wsl --set-default-version 2
   ```

3. In the Docker settings (Docker Desktop), set the option to use WSL 2 as the backend.

### Step 4: Install Docker Desktop (Optional)

**Docker Desktop** provides a user-friendly GUI and is typically used for development environments. However, it is less common on Windows Server since it's designed for workstation environments. If you still wish to install it, here's how:

1. **Download Docker Desktop** from the official Docker website: [Docker Desktop Download](https://www.docker.com/products/docker-desktop).
   
2. Run the **Docker Desktop Installer** and follow the setup wizard.

3. **Enable WSL 2 integration** during installation if you plan to use WSL 2 as the backend.

4. **Start Docker Desktop** and configure it based on your preferences.

### Step 5: Verify the Installation

After installation, you can verify that Docker is running properly:

1. Open PowerShell and run:
   ```powershell
   docker run hello-world
   ```

   This will download a test image and run it to confirm the Docker installation is working.

### Step 6: Post-Installation Configuration (Optional)

- **Manage Docker as a Non-Administrator**: By default, Docker requires administrative privileges. To use Docker without needing admin rights, follow Docker's documentation for setting up non-admin access.
  
- **Networking**: Ensure your firewall settings allow Docker traffic if you plan to expose containers to the network.

### Conclusion

You should now have Docker and optionally Docker Desktop running on your Windows Server 2022 system, with or without WSL 2 integration depending on your setup.