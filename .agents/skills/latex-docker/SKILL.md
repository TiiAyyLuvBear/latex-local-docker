---
name: latex-docker
description: Use when setting up, testing, or troubleshooting local LaTeX compilation with Docker and VS Code.
---

# Local LaTeX with Docker

Work in the project directory specified by the user. Read the project's `AGENTS.md` and `README.md` when available, and respect existing files and configuration.

1. Check the operating system, `docker version` (both Client and Server), VS Code, and the `James-Yu.latex-workshop` extension. If a prerequisite is missing or Docker Engine is stopped, identify the precise blocking step; the Docker CLI alone is insufficient.
2. Use `texlive/texlive:latest` and `latexmk -xelatex` as described in the README unless the project or user specifies another version. Pull the image when needed. Do not install TeX Live on the host unless requested.
3. For VS Code, install LaTeX Workshop if missing and configure the workspace. Inspect existing files before changing them; do not overwrite global settings. With LaTeX Workshop's Docker integration, use `latexmk`, set the working directory to the root document's directory, and pass a relative document filename to the container.
4. Build the sample or the document selected by the user. Check the exit code and generated PDF. If possible, inspect Vietnamese text and the equation. On failure, inspect the log and report the blocking step. Do not claim the PDF renders correctly without inspecting it.
5. Report the test command, result, PDF path and any limitations. Preserve user data and do not upload private files without authorization.
