# Repository Overview: Getting Started with GitHub Copilot

## Main Functionality

This repository serves as an **interactive learning exercise** designed to teach developers how to use GitHub Copilot effectively. It combines a practical coding project (a school activity registration system) with step-by-step tutorials that guide users through various GitHub Copilot features.

## Dual Purpose

### 1. Educational Exercise Framework
A structured, multi-step tutorial that teaches GitHub Copilot usage through hands-on practice. The exercise is automated using GitHub Actions workflows that track learner progress.

### 2. Sample Application
A functional web application called "Mergington High School Activities API" that serves as the practice project for the exercise.

---

## Key Components

### Application Components

#### Backend - FastAPI REST API (`src/app.py`)
- **Technology**: Python with FastAPI framework
- **Purpose**: RESTful API for managing extracurricular activity signups
- **Key Features**:
  - In-memory data storage for activities and participants
  - View all available activities with participant counts
  - Register students for activities via email
  - Serves static frontend files
  - Auto-generated API documentation at `/docs` and `/redoc`

**API Endpoints**:
- `GET /` - Redirects to the web interface
- `GET /activities` - Returns all activities with details and participant counts
- `POST /activities/{activity_name}/signup?email={email}` - Registers a student for an activity

#### Frontend - Web Interface (`src/static/`)
- **index.html**: User interface for viewing and signing up for activities
- **app.js**: JavaScript application logic that:
  - Fetches activities from the API
  - Displays activity cards with availability information
  - Handles form submission for activity signups
  - Provides user feedback on signup success/failure
- **styles.css**: Styling for the web interface

#### Data Model
The application uses simple in-memory data structures:
- **Activities**: Dictionary with activity names as keys, containing:
  - Description
  - Schedule
  - Maximum participants
  - List of participant emails
- **Example Activities**: Chess Club, Programming Class, Gym Class (with room for expansion during exercises)

### Exercise Components

#### Step-by-Step Tutorial (`.github/steps/`)
Progressive learning modules that teach different Copilot features:
1. **1-preparing.md**: Introduction to Copilot, setting up Codespaces, basic @workspace queries
2. **2-first-introduction.md**: Bug fixing, inline suggestions, inline chat, generating sample data
3. **3-copilot-edits.md**: Using Copilot Edit Mode for multi-file changes
4. **4-copilot-agent-mode.md**: Using Copilot Agent Mode for autonomous coding tasks
5. **5-copilot-on-github.md**: Using Copilot features on github.com
6. **x-review.md**: Exercise completion and review

#### Automated Progress Tracking (`.github/workflows/`)
GitHub Actions workflows that:
- **0-start-exercise.yml**: Initializes the exercise, creates issue, posts first step
- **1-preparing.yml**: Validates branch creation and progression
- **2-first-introduction.yml**: Checks for bug fix commits
- **3-copilot-edits.yml**: Validates Edit Mode exercises
- **4-copilot-agent-mode.yml**: Validates Agent Mode exercises
- **5-copilot-on-github.yml**: Final step validation

Each workflow monitors for specific learner actions (branch creation, commits, etc.) and automatically progresses the exercise by posting next steps as issue comments.

#### Development Environment (`.devcontainer/`)
Pre-configured GitHub Codespaces environment:
- Python 3.13 container
- Auto-installs dependencies via `requirements.txt`
- Pre-loaded VS Code extensions:
  - GitHub Copilot
  - Python language support
  - Python debugger
- Port 8000 forwarded for local testing

#### Launch Configuration (`.vscode/launch.json`)
VS Code debugging configuration for running the FastAPI application with uvicorn.

---

## Learning Objectives

Students using this repository will learn to:
1. **Ask Mode**: Query Copilot about code structure and get project explanations
2. **Inline Suggestions**: Accept AI-powered code completions as they type
3. **Inline Chat**: Get targeted help on specific code selections
4. **Edit Mode**: Make controlled multi-file edits with AI assistance
5. **Agent Mode**: Let Copilot work autonomously on complex tasks
6. **Terminal Integration**: Get command-line help from Copilot
7. **Commit Message Generation**: Auto-generate descriptive commit messages

---

## How It Works

1. **Learner starts** by clicking a badge in README that creates an issue
2. **GitHub Actions respond** by posting the first exercise step
3. **Learner creates a Codespace** with the pre-configured development environment
4. **Step-by-step progression**: Learner works through exercises using different Copilot features
5. **Automatic validation**: GitHub Actions detect learner progress (branches, commits) and automatically post next steps
6. **Hands-on practice**: All exercises involve real code changes to the sample application
7. **Exercise completion**: Final review and congratulations

---

## Technology Stack

### Runtime
- **Language**: Python 3.13
- **Web Framework**: FastAPI
- **Server**: Uvicorn ASGI server

### Development
- **IDE**: VS Code (via GitHub Codespaces)
- **AI Assistant**: GitHub Copilot
- **Version Control**: Git/GitHub
- **CI/CD**: GitHub Actions

### Frontend
- **HTML5** with semantic structure
- **CSS3** for styling
- **Vanilla JavaScript** (no frameworks) for API interaction

---

## Project Structure

```
.
├── .devcontainer/          # Codespaces configuration
│   └── devcontainer.json   # Container settings and extensions
├── .github/
│   ├── steps/              # Tutorial content for each learning step
│   └── workflows/          # Automated progress tracking
├── .vscode/
│   └── launch.json         # Debug configuration for FastAPI
├── src/
│   ├── app.py              # FastAPI backend application
│   ├── static/             # Frontend files
│   │   ├── index.html      # UI structure
│   │   ├── app.js          # Client-side logic
│   │   └── styles.css      # Styling
│   └── README.md           # Application documentation
├── requirements.txt        # Python dependencies
├── pytest.ini              # Test configuration
└── README.md               # Exercise entry point
```

---

## Notable Features

### Educational Design
- **Progressive complexity**: Starts with simple queries, builds to autonomous agents
- **Real-world scenarios**: Bug fixing, feature addition, data generation
- **Immediate feedback**: See changes reflected in running application
- **Multiple interaction modes**: Covers breadth of Copilot capabilities

### Application Design
- **Simple but complete**: Full-stack application that's easy to understand
- **Extensible**: Easy to add activities, features, or validation during exercises
- **No database required**: In-memory storage keeps focus on Copilot, not infrastructure
- **Production patterns**: Uses proper REST API design, error handling, and documentation

---

## Getting Started

### For Learners
Click the badge in the main README to start the exercise. An automated issue will guide you through each step.

### For Running the Application Standalone
```bash
# Install dependencies
pip install -r requirements.txt

# Run the application
python src/app.py

# Access the application
# Web UI: http://localhost:8000
# API Docs: http://localhost:8000/docs
```

---

## Summary

This repository is a **comprehensive GitHub Copilot training program** disguised as a simple school activity registration system. It teaches developers how to effectively use AI-assisted coding through practical, hands-on exercises while building real features in a working web application. The automated workflow system provides guidance and validation, making it a self-paced learning experience suitable for developers at any level.
