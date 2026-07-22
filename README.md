# Coding with AI Template

A cookiecutter template for organizing AI-assisted coding projects with comprehensive context documentation, feature specifications, research notes, and bug fixes.

## Overview

This template provides a structured approach to managing coding projects where you work closely with AI assistants. It includes organized directories for:

- **Context Documentation**: Project overview, coding standards, AI interaction guidelines
- **Features**: Detailed specifications and implementation plans for each feature
- **Fixes**: Bug fixes and issue resolutions
- **Research**: Investigation notes and technical research

## Quick Start

### Generate a New Project

```bash
uvx cookiecutter https://github.com/GioDecio/coding-with-ai-template
```

You'll be prompted to enter:
- **project_name**: Name of your project (e.g., "My Web App")
- **project_slug**: URL-friendly version (auto-generated from project name)
- **project_description**: Brief description of your project
- **author_name**: Your name
- **author_email**: Your email

### Directory Structure

Once created, your project will have this structure:

```
your-project/
└── context/
    ├── ai-interaction.md          # Guidelines for working with AI
    ├── coding-standards.md         # Project coding standards
    ├── current-feature.md          # Current feature being worked on
    ├── project-overview.md         # Project overview and goals
    ├── features/                   # Feature specifications
    │   ├── auth-phase-1-spec.md
    │   ├── dashboard-spec.md
    │   └── ...
    ├── fixes/                      # Bug fixes and resolutions
    │   └── github-oauth-redirect-fix.md
    └── research/                   # Technical research and investigations
        ├── ai-integration-research.md
        └── ...
```

## Usage

1. **Update context files** with your project-specific information:
   - `project-overview.md`: Describe your project goals and architecture
   - `coding-standards.md`: Define your coding standards and conventions
   - `ai-interaction.md`: Document how you want to work with AI assistants

2. **Add feature specifications** as you plan features:
   - Create new `.md` files in `context/features/`
   - Use consistent formatting for specifications

3. **Document research** as you investigate technical decisions:
   - Create new `.md` files in `context/research/`

4. **Track fixes** in the fixes directory:
   - Document bugs and their solutions
   - Create `.md` files for each fix

## Tips for Success

- **Keep context fresh**: Update your context files regularly as the project evolves
- **Use consistent formatting**: Maintain consistent markdown formatting across all files
- **Cross-reference**: Link related documents using markdown links
- **Share with Claude Code**: Use these context files when working with Claude Code to provide comprehensive project context
- **Version control**: Include the context directory in your git repository

## Example Context Files

The template includes example files from a real project. Feel free to:
- Modify examples to match your project structure
- Delete unused examples
- Create new files following the same format

## License

This template is provided as-is for organizing your coding projects.
