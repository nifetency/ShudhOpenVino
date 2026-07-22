# ShudhOpenVino Example

A **Python-based OpenVINO** application published as a **sample deployment project for [Nife.io](https://nife.io)**.

This repository demonstrates how to run a lightweight OpenVINO inference application locally and deploy it on [Nife.io](https://nife.io). It is intended as a practical sample for testing AI inference deployment workflows and showcasing a straightforward OpenVINO deployment path.

## Overview

This project is a basic OpenVINO application with a standard project structure, optimized inference logic, and support for multiple model types including face detection and object detection. It is designed to be small enough for learning and deployment experiments while still reflecting the conventions of a real OpenVINO application.[3]

If you want a simple AI inference sample to test deployment on [Nife.io](https://nife.io), this repository is a good starting point.

## Features

| Feature | Description |
| --- | --- |
| OpenVINO inference | Optimized Intel OpenVINO model inference |
| Face detection | Face detection and recognition capabilities |
| Object detection | Object detection module for image analysis |
| Python server | Flask-based API server for inference requests |
| Modular architecture | Separate modules for different detection tasks |
| Deployment-ready setup | Can be deployed using Git-based workflows |
| Nife.io sample use case | Suitable as a reference project for [Nife.io](https://nife.io) deployments |

## Tech Stack

| Technology | Purpose |
| --- | --- |
| Python | Runtime environment |
| OpenVINO | Intel optimized inference engine |
| Flask | Web framework for API server |
| Docker | Container packaging |
| Nife.io | Deployment platform |

## Prerequisites

Before running the project locally, make sure the following are installed.

| Requirement | Notes |
| --- | --- |
| Python | Version 3.7+ recommended |
| pip | Python package manager |
| OpenVINO | Intel OpenVINO Toolkit |
| Git | Required to clone the repository |

## Getting Started

### Clone the repository

```bash
git clone https://github.com/nifetency/shudh-openvino.git
cd ShudhOpenVino
```

### Create a virtual environment (recommended)

```bash
python -m venv venv
```

**Activate the virtual environment:**

- **On Windows:**
  ```bash
  venv\Scripts\activate
  ```

- **On macOS/Linux:**
  ```bash
  source venv/bin/activate
  ```

### Install dependencies

```bash
pip install -r requirements.txt
```

### Start the application

```bash
python server.py
```

Then open the application at `http://localhost:9099`.

## Deploy on Nife.io

You can deploy this application on [Nife.io](https://nife.io) using either the Git repository or the CLI.[1] [2]

### Option 1: Deploy from a Docker image

First, build and push the image to your preferred container registry.

```bash
docker build -t shudhopenvino .
docker tag shudhopenvino <username>/shudhopenvino:latest
docker push <username>/shudhopenvino:latest
```

Then configure a new application in Nife.io with the following settings.

| Setting | Value |
| --- | --- |
| Source | Docker Image |
| Registry | Docker Hub or another supported registry |
| Image | `<username>/shudhopenvino:latest` |
| Internal Port | `9099` |
| External Port | `9099` |
| Suggested Replicas | `1` |

### Option 2: Deploy from the Git repository

Deploy the project directly from GitHub.

| Setting | Value |
| --- | --- |
| Source | Git Repository |
| Provider | GitHub |
| Branch | `main` |
| Internal Port | `9099` |
| External Port | `9099` |
| Build Mode | Auto-Dockerize with runtime |

### Option 3: Deploy with `nifectl`

If you prefer the command line, use the following workflow.

```bash
nifectl auth login
nifectl init
nifectl deploy
```

For step-by-step instructions, see the [Nife.io Quick Deploy documentation](https://docs.nife.io/overview/quick-deploy) and the [nifectl quick start guide](https://docs.nife.io/Quick-Start/Nifectl).

## Environment Variables

The following variables are commonly relevant for deployment.

| Variable | Description | Example |
| --- | --- | --- |
| `PYTHON_ENV` | Python execution environment | `production` |
| `PORT` | Application port | `9099` |

## Repository Structure

| Path | Purpose |
| --- | --- |
| `server.py` | Main Flask API server |
| `common.py` | Common utility functions |
| `Face/` | Face detection and recognition module |
| `Objects/` | Object detection module |
| `venv/` | Python virtual environment |
| `requirements.txt` | Python dependencies |
| `dockerfile` | Container build instructions |

## Troubleshooting

| Issue | Suggested fix |
| --- | --- |
| Python not installed | Install Python and verify with `python --version` |
| Dependencies missing | Run `pip install -r requirements.txt` |
| OpenVINO not installed | Install OpenVINO Toolkit and verify installation |
| Flask import error | Reinstall Flask with `pip install flask` |
| Virtual environment issues | Delete venv folder and recreate with `python -m venv venv` |
| Port `9099` already in use | Stop the conflicting process or change the port |
| Model inference fails | Verify model files and OpenVINO paths |
| Deployment fails on Nife.io | Verify ports, environment variables, and build settings |
| Application is unreachable | Check routing, service exposure, and deployment logs |

## Acknowledgements

This repository is maintained by **Nifetency** as a sample deployment project for [Nife.io](https://nife.io).

If this repository is derived from an earlier template or upstream example, it is good practice to retain visible credit to the original author or source repository.

## License

This project is licensed under the **MIT License**.

## References

1. [Nife.io](https://nife.io)
2. [Nife Docs Overview](https://docs.nife.io/overview/)
3. [Original Repository](https://github.com/nife-public/ShudhOpenVino.git)
4. [Nife Quick Start](https://docs.nife.io/Quick-Start)