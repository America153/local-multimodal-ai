# Local Multimodal AI

A **modular, fully local AI template** for running independent systems:

- **Chatbot** (text + image understanding)
- **Image generation** (photo + prompt)
- **Video generation** (image + prompt)

This repository is designed for **offline / local use**, with clear separation of subsystems. Each system can run independently or on separate hardware.

---

## Repository Structure

```text
.
├── chatbot/
│   └── docker-compose.yml
├── docs/
│   └── architecture.md
├── LICENSE
└── README.md
```

---

## Quick Start (Chatbot)

From the repository root:

```bash
cd chatbot
docker compose up -d
```

Services exposed by default:

- **Ollama API**: `http://localhost:11434`
- **Open WebUI**: `http://localhost:3000`

---

## Documentation

- Architecture overview: [`docs/architecture.md`](docs/architecture.md)

---

## License

See [`LICENSE`](LICENSE).
