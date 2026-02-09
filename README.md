# docker-esphome
ESPHome project devenv

## VS Code Dev Container Setup

This repository includes a VS Code Dev Container configuration that provides a complete development environment for ESPHome projects.

### Prerequisites

- [Visual Studio Code](https://code.visualstudio.com/)
- [Docker](https://www.docker.com/products/docker-desktop)
- [Remote - Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

### Getting Started

1. Clone this repository
2. Open the repository folder in VS Code
3. When prompted, click "Reopen in Container" (or use the command palette: `Remote-Containers: Reopen in Container`)
4. Wait for the container to build (first time may take a few minutes)
5. Once the container is ready, you can start using ESPHome commands

### Included Dependencies

The dev container includes:

- **Python 3.11** - Base Python environment
- **ESPHome** - Latest version of ESPHome CLI (automatically installed from PyPI)
- **PlatformIO Core** - For building and uploading firmware (automatically installed from PyPI)
- **Build tools** - gcc, g++, cmake, ninja-build, and other essential build tools
- **Development tools** - pylint, black, pytest for Python development

### Verify Installation

Once the container is running, you can verify the installation by running:

```bash
esphome version
```

### Working with ESPHome

You can now create and build ESPHome configurations:

```bash
# Create a new ESPHome configuration
esphome wizard my-device.yaml

# Compile the configuration
esphome compile my-device.yaml

# Upload to device (make sure the device is connected)
esphome upload my-device.yaml
```

### VS Code Extensions

The following VS Code extensions are automatically installed in the container:

- **Python** - Python language support
- **Pylance** - Fast Python language server
- **ESPHome** - ESPHome YAML configuration support
