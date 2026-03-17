# Architecture

This document explains the overall structure of the repository and the independent responsibilities of the chatbot, image generation, and video generation systems.

## Design Goals

- Keep each subsystem isolated so it can run independently.
- Enable local-first, offline-friendly deployment.
- Allow components to be split across machines if needed.
- Keep integration points explicit and minimal.

## Systems

### 1) Chatbot subsystem

The chatbot subsystem is currently defined in [`chatbot/docker-compose.yml`](../chatbot/docker-compose.yml) and includes:

- **Ollama**: local model serving endpoint.
- **Open WebUI**: browser-based chat interface connected to Ollama.

### 2) Image generation subsystem

Planned as a separate service stack for text-to-image and image-to-image workflows.

Expected characteristics:

- Independent runtime and dependencies.
- Optional GPU acceleration.
- Local model storage and inference.

### 3) Video generation subsystem

Planned as a separate service stack for image + prompt to video workflows.

Expected characteristics:

- Isolated execution environment due to higher compute requirements.
- Optional queueing/job orchestration for long-running generations.
- Storage and artifact management kept independent from chatbot services.

## Deployment model

Each subsystem should be deployable in one of these patterns:

- **Single host**: all services on one machine.
- **Split host**: each subsystem on dedicated hardware.
- **Hybrid local network**: selected services exposed internally over LAN.

## Data boundaries

- Service-specific model and cache volumes should remain scoped to each subsystem.
- Shared data exchange should happen through explicit APIs, mounted directories, or message queues.
- No subsystem should require direct coupling to another subsystem's internal files.

## Current status

- Chatbot: available.
- Image generation: scaffold planned.
- Video generation: scaffold planned.
