# jupyterlab-repo

JupyterLab notebooks project using [uv](https://docs.astral.sh/uv/).

## Overview

This repository contains Jupyter notebooks for data analysis, machine learning, and visualization tasks, all managed with uv for fast and reliable dependency management.

## Structure

```
jupyterlab-repo/
├── pyproject.toml          # Project configuration and dependencies
├── notebooks/
│   └── hello.ipynb         # Example notebook
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

This will install JupyterLab. You can add more dependencies as needed by editing `pyproject.toml`.

## Usage

### Starting JupyterLab

```bash
uv run jupyter lab
```

This will start JupyterLab with access to all notebooks in the `notebooks/` directory.

### Running a specific notebook

```bash
uv run jupyter notebook notebooks/hello.ipynb
```

### Adding dependencies

Edit `pyproject.toml` and add dependencies to the `dependencies` list, then run:

```bash
uv sync
```

For example, to add pandas and numpy:

```toml
dependencies = [
    "jupyterlab>=4.0.0",
    "pandas>=2.0.0",
    "numpy>=1.24.0",
]
```

### Adding new notebooks

Simply create new `.ipynb` files in the `notebooks/` directory. They will automatically have access to all installed dependencies.

## Example Notebook

The included `hello.ipynb` demonstrates:
- Basic Python execution in JupyterLab
- How to add and use packages as needed

## GitHub Pages Deployment

This repository includes a GitHub Actions workflow that automatically:
1. Converts all Jupyter notebooks in the `notebooks/` directory to HTML
2. Creates an index page listing all available notebooks
3. Deploys them to GitHub Pages

The workflow runs automatically on every push to the `main` branch. You can also trigger it manually from the Actions tab.

To enable GitHub Pages:
1. Go to your repository Settings > Pages
2. Under "Source", select "GitHub Actions"

Once deployed, your notebooks will be available at: `https://<username>.github.io/<repository-name>/`

## Development

### Linting

```bash
uv run ruff check notebooks/
```

The lock file (`uv.lock`) ensures consistent installations across different environments.

## Dependencies

This project includes:

- **JupyterLab**: Interactive computing environment
- **nbconvert**: Convert notebooks to other formats (used for GitHub Pages deployment)
- **Development**: ruff (linting)

Add additional packages as needed for your notebooks by editing `pyproject.toml`.

## License

This project is licensed under the Mozilla Public License Version 2.0 - see the [LICENSE](LICENSE) file for details.
