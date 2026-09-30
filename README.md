# VeriSelf — Digital Identity Defense for the Non-Famous

<p align="center">
  <strong>Protecting personal identity in the age of manipulated and misused media.</strong>
</p>

<p align="center">
  <a href="https://github.com/keke2204/ASK-TEAM">Repository</a>
  ·
  <a href="https://github.com/keke2204/ASK-TEAM/releases/tag/v1.0">v1.0</a>
</p>

---

## Overview

**VeriSelf** is an identity-protection application designed to help ordinary people understand, verify, monitor, and respond to the misuse of their digital identity.

Modern manipulation is no longer limited to celebrities or public figures. A person's photograph can be copied, altered, impersonated, or reused across the public web without their knowledge.

VeriSelf brings several defensive capabilities into one workflow:

**Learn your identity → Detect manipulation → Monitor public web → Verify matches → Collect evidence → Respond → Protect future media**

The project combines a modern web interface with a Python/FastAPI backend and computer-vision techniques to create a practical identity-defense workflow rather than a static demonstration dashboard.

---

## Why VeriSelf?

Digital identity protection often becomes difficult because evidence is scattered across different tools and platforms.

VeriSelf is designed around a simple idea:

> **Give the individual a practical way to understand what happened, verify what they found, collect evidence, and take the next defensive step.**

### Core problems addressed

- Unauthorized reuse of personal photographs
- Manipulated or altered images
- Potential identity impersonation
- Public-web monitoring
- Image matching and verification
- Evidence collection
- Defensive response/removal workflows
- Protection of future media

---

## Product Workflow

```text
┌─────────────────────┐
│  Learn Your Identity│
└──────────┬──────────┘
           ↓
┌─────────────────────┐
│ Detect Manipulation │
└──────────┬──────────┘
           ↓
┌─────────────────────┐
│ Monitor Public Web  │
└──────────┬──────────┘
           ↓
┌─────────────────────┐
│   Verify Matches    │
└──────────┬──────────┘
           ↓
┌─────────────────────┐
│  Collect Evidence   │
└──────────┬──────────┘
           ↓
┌─────────────────────┐
│ Respond / Removal   │
└──────────┬──────────┘
           ↓
┌─────────────────────┐
│ Protect Future Media│
└─────────────────────┘
```

---

## Key Capabilities

### 🔎 Identity & Image Analysis

The application can work with uploaded media and analyze it using image-processing and computer-vision techniques.

### 🧬 Image Similarity

VeriSelf uses techniques such as **perceptual hashing** and **embeddings** to help identify visually related media.

### 🛡️ Manipulation Detection

Computer-vision processing can be used as part of the workflow for identifying suspicious or altered media.

### 🌐 Public-Web Monitoring

The backend is designed to inspect publicly accessible web content using HTTP-based retrieval and browser automation where appropriate.

### 🧾 Evidence Collection

Potential findings can be organized into useful evidence so that the user has a clearer record of what was discovered.

### 📤 Defensive Response

The workflow moves beyond detection by providing a path toward response and removal actions.

### 🔐 Future Media Protection

The final stage focuses on helping users protect media they publish in the future.

---

## Architecture

VeriSelf follows a frontend/backend architecture:

```text
                    ┌──────────────────────┐
                    │      User / Web      │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │ React + Vite +       │
                    │ Tailwind Frontend    │
                    └──────────┬───────────┘
                               │ HTTP / API
                               ▼
                    ┌──────────────────────┐
                    │   FastAPI Backend    │
                    └──────────┬───────────┘
                               │
          ┌────────────────────┼────────────────────┐
          ▼                    ▼                    ▼
 ┌────────────────┐   ┌────────────────┐   ┌────────────────┐
 │ Image / Vision │   │ Web Monitoring │   │ Data / Storage │
 │ Processing     │   │ & Verification │   │ SQLite + ORM   │
 └────────────────┘   └────────────────┘   └────────────────┘
          │                    │
          ▼                    ▼
 ┌────────────────┐   ┌────────────────┐
 │ OpenCV /       │   │ HTTPX /        │
 │ Hashing /      │   │ Selectolax /   │
 │ Embeddings     │   │ Playwright     │
 └────────────────┘   └────────────────┘
```

A source architecture diagram is also included in the repository as `architecture.svg`.

---

## Technology Stack

| Layer | Technology |
|---|---|
| Frontend | React, Vite, Tailwind CSS |
| Backend | Python, FastAPI |
| Database | SQLite, SQLAlchemy |
| Computer Vision | OpenCV |
| ML / Data | NumPy, Pandas, Scikit-learn |
| Image Matching | Perceptual Hashing, Embeddings |
| Web Retrieval | HTTPX, Selectolax |
| Browser Automation | Playwright |
| Testing | Pytest |
| Deployment | Render + GitHub Pages |
| Version Control | Git + GitHub |

---

## Project Structure

```text
ASK-TEAM/
│
├── .github/
│   ├── workflows/
│   │   ├── backend-check.yml
│   │   ├── build-updated-zip.yml
│   │   └── live-integration.yml
│   └── live-integration-test.cjs
│
├── apps/
│   └── backend/
│       ├── app/
│       │   ├── main.py
│       │   └── __init__.py
│       ├── tests/
│       │   └── test_api.py
│       ├── requirements.txt
│       └── README.md
│
├── docs/
│   └── STAGE15_DEPLOYMENT.md
│
├── architecture.svg
├── backend-bridge.js
├── index.html
├── logo.svg
├── render.yaml
├── script.js
├── style.css
└── README.md
```

---

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/keke2204/ASK-TEAM.git
cd ASK-TEAM
```

### 2. Backend setup

Open a terminal in the backend directory:

```bash
cd apps/backend
```

Create a virtual environment:

```bash
python -m venv .venv
```

Activate it on Windows:

```bat
.venv\Scripts\activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

### 3. Start the API

```bash
uvicorn app.main:app --reload
```

The FastAPI development server will normally be available at:

```text
http://127.0.0.1:8000
```

Interactive API documentation:

```text
http://127.0.0.1:8000/docs
```

Health endpoint:

```text
/api/health
```

---

## API Layer

The backend is built with **FastAPI**, providing a lightweight API layer between the web interface and identity-analysis services.

The interactive Swagger documentation available at `/docs` can be used to inspect and test the exposed endpoints during development.

---

## Verification & Testing

Automated testing is included through **Pytest**.

Run the backend tests from the backend directory:

```bash
pytest
```

The repository also contains GitHub Actions workflows for automated backend checks and integration-oriented validation.

---

## Deployment

The project is structured for a separated frontend/backend deployment model.

### Frontend

The frontend can be deployed as a static web application, including through GitHub Pages.

### Backend

The FastAPI backend includes Render deployment configuration through:

```text
render.yaml
```

This separation allows the user interface and API service to be deployed independently while communicating through HTTP APIs.

---

## Security & Privacy

VeriSelf is intended as a **defensive identity-protection project**.

Important principles:

- Analyze only media and public information that the user is authorized to process.
- Do not treat automated similarity results as definitive proof of identity.
- Preserve evidence carefully when investigating potential misuse.
- Avoid exposing unnecessary personal information.
- Respect website terms, access controls, robots policies, and applicable laws.
- Human review should remain part of important identity-related decisions.

---

## Limitations

VeriSelf is a defensive research and application project. Automated image matching and manipulation analysis can produce false positives and false negatives.

A similarity score or detection result should therefore be treated as **supporting evidence**, not as an unquestionable conclusion.

Public-web monitoring is also inherently limited by:

- Search/index coverage
- Website availability
- Dynamic content
- Access restrictions
- Changes to public pages
- Rate limits and network conditions

---

## Roadmap

Potential future improvements include:

- More robust multimodal identity verification
- Improved manipulation and deepfake detection
- Broader public-web discovery
- Stronger evidence packaging
- Additional privacy controls
- Improved media-protection mechanisms
- More comprehensive automated testing
- Expanded deployment monitoring
- Better user guidance for response/removal workflows

---

## Release

### v1.0 — Initial Release

**Tag:** `v1.0`

VeriSelf v1.0 represents the initial release of the **Digital Identity Defense for the Non-Famous** project.

Release page:

https://github.com/keke2204/ASK-TEAM/releases/tag/v1.0

---

## Team

### ASK TEAM

**Project:** VeriSelf  
**Title:** Digital Identity Defense for the Non-Famous

Built as an AI/ML-focused software project combining web engineering, computer vision, machine learning, and defensive digital-identity workflows.

---

## Contributing

Contributions and improvements are welcome.

1. Fork the repository.
2. Create a feature branch.
3. Make your changes.
4. Test the changes.
5. Open a pull request with a clear description.

---

## License

If a specific license has not yet been added to this repository, the project remains subject to the copyright and usage rights of its authors. Add an appropriate `LICENSE` file before distributing the project under an open-source license.

---

<p align="center">
  <strong>VeriSelf</strong><br>
  Digital Identity Defense for the Non-Famous
</p>
