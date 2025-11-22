# AGENTS.MD

This file provides essential information for AI agents working on the **Open Notebook** repository.

## 1. Context & Purpose
**Open Notebook** is an open-source, privacy-first alternative to Google's Notebook LM. It allows users to ingest multi-modal content (PDF, Audio, Video, Web), chat with it using various LLMs, generate podcasts, and manage notes.

## 2. Tech Stack
*   **Language:** Python 3.11+ (Backend), TypeScript/JavaScript (Frontend).
*   **Backend Framework:** FastAPI (`api/`).
*   **Frontend Framework:** Next.js 15 + React 19 (`frontend/`).
*   **Database:** SurrealDB.
*   **Package Managers:** `uv` (Python), `npm` (Node.js).
*   **AI/LLM Orchestration:** LangChain, Esperanto.
*   **Containerization:** Docker.

## 3. Project Structure
*   `api/`: FastAPI backend application code.
    *   `routers/`: API endpoints organized by feature.
    *   `main.py`: Entry point.
*   `frontend/`: Next.js application.
*   `open_notebook/`: Core business logic and library code.
*   `commands/`: Background worker commands (Surreal Commands).
*   `tests/`: Python tests.
*   `docs/`: Documentation files.

## 4. Development Environment & Commands
This project uses a `Makefile` to manage common tasks.

### Running Services
*   `make start-all`: Starts Database (Docker), API, Worker, and Frontend.
*   `make database`: Starts only the SurrealDB container.
*   `make api`: Runs the FastAPI backend (`run_api.py`).
*   `make worker`: Runs the background worker.
*   `make frontend`: Runs the Next.js dev server.

### Quality Assurance (QA)
*   **Linting (Python):** `make ruff` (Auto-fixes linting errors).
*   **Type Checking (Python):** `make lint` (Runs `mypy`).
*   **Testing:** `uv run pytest`.

### Dependencies
*   **Python:** Managed by `uv`. Run `uv sync` to install.
*   **Frontend:** Managed by `npm`. Run `cd frontend && npm install`.

## 5. Coding Conventions & Guidelines
*   **Python:** Follow PEP 8. Use type hints strongly. Docstrings are required for functions/classes.
*   **Frontend:** Use functional React components with Hooks. Use TypeScript interfaces.
*   **Architecture:**
    *   The frontend is a Next.js app proxying `/api` requests to the backend.
    *   Background tasks (e.g., podcast generation) are handled by the `worker` via SurrealDB command queue.
*   **Verification:** Always run `make ruff` and `make lint` before submitting Python changes.

## 6. Key Configuration Files
*   `pyproject.toml`: Python dependencies and tool configs.
*   `frontend/package.json`: Frontend dependencies.
*   `docker-compose.*.yml`: Docker configurations for different environments.
*   `.env`: Environment variables (see `.env.example`).

## 7. Documentation
*   Refer to `docs/` for detailed feature explanations.
*   Refer to `api/routers` for endpoint definitions.
