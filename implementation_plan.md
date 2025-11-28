# Dog Training App - Implementation Plan

## Goal
Build a turnkey AI-powered dog training web app that ingests skill notecards, extracts data using Gemini 3 Pro, and generates training plans.

## Architecture

### Tech Stack
- **Backend**: Python + FastAPI
- **Frontend**: React + Vite + TailwindCSS (for "wow" aesthetics)
- **Database**: SQLite (local file)
- **AI**: Gemini 3 Pro (via `google-genai`)
- **Deployment**: Docker + Docker Compose

### Directory Structure
```
dog-training-app/
├── backend/
│   ├── app/
│   │   ├── __init__.py
│   │   ├── main.py          # FastAPI entry point
│   │   ├── api.py           # API endpoints
│   │   ├── models.py        # Pydantic & DB models
│   │   ├── database.py      # SQLite connection
│   │   ├── ingest.py        # Image ingestion logic
│   │   └── services.py      # Gemini integration
│   ├── requirements.txt
│   └── Dockerfile.backend
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── App.jsx
│   │   └── main.jsx
│   ├── package.json
│   ├── vite.config.js
│   └── Dockerfile.frontend
├── data/
│   ├── dog_skill_notecards/ # Image inputs
│   └── skills.db            # SQLite DB
├── docker-compose.yml
└── README.md
```

## Data Model

### Skill
- `id`: Integer (PK)
- `name`: String (Unique)
- `cue`: String
- `description`: Text
- `image_filename`: String (optional, reference to source image)

## API Endpoints

- `GET /api/skills`: List all skills
- `GET /api/skills/{id}`: Get skill details
- `POST /api/skills/{id}/training-plan`: Generate training plan using Gemini
- `POST /api/ingest`: Trigger ingestion process (idempotent)

## Implementation Steps

1.  **Backend Setup**: Initialize FastAPI, SQLite, and Pydantic models.
2.  **Ingestion Logic**: Implement image iteration and Gemini extraction.
3.  **API Implementation**: Create endpoints for skills and training plans.
4.  **Frontend Setup**: Initialize Vite + React project with TailwindCSS.
5.  **Frontend UI**: Build Skill List and Skill Detail pages with "wow" design.
6.  **Integration**: Connect Frontend to Backend.
7.  **Dockerization**: Create Dockerfiles and Compose file.
8.  **Documentation**: Write README.

## Verification
- Run `docker compose up`.
- Verify ingestion logs.
- Check UI at `localhost`.
- Generate a training plan and verify output.
