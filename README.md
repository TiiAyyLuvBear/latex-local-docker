# Local LaTeX with Docker and VS Code

Compile LaTeX locally with Docker and XeLaTeX, including Vietnamese text. Source files and the resulting PDF stay in your project folder; TeX Live does not need to be installed on the host.

## Prerequisites

- Install [Docker Desktop](https://www.docker.com/products/docker-desktop/) and start the Docker Engine. On Linux, Docker Engine can be used directly.
- Install [VS Code](https://code.visualstudio.com/) and the [LaTeX Workshop extension](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop).
- Install [Git](https://git-scm.com/) to clone and share the project.
- Run `docker version` and verify that both Client and Server are shown. The full TeX Live image is large and requires an internet connection for the first download.

## Getting started

1. Clone the repository and open its folder in VS Code using **File → Open Folder**. Trust the workspace if you trust its contents.
2. Run `docker pull texlive/texlive:latest` in a terminal and wait for it to finish.
3. Open `main.tex` and press `Ctrl+Alt+B` to build. The resulting `main.pdf` appears beside the source file.
4. Press `Ctrl+Alt+V` to view the PDF in VS Code. LaTeX Workshop may also rebuild after you save.

The workspace configuration is in `.vscode/settings.json`. Copy that folder into another project to reuse it. The container mounts the directory containing the main LaTeX file, so keep included files and images inside that directory. The `latest` image tag can change; agree on a specific image version if reproducible builds are needed.

## Build and test manually

From the project folder in PowerShell:

```powershell
docker run --rm -v "${PWD}:/workdir" -w /workdir texlive/texlive:latest latexmk -g -xelatex -interaction=nonstopmode -file-line-error main.tex
```

From the project folder in Bash on Linux or macOS:

```bash
docker run --rm -v "$PWD:/workdir" -w /workdir texlive/texlive:latest latexmk -g -xelatex -interaction=nonstopmode -file-line-error main.tex
```

The test passes when the command exits with code 0, produces `main.pdf`, and the PDF displays the Vietnamese text and equation correctly. The `-g` option forces a rebuild. Git ignores the PDF and generated auxiliary files.

## Collaborate on GitHub

The repository owner can invite people under **Settings → Collaborators**. Each collaborator can clone, edit, commit, push and pull changes; use branches and pull requests when review is needed. Git does not synchronize individual keystrokes like Overleaf. Do not commit passwords, tokens or private documents.

## Troubleshooting

- **Cannot connect to Docker:** start Docker Desktop, wait for the engine, and run `docker version` again.
- **Image unavailable:** retry `docker pull texlive/texlive:latest` and check your network connection and free disk space.
- **Build fails:** open **Output → LaTeX Workshop** and find the first error; check paths to images and included files. Run the manual command above for the full log.
- **Build command missing:** verify that LaTeX Workshop is installed and that you opened the folder containing `.vscode`.

## Using a coding agent

[AGENTS.md](AGENTS.md) contains project instructions for coding agents. The repository also provides the `latex-docker` skill in `.agents/skills/latex-docker/SKILL.md`. Open the repository in Codex and start a new session if needed for skill discovery, then ask:

```text
$latex-docker Check and set up local LaTeX for this project.
```

Agents without skill support can read `AGENTS.md` and `SKILL.md` directly. Calling a skill does not grant additional permissions.

## License

This project is licensed under the [MIT License](LICENSE).
