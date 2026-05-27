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
RUN az bicep install

# Install PowerShell modules
RUN pwsh -Command "Install-Module -Name Az -Force -Scope AllUsers -AllowClobber" && \
    pwsh -Command "Install-Module -Name Microsoft.Graph -Force -Scope AllUsers"