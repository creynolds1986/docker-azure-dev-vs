# Azure & PowerShell Development Container

A comprehensive development container for Azure infrastructure and PowerShell development with VS Code. This container is configured as a Dev Container and provides a complete, pre-configured environment for building, managing, and deploying Azure resources.

## Overview

This Docker container is built on Ubuntu and includes all essential tools and extensions needed for Azure development, Infrastructure as Code (IaC), and PowerShell scripting. It's designed to work seamlessly with VS Code's Dev Containers extension to provide a consistent development environment.

## What's Included

### Runtime & Shell
- **PowerShell** - Full PowerShell runtime for scripting and automation
- **Ubuntu Base Image** - Latest Ubuntu-based dev container foundation

### Azure Tools
- **Azure CLI** - Command-line interface for managing Azure resources
- **Bicep CLI** - Domain-specific language for defining Azure infrastructure

### PowerShell Modules
- **Azure PowerShell (Az module)** - Complete PowerShell SDK for Azure resource management
- **Microsoft Graph PowerShell** - PowerShell SDK for interacting with Microsoft Graph API

### VS Code Extensions
- **PowerShell** - IntelliSense, debugging, and syntax highlighting for PowerShell scripts
- **Bicep** - Language support and validation for Bicep IaC templates
- **Azure Resource Groups** - Browse and manage Azure resources from VS Code
- **GitHub Copilot** - AI-powered code completion and assistance
- **GitHub Copilot Chat** - Interactive chat for coding help

### Configuration
- **PowerShell Profile** - Pre-configured with Windows-style tab completion for a familiar experience
- **Terminal Integration** - VS Code terminal defaults to PowerShell with shell integration enabled

## Quick Start

### Prerequisites
- Docker
- VS Code
- VS Code Dev Containers extension

### Getting Started

1. **Clone the repository:**
   ```bash
   git clone https://github.com/yourusername/docker-azure-dev-vs.git
   cd docker-azure-dev-vs
   ```

2. **Open in Dev Container:**
   - Open the folder in VS Code
   - Click the remote indicator in the bottom-left corner
   - Select "Reopen in Container"
   - Wait for the container to build and start

3. **Verify Installation:**
   ```powershell
   az version
   bicep --version
   pwsh --version
   Get-Module Az -ListAvailable
   ```

## Usage Examples

### Azure CLI Commands
```bash
# Login to Azure
az login

# List resource groups
az group list --output table

# Create a resource group
az group create --name myResourceGroup --location eastus
```

### PowerShell Azure Management
```powershell
# Connect to Azure
Connect-AzAccount

# Get all storage accounts
Get-AzStorageAccount

# Create a resource group
New-AzResourceGroup -Name myResourceGroup -Location EastUS
```

### Bicep Deployment
```bash
# Build Bicep template to ARM JSON
bicep build main.bicep

# Deploy infrastructure
az deployment group create \
  --resource-group myResourceGroup \
  --template-file main.bicep
```

### PowerShell Scripting
```powershell
# Run a PowerShell script
./deploy.ps1

# Interactively manage Azure resources
$vms = Get-AzVM
$vms | ForEach-Object { Write-Host $_.Name }
```

## Project Structure

```
docker-azure-dev-vs/
├── .devcontainer/
│   ├── Dockerfile          # Container configuration
│   └── devcontainer.json   # VS Code Dev Container settings
└── README.md               # This file
```

## Customization

### Adding More PowerShell Modules
Edit the Dockerfile and add additional modules:
```dockerfile
RUN pwsh -Command "Install-Module -Name ModuleName -Force -Scope AllUsers"
```

### Installing Additional Tools
Extend the Dockerfile to include additional tools:
```dockerfile
RUN apt-get update && apt-get install -y <tool-name>
```

### Modifying VS Code Extensions
Edit `.devcontainer/devcontainer.json` to add or remove extensions in the `customizations.vscode.extensions` array.

## Environment Details

- **Base Image:** Ubuntu (latest from Microsoft's Dev Containers)
- **Remote User:** vscode
- **Default Shell:** PowerShell (pwsh)
- **Platform:** Linux (x64)

## Troubleshooting

### Container won't build
- Ensure Docker daemon is running
- Check internet connectivity for package downloads
- Review Docker logs for detailed error messages

### PowerShell commands not found
- Verify PowerShell is installed: `which pwsh`
- Check PowerShell profile: `cat ~/.config/powershell/Microsoft.PowerShell_profile.ps1`

### Azure CLI authentication issues
- Ensure you've logged in: `az login`
- Check account subscription: `az account list`

## Support & Documentation

- [Azure CLI Documentation](https://learn.microsoft.com/en-us/cli/azure/)
- [PowerShell Documentation](https://learn.microsoft.com/en-us/powershell/)
- [Bicep Documentation](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/overview)
- [VS Code Dev Containers](https://code.visualstudio.com/docs/devcontainers/containers)

## License

[Specify your license here]

## Contributing

[Add contribution guidelines if applicable]
