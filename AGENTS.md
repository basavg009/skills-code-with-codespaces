# AGENTS.md

## Cursor Cloud specific instructions

This repository is a **GitHub Skills course template** (not a traditional application). It teaches learners how to use GitHub Codespaces and VS Code.

### What this repo contains

- `index.html` — A trivial HTML page learners edit as part of the course exercise
- `.devcontainer/devcontainer.json` — Codespace configuration (universal image + Copilot extension)
- `.github/workflows/` — GitHub Actions that auto-progress learners through course steps
- `setup.sh` — Demo script that installs the `sl` package (used in a course exercise)
- `codespace.md` — File that gets appended to during exercises

### Running locally

Serve the static site with any HTTP server:

```bash
python3 -m http.server 8080 --directory /workspace
```

Then open `http://localhost:8080/index.html`.

### Validation / Linting

There is no formal linting setup. Useful manual validation:

- **HTML**: `python3 -c "import html.parser; ..."` or any HTML validator
- **YAML** (workflows): `python3 -c "import yaml; yaml.safe_load(open('file.yml'))"` 
- **Shell**: `bash -n setup.sh`
- **JSON** (devcontainer): Parse `.devcontainer/devcontainer.json` (JSONC — strip `//` comments first)

### Important notes

- No dependencies to install (no `package.json`, `requirements.txt`, etc.)
- No build step required
- The GitHub Actions workflows only function on GitHub's platform — they cannot be tested locally
- The `postCreateCommand` in `devcontainer.json` appends to `codespace.md` on Codespace creation
