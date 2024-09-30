# FauxPilot

This is an attempt to build a locally hosted alternative to [GitHub Copilot](https://copilot.github.com/). It uses the [SalesForce CodeGen](https://github.com/salesforce/CodeGen) models inside of NVIDIA's [Triton Inference Server](https://developer.nvidia.com/nvidia-triton-inference-server) with the [FasterTransformer backend](https://github.com/triton-inference-server/fastertransformer_backend/).

<p align="right">
  <img width="50%" align="right" src="./img/fauxpilot.png">
</p>

## Table of Contents

1. [Introduction](#introduction)
2. [Prerequisites](#prerequisites)
3. [Installation and Setup](#installation-and-setup)
   - [Setting up a FauxPilot Server](#setting-up-a-fauxpilot-server)
   - [Client Configuration for FauxPilot](#client-configuration-for-fauxpilot)
4. [Usage](#usage)
5. [Contributing](#contributing)
6. [Support and Warranty](#support-and-warranty)
7. [Terminology](#terminology)

## Introduction

FauxPilot allows developers to enjoy AI-driven code completion similar to GitHub Copilot, but hosted locally. This solution is ideal for developers and organizations seeking privacy in their offline work enviornments while also getting the assistance of advanced machine learning models that help streamline the coding process.

## Prerequisites

You'll need the following to run FauxPilot:

* Docker
* `docker compose` version >= 1.28
* An NVIDIA GPU with Compute Capability >= 6.0 and enough VRAM to run the model you want.
* [`nvidia-docker`](https://github.com/NVIDIA/nvidia-docker) for running Docker containers with GPU support.
* `curl` and `zstd` for downloading and unpacking the models.

**Note**: The VRAM requirements listed by `setup.sh` are cumulative. If you have multiple GPUs, you can distribute the model across them. For example, two NVIDIA RTX 3080 GPUs should be able to run the 6B model by splitting it across the GPUs.

## Installation and Setup

This section describes the steps to set up a FauxPilot server and configure clients to interact with the server.

### Setting up a FauxPilot Server

1. Run the `setup.sh` script to select a model. The script will download the chosen model from [Huggingface/Moyix](https://huggingface.co/Moyix) in GPT-J format.
2. The model will then be converted for use with the FasterTransformer backend.

For more detailed instructions, please refer to [How to set-up a FauxPilot server](documentation/server.md).

### Client Configuration for FauxPilot

FauxPilot supports various ways to connect to the server, including:
- OpenAI API
- Copilot Plugin
- REST API

Please refer to [How to set-up a client](documentation/client.md) for client configuration details.

## Usage

Once the FauxPilot server is set up, you can integrate it with your local offline development environment similarly to Github Copilot, but fully secure.

## Contributing

We welcome contributions! If you’d like to contribute to FauxPilot, please follow these steps:

1. **Fork the repository**: Click the "Fork" button on the top right of this page to create a copy of this github repository on your account.
2. **Clone the repository**: Clone the forked repository to your local machine using:
   ```bash
   git clone https://github.com/YOUR-USERNAME/fauxpilot.git
3. **Create a new branch**:
   ```bash
   git checkout -b your-branch-name
4. **Set up locally**: Ensure you have docker installed and then build the server:
   ```bash
   docker-compose up --build
5. **Make your changes**: Update the code or documentation.
6. **Commit your changes and push**: Commit your changes to the repo and push using these commands.
   ```bash
   git add .
   git commit -m "Brief description of changes"
   git push origin your-branch-name
7. **Submit a pull request**: Go to your GitHub fork and open a PR.

## Support and Warranty

While FauxPilot is actively maintained, we do not offer formal support or warranties. However, you can find some helpful information in the following resources:

- [Wiki](https://github.com/moyix/fauxpilot/wiki)
- [Discussion Forum](https://github.com/moyix/fauxpilot/discussions)

Feel free to ask questions in the discussion forum.

## Terminology

- **API**: Application Programming Interface
- **CC**: Compute Capability
- **CUDA**: Compute Unified Device Architecture
- **FT**: FasterTransformer
- **JSON**: JavaScript Object Notation
- **gRPC**: Google Remote Procedure Call
- **GPT-J**: A transformer model trained using Ben Wang’s Mesh Transformer JAX
- **REST**: Representational State Transfer

