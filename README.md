# Azure & PowerShell Development Container

A development container for Azure infrastructure and PowerShell development with VS Code.

## Prerequisites

- Docker
- VS Code
- VS Code Dev Containers extension

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/creynolds1986/docker-azure-dev-vs.git
   cd docker-azure-dev-vs
   ```

2. Open in VS Code:
   ```bash
   code .
   ```

3. Reopen in container:
   - Click the remote indicator (bottom-left corner)
   - Select "Reopen in Container"
   - Wait for the container to build

## What's Included

### Runtime & Shell
- PowerShell
- Ubuntu base image

### Azure Tools
- Azure CLI
- Bicep CLI

### PowerShell Modules
- Azure PowerShell (Az module)
- Microsoft Graph PowerShell

### VS Code Extensions
- PowerShell
- Bicep
- Azure Resource Groups
- GitHub Copilot
- GitHub Copilot Chat
