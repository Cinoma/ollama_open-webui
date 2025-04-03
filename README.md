# Ollama Docker Setup with Open WebUI

This repository contains Docker configuration for running Ollama with Open WebUI, providing a user-friendly interface for interacting with various AI models.

## Prerequisites

- Docker and Docker Compose installed on your system
- NVIDIA GPU with updated NVIDIA drivers
- NVIDIA Container Toolkit installed ([Installation Guide](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html))

## Installation & Setup

1. Clone this repository
2. Start the Docker containers:

```bash
docker compose up -d
```

This will:

- Start Ollama server with GPU support
- Launch Open WebUI interface
- Create persistent volumes for both services

## Accessing the Interface

Once the containers are running, you can access the Open WebUI interface at: <http://localhost:3000>

## Pulling Models

### Deepseek Model

To pull the Deepseek model, use either:

1. Via CLI:

```bash
docker exec -it ollama ollama pull deepseek-coder
```

2. Via Open WebUI:
   - Navigate to <http://localhost:3000>
   - Click on "Models" in the sidebar
   - Search for "deepseek-coder"
   - Click "Pull" button

### Qwen Model

To pull the Qwen model, use either:

1. Via CLI:

```bash
docker exec -it ollama ollama pull qwen2.5
```

2. Via Open WebUI:
   - Navigate to <http://localhost:3000>
   - Click on "Models" in the sidebar
   - Search for "qwen"
   - Select version 2.5
   - Click "Pull" button

## System Requirements

- Minimum 8GB RAM (allocated to Docker)
- 4 CPU cores
- NVIDIA GPU with at least 8GB VRAM
- Sufficient storage space for models:
  - Deepseek-coder: ~4GB
  - Qwen 2.5: ~4GB

## Troubleshooting

If you encounter issues:

1. Check Docker logs:

```bash
docker compose logs -f
```

2. Ensure NVIDIA drivers are properly installed:

```bash
nvidia-smi
```

3. Verify GPU access in container:

```bash
docker exec -it ollama nvidia-smi
```

## Security Notes

The setup includes several security measures:

- Container memory limited to 8GB
- CPU usage limited to 4 cores
- Read-only filesystem
- Dropped capabilities and no privilege escalation
- Automatic restart on failure
