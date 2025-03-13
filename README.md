# Azure DevOps Microagent for OpenHands

This project is a microagent developed for [OpenHands](https://github.com/All-Hands-AI/OpenHands), a platform for AI-powered software development agents.

## 📝 Description

The Azure DevOps Microagent is a specialized extension that enables seamless integration between OpenHands and Azure DevOps. This agent facilitates operations such as:

- Cloning repositories from Azure DevOps
- Simplified authentication using Personal Access Tokens (PAT)
- Automatic configuration of Azure DevOps CLI environment
- Repository navigation and management

## 🚀 Features

- Azure DevOps CLI integration
- Environment variables management for authentication
- Repository operations support
- Automated development environment setup

## ⚙️ Configuration

The agent uses the following environment variables:

```bash
AZURE_DEVOPS_ORG - Azure DevOps organization URL
AZURE_DEVOPS_PAT - Personal Access Token for authentication
AZURE_DEVOPS_PROJECT - Azure DevOps project name
```

## 📦 Installation

1. Run OpenHands with Azure DevOps configuration:
```bash
docker run -it --rm --pull=always \
    -e SANDBOX_RUNTIME_CONTAINER_IMAGE=docker.all-hands.dev/all-hands-ai/runtime:0.28-nikolaik \
    -e LOG_ALL_EVENTS=true \
    -e "SANDBOX_RUNTIME_STARTUP_ENV_VARS={ 'AZURE_DEVOPS_PROJECT':'project', 'AZURE_DEVOPS_ORG': 'org', 'AZURE_DEVOPS_PAT': 'PAT'}" \
    -v /var/run/docker.sock:/var/run/docker.sock \
    -v ~/.openhands-state:/.openhands-state \
    -v $PWD/microagents:/app/microagents \
    -p 3000:3000 \
    --add-host host.docker.internal:host-gateway \
    --name openhands-app \
    docker.all-hands.dev/all-hands-ai/openhands:0.28
```

3. Configure environment variables and authenticate with Azure DevOps

## 🤝 Contributing

Contributions are welcome! Please read the OpenHands project contribution guidelines before submitting your changes.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---
Developed as part of the [OpenHands](https://github.com/All-Hands-AI/OpenHands) ecosystem 