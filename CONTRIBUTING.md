# Contributing to Smart Grid Demand Response

Thank you for your interest in contributing! This document outlines how to get set up, how to run tests, and the conventions we follow in this project.

---

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/Smart-Grid-Openenv.git
cd Smart-Grid-Openenv
```

### 2. Create and activate a virtual environment

```powershell
# Windows (PowerShell)
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
python -m venv venv
.\venv\Scripts\Activate.ps1
```

```bash
# Linux / macOS
python -m venv venv
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -e ".[dev]"
```

---

## 📁 Project Structure

```
Smart-Grid-Openenv/
├── server/
│   ├── app.py          # FastAPI entry point
│   ├── grid_env.py     # Main Environment class (SmartGridEnv)
│   ├── simulator.py    # Physics engine (demand, battery, frequency)
│   ├── tasks.py        # Task definitions and graders
│   └── weather.py      # Markov weather engine
├── models.py           # Pydantic Action / Observation models (root level)
├── inference.py        # LLM agent inference entry point
├── openenv.yaml        # OpenEnv environment descriptor
├── Dockerfile          # Container build spec
└── pyproject.toml      # Project metadata and dependencies
```

---

## 🧪 Running Tests

```bash
# Run all tests
python -m pytest

# Run a specific test file
python test_env.py

# Verify environment compliance
openenv validate smart-grid-demand-response
```

---

## 🛠️ Development Workflow

1. **Create a feature branch** off `main`:
   ```bash
   git checkout -b feat/your-feature-name
   ```

2. **Make your changes** following the conventions below.

3. **Run the tests** to make sure nothing is broken.

4. **Commit** with a clear message:
   ```
   feat: add wind forecast to situation report
   fix: clamp battery SOC below 100% correctly
   docs: update CONTRIBUTING with test instructions
   refactor: extract reward calculation to helper
   ```

5. **Open a Pull Request** against `main` and describe what you changed and why.

---

## 🎨 Code Conventions

- **Python version**: 3.10+
- **Style**: Follow [PEP 8](https://peps.python.org/pep-0008/). Run `ruff check .` before committing.
- **Type hints**: All public functions must have type annotations.
- **Docstrings**: Use Google-style docstrings for public classes and methods.
- **No breaking changes**: The `Action` and `Observation` Pydantic models in `models.py` are part of the public API — any new field must have a default value so existing clients are unaffected.

---

## 🌍 Areas for Contribution

Here are some good areas to contribute to:

| Area | Ideas |
|------|-------|
| **New Tasks** | Add a `cold_wave` or `grid_restoration` scenario in `server/tasks.py` |
| **Grader improvements** | Refine the fairness scoring (Gini coefficient weighting) |
| **Weather system** | Add seasonal variation to Markov transition probabilities |
| **Situation Report** | Improve the natural-language briefing for edge cases |
| **Documentation** | Improve README, add docstrings, or write a tutorial notebook |
| **Testing** | Add more unit tests for the simulator physics |
| **Inference agents** | Implement a rule-based baseline agent in `inference.py` |

---

## 📋 Code of Conduct

Be respectful and constructive. We follow the [Contributor Covenant](https://www.contributor-covenant.org/).

---

**Happy hacking!** ⚡
