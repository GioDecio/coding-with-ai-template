# {{ cookiecutter.project_name }}

{{ cookiecutter.project_description }}

## Setup

This project uses [UV](https://docs.astral.sh/uv/) for Python dependency management.

### Initialize the Virtual Environment

```bash
uv sync
```

This will:
- Create a virtual environment
- Install dependencies from `pyproject.toml`
- Prepare the project for development

### Activate the Environment

```bash
source .venv/bin/activate  # On macOS/Linux
# or
.venv\Scripts\activate  # On Windows
```

## Project Structure

See `context/project-overview.md` for detailed project information.

## Documentation

- `context/project-overview.md` - Project goals and architecture
- `context/coding-standards.md` - Coding standards and conventions
- `context/ai-interaction.md` - Guidelines for working with AI assistants
- `context/features/` - Feature specifications
- `context/research/` - Technical research and investigations
- `context/fixes/` - Bug fixes and resolutions
