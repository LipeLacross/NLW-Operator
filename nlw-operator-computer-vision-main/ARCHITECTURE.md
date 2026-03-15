# Project Architecture

## 📁 Project Structure

```
nlw-operator-computer-vision/
├── lenet/                       # LeNet-5 MNIST Classification
│   ├── pyproject.toml          # Dependencies (PyTorch, Matplotlib, Jupyter)
│   ├── notebooks/              # Jupyter notebooks
│   ├── src/
│   │   ├── model.py           # LeNet-5 model definition
│   │   ├── train.py           # Training script
│   │   └── visualize.py       # Feature map visualization
│   └── README.md              # Module-specific documentation
│
├── recog_system/                # Recognition System & Lab
│   ├── pyproject.toml          # Dependencies (Scikit-Learn, MediaPipe, YOLO, Gemini)
│   ├── notebooks/              # Exploratory notebooks
│   ├── src/
│   │   ├── data/              # Data collection pipeline
│   │   ├── models/            # Model training scripts
│   │   └── utils/             # Helper functions
│   ├── .env                   # API keys (not committed)
│   └── README.md              # Module-specific documentation
│
├── computer_vision_app/         # FastHTML Web Application
│   ├── pyproject.toml          # Dependencies (FastHTML, OpenCV, MediaPipe)
│   ├── src/
│   │   ├── app.py             # Main FastHTML application
│   │   ├── camera.py          # Camera/WebSocket handling
│   │   └── gestures.py        # Gesture recognition logic
│   ├── static/                 # Static assets
│   └── README.md              # Module-specific documentation
│
├── public/                      # Public static files (screenshots)
├── docs/                        # Documentation
├── .gitignore
├── README.md                    # This file
└── .env.example                # Environment variables template
```

---

## 🎯 Architecture Principles

### Modular Design
- Each lesson module is independent with its own `pyproject.toml`
- Shared utilities can be extracted to a common `lib/` directory
- Environment isolation via uv workspaces

### Technology Choices
- **uv** for fast, reliable dependency management
- **PyTorch** for deep learning experiments (LeNet)
- **MediaPipe** for real-time hand/face landmark detection
- **FastHTML** for building web interfaces without JavaScript
- **WebSockets** for real-time video streaming

### Data Flow

```
┌─────────────────┐     ┌──────────────────┐     ┌─────────────────┐
│   Camera       │────▶│  MediaPipe       │────▶│  Classification │
│   (OpenCV)     │     │  (Landmarks)     │     │  (Scikit-Learn)│
└─────────────────┘     └──────────────────┘     └─────────────────┘
                                │
                                ▼
                        ┌──────────────────┐
                        │  WebSocket       │
                        │  (FastHTML)      │
                        └──────────────────┘
                                │
                                ▼
                        ┌──────────────────┐
                        │  Browser UI      │
                        └──────────────────┘
```

---

## 📝 Conventions

### Python Code
- **Type hints**: Required for all functions
- **Naming**: `snake_case` for functions/variables, `PascalCase` for classes
- **Formatting**: Use `ruff` or `black` for formatting
- **Linting**: Use `ruff` for linting

### Git Workflow
- Use conventional commits
- Create feature branches for new modules
- Keep main branch stable

### Module Structure
```
module/
├── pyproject.toml
├── src/
│   └── module/
│       ├── __init__.py
│       └── ...
├── tests/
│   └── ...
└── README.md
```

---

## 🧪 Development Workflow

### Setting Up Development Environment

```bash
# Install uv if not already installed
curl -LsSf https://astral.sh/uv/install.sh | sh

# Clone repository
git clone <repo-url>
cd nlw-operator-computer-vision-main

# Set up a module
cd lenet
uv sync

# Run Jupyter
jupyter notebook
```

### Running the Computer Vision App

```bash
cd computer_vision_app
uv sync
uv run python -m src.app
```

---

## 🔧 Maintenance

### Dependency Updates

```bash
# Update dependencies in a module
cd <module-name>
uv sync --upgrade
```

### Adding New Modules

1. Create a new directory
2. Add `pyproject.toml` with dependencies
3. Run `uv sync` to create virtual environment
4. Add module description to main README

---

## 📚 Tech Stack Summary

| Module | Technologies |
|--------|--------------|
| **LeNet** | PyTorch, torchvision, Matplotlib, Jupyter |
| **Recog System** | Scikit-Learn, MediaPipe, YOLO, CLIPSeg, Gemini, transformers |
| **CV App** | FastHTML, OpenCV, MediaPipe, Uvicorn, WebSockets |

---

**Last update**: 2026-03-14  
**Project version**: 0.1.0  
**Maintainer**: Arthur Kamienski
