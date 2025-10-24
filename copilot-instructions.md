# Copilot instructions for EstalPropTech

This repository is currently minimal (only `README.md`). These instructions tell an AI coding agent how to be immediately productive here and what to do next when adding real project files.

1. Repo snapshot

   - Only detected file: `README.md` at repo root. No package manifests (e.g. `package.json`, `pyproject.toml`), no `src/` or `tests/` directories, and no CI workflows.
   - Default branch: `main`. Local dev OS: Windows (PowerShell `pwsh`).

2. High-level objectives for the agent

   - When asked to implement a feature, prefer creating a minimal, runnable scaffold (source folder, manifest, simple test, and README update) rather than large, unverified changes.
   - Keep commits small and self-contained. Add tests for new behavior and a short README usage snippet.

3. How to detect project type (do this before changing anything)

   - Search for these files (case-insensitive): `package.json`, `pyproject.toml`, `requirements.txt`, `Pipfile`, `go.mod`, `Cargo.toml`, `*.sln`, `*.csproj`, `Dockerfile`.
   - If none are present (current state), create a clear scaffold and document the choices in `README.md`.

4. Conventions to follow in this repo

   - Place source code under `src/` and tests under `tests/` (or language-native equivalents). Keep top-level directories shallow.
   - Use a single manifest at repo root (e.g., `package.json` for Node, `pyproject.toml` for Python). Add minimal scripts: `build`, `test`, `lint` where relevant.
   - Use PowerShell-compatible commands in docs and CI examples because the developer environment is Windows (`pwsh`). Where POSIX-only commands are necessary, provide Windows alternatives or note WSL requirements.

5. Helpful examples / copyable snippets

   - Node (example `package.json` scripts section to add when scaffolding):
     {
     "scripts": {
     "build": "echo build",
     "test": "echo test && exit 0",
     "lint": "echo lint"
     }
     }

   - PowerShell example to run tests (document in README):
     pwsh -Command "npm test" # or the appropriate command for the language

6. Testing and validation

   - New features must include at least one happy-path unit test runnable via the repo manifest's `test` script.
   - After adding files, run quick validation (lint/typecheck/test) and record the results in the commit message or PR description.

7. CI and workflows

   - If adding CI, place workflows under `.github/workflows/`. Use `pwsh` shell steps where platform matters, or include matrix OSes if you need cross-platform verification.

8. Integration points and external deps

   - There are no detected integrations in this snapshot. When adding external services (DB, APIs), also add a local dev stub or an integration test marked as optional.

9. When modifying `README.md`

   - Keep a short developer-focused section: how to build, test, run (one-liners), and the expected outputs for the initial scaffold.

10. Communication and PR expectations
    - Prefer small PRs with: What changed, Why, How to run locally, and test results.

If anything in this file looks incorrect (for example, you have private files I couldn't see), tell me which files to inspect or paste the missing manifests and I'll merge updates into this guidance.
