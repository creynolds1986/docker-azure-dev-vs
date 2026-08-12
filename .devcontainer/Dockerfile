FROM mcr.microsoft.com/devcontainers/base:ubuntu

# Install PowerShell
RUN apt-get update && apt-get install -y wget apt-transport-https software-properties-common && \
    wget -q "https://packages.microsoft.com/config/ubuntu/22.04/packages-microsoft-prod.deb" && \
    dpkg -i packages-microsoft-prod.deb && \
    apt-get update && apt-get install -y powershell && \
    rm packages-microsoft-prod.deb

# Install Azure CLI
RUN curl -sL https://aka.ms/InstallAzureCLIDeb | bash

# Install Bicep CLI
RUN curl -Lo /usr/local/bin/bicep https://github.com/Azure/bicep/releases/latest/download/bicep-linux-x64 && \
    chmod +x /usr/local/bin/bicep

# Install PowerShell modules
RUN pwsh -Command "Install-Module -Name Az -Force -Scope AllUsers -AllowClobber" && \
    pwsh -Command "Install-Module -Name Microsoft.Graph -Force -Scope AllUsers"

# Configure PowerShell profile for Windows-style tab completion
RUN mkdir -p /home/vscode/.config/powershell && \
    echo 'Set-PSReadLineKeyHandler -Key Tab -Function Complete' >> /home/vscode/.config/powershell/Microsoft.PowerShell_profile.ps1

# Install Terraform CLI
RUN apt-get update && apt-get install -y gnupg lsb-release curl && \
    curl -fsSL https://apt.releases.hashicorp.com/gpg | gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg && \
    echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | tee /etc/apt/sources.list.d/hashicorp.list && \
    apt-get update && apt-get install -y terraform && \
    rm -rf /var/lib/apt/lists/*