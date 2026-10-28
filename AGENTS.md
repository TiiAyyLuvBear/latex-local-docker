# Instructions for coding agents

- Read README.md and identify the operating system, Docker Engine, VS Code and LaTeX Workshop before setup. Do not assume Docker is installed or running.
- Use the `texlive/texlive:latest` Docker image and `latexmk -xelatex`; do not install TeX Live directly on the host unless requested. Preserve the user's sources and data.
- If Docker or VS Code is missing, explain the prerequisites and install only when the environment permits. Report any interactive or permission-dependent step that blocks progress.
- For VS Code, install `James-Yu.latex-workshop` if missing, open the project folder, and use `.vscode/settings.json`. Do not overwrite global user settings.
- Run the operating-system-appropriate Docker test in README. Check the exit code and that `main.pdf` exists. Check the Vietnamese text and equation if PDF inspection is available. Report results and unverified behavior; downloading an image alone is not a successful build.
- Rebuild affected documents after edits. Do not commit generated PDFs or auxiliary files unless requested. Do not delete user data; preserve unrelated changes.
- If adding or running Python code, use a virtual environment; ask the user when no suitable activation script exists, in accordance with their instructions. Deliver test cases and test results before completing programming work.

## Callable skill

For local LaTeX setup or troubleshooting with Docker, invoke `$latex-docker` if the environment supports skills, or read `.agents/skills/latex-docker/SKILL.md`. This AGENTS.md is project guidance and is not itself a callable skill.
