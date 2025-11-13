<!--
Brief: Guidance for AI coding agents (GitHub Copilot-style) to be productive in this repository.
Generated: automated update — please review and tweak to taste.
-->

# Copilot / AI Agent Instructions — demo repository

Purpose
- Be immediately productive in this repository by describing the repo snapshot, where to look next, and concrete, reproducible commands to discover build/test/runtime details.

Repository snapshot
- This repository currently contains only `README.md` at the project root. There are no obvious language manifests (`package.json`, `pyproject.toml`, `*.csproj`, `pom.xml`) or source directories present.

What to do first (quick checklist)
- Confirm current tree: run `git ls-files` or from PowerShell:
  - `Get-ChildItem -File -Recurse | Select-Object FullName`
- Look for common manifests and CI files (examples):
  - `package.json`, `yarn.lock` (JavaScript/Node)
  - `pyproject.toml`, `requirements.txt` (Python)
  - `*.csproj`, `global.json` (dotnet)
  - `pom.xml` (Java/Maven)
  - `Dockerfile`, `.github/workflows/**`, `Makefile`
- If none of the above exist (as is currently the case), treat this repo as a scaffold or content placeholder and follow the guidance below.

How to discover architecture and conventions
- Search for tests and CI to understand language and runner choices: check `tests`, `spec`, `src`, and `.github/workflows`.
- Use file-extension based discovery to detect primary language(s): look for `.js`, `.ts`, `.py`, `.cs`, `.java`, `.go`, `.rs` etc.
- Use these PowerShell commands for robust discovery on Windows (copy/paste):
  - `Get-ChildItem -Recurse -File | Select-String -Pattern "package.json|pyproject.toml|Dockerfile|\.github"`
  - If `rg` (ripgrep) is available: `rg --hidden --no-ignore "package.json|pyproject.toml|Dockerfile|\.github"`

Project-specific patterns and conventions (discoverable)
- Currently there are no discovered project-specific coding conventions or build scripts inside this repo to follow.
- When you find a manifest, prefer using the commands and scripts defined there (e.g., `npm test`, `dotnet test`, `pytest`). Do not assume a custom test runner unless a CI workflow or script indicates one.

Making changes
- If creating new files, follow these lightweight rules for this repo until a stricter convention appears:
  - Use a short feature branch: `feature/<short-desc>` or `fix/<short-desc>`.
  - Make small, focused commits with imperative messages (e.g., "Add initial CLI scaffold").
  - Open a pull request against `main` with a brief description and any manual verification steps.

If a `.github/copilot-instructions.md` already exists
- Merge rather than overwrite: preserve any human-curated sections (project history, developer notes). Add missing discovery steps and update the repository snapshot at the top.

Examples (how to reference files found)
- If you find `src/` and `tests/`, prefer running the test runner declared in `package.json` / `pyproject.toml` and reference those files explicitly in PR descriptions: e.g., "Changes touch `src/foo.js` and `tests/foo.test.js` — run `npm test` locally." 

When unsure, ask
- If the repository lacks build/test artifacts (like today), ask the maintainers what the intended language/target is and whether this repo is intentionally empty or a placeholder.

Follow-ups for maintainers
- Consider adding a short CONTRIBUTING.md that declares the preferred language, build/test commands, and branch/PR convention. This makes future AI assistance much more precise.

End of file
