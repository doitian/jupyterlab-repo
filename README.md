# jupyterlab-repo

Monorepo for JupyterLab notebooks managed with [uv](https://docs.astral.sh/uv/).

## Overview

This repository is organized as a workspace with multiple notebook projects, each with their own dependencies managed by uv.

## Structure

```
jupyterlab-repo/
├── pyproject.toml          # Root workspace configuration
├── notebooks/
│   ├── data-analysis/      # Data analysis notebooks
│   │   ├── pyproject.toml
│   │   └── example.ipynb
│   ├── machine-learning/   # Machine learning notebooks
│   │   ├── pyproject.toml
│   │   └── example.ipynb
│   └── visualization/      # Visualization notebooks
│       ├── pyproject.toml
│       └── example.ipynb
└── README.md
```

## Prerequisites

- Python 3.10 or higher
- [uv](https://docs.astral.sh/uv/) package manager

## Installation

1. Install uv if you haven't already:

```bash
# On macOS and Linux
curl -LsSf https://astral.sh/uv/install.sh | sh

# Or with pip
pip install uv
```

2. Clone this repository:

```bash
git clone <repository-url>
cd jupyterlab-repo
```

3. Install all dependencies:

```bash
uv sync
```

This will install JupyterLab and all dependencies for all workspace members.

## Usage

### Starting JupyterLab

```bash
uv run jupyter lab
```

This will start JupyterLab with access to all notebooks in the workspace.

### Running a specific notebook

```bash
uv run jupyter notebook notebooks/data-analysis/example.ipynb
```

### Adding dependencies

#### To the root workspace:

Edit `pyproject.toml` and add dependencies, then run:

```bash
uv sync
```

#### To a specific notebook project:

Edit the `pyproject.toml` in the notebook's directory (e.g., `notebooks/data-analysis/pyproject.toml`), then run:

```bash
uv sync
```

### Creating a new notebook project

1. Create a new directory under `notebooks/`:

```bash
mkdir notebooks/my-project
```

2. Create a `pyproject.toml` file:

```toml
[project]
name = "my-project"
version = "0.1.0"
description = "My project description"
requires-python = ">=3.10"
dependencies = [
    # Add your dependencies here
]

[build-system]
requires = ["hatchling"]
build-backend = "hatchling.build"
```

3. Sync dependencies:

```bash
uv sync
```

## Workspace Benefits

- **Centralized dependency management**: All projects share the same virtual environment
- **Consistent Python version**: Enforced across all notebooks
- **Fast dependency resolution**: uv's resolver is significantly faster than pip
- **Reproducible environments**: Lock files ensure consistent installs

## Development

### Code formatting

```bash
uv run black notebooks/
```

### Linting

```bash
uv run ruff check notebooks/
```

## License

This project is licensed under the Mozilla Public License Version 2.0 - see the [LICENSE](LICENSE) file for details.
