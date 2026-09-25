# Git and VS Code Environment Setup

This document records the Windows development environment prepared for maintaining the SOC analyst portfolio. The setup was verified locally before any portfolio changes were published.

## Objective

Prepare a secure and repeatable Git and Visual Studio Code workflow for documenting cybersecurity labs, reviewing changes and publishing approved evidence to GitHub.

## Verified Environment

| Component | Verified value |
| --- | --- |
| Operating system | Windows 11, 64-bit |
| Git | 2.50.1.windows.1 |
| Visual Studio Code | 1.136.1, x64 |
| Default Git branch | `main` |
| Git author | Ritik Chauhan |
| Commit email | GitHub private no-reply address configured |
| Remote repository | `ritik19coder/soc-analyst-portfolio` over HTTPS |
| Working branch | `task/task-2-git-vscode-setup` |

The private no-reply address is intentionally omitted from this public document.

## Security and Privacy Controls

- Enabled GitHub email privacy.
- Enabled GitHub protection that blocks command-line pushes exposing a private email address.
- Configured command-line commits to use the GitHub no-reply identity.
- Kept TLS certificate verification enabled.
- Confirmed that local VS Code settings are excluded by `.gitignore`.
- Checked screenshots and command output for credentials and personal information before publication.

## Git Configuration

The following commands show the configuration pattern. The actual no-reply address must be copied from the authenticated GitHub email settings page and must not be replaced with a personal address in public evidence.

```powershell
git config --global user.name "Ritik Chauhan"
git config --global user.email "YOUR_GITHUB_NOREPLY_EMAIL"
git config --global init.defaultBranch main
```

Verification commands:

```powershell
git --version
git config --global user.name
git config --global init.defaultBranch
git status
git remote -v
```

The email value is deliberately excluded from screenshots and copied output.

## Repository Setup

The public portfolio was cloned into a dedicated GitHub workspace and checked before editing.

```powershell
git clone https://github.com/ritik19coder/soc-analyst-portfolio.git
cd soc-analyst-portfolio
git status
git remote -v
code .
```

The validation showed that local `main` was up to date with `origin/main` and the working tree was clean.

## Windows TLS Troubleshooting

The first clone attempt reached GitHub but the Windows Schannel TLS backend closed the connection unexpectedly with `missing close_notify`. The repository was cloned successfully using Git for Windows' bundled OpenSSL backend and HTTP/1.1, without disabling certificate validation.

```powershell
git config --global http.sslBackend openssl
git config --global http.version HTTP/1.1
git fetch origin
```

Disabling `http.sslVerify` was rejected because it would weaken transport security.

## VS Code Extensions

| Extension | Purpose |
| --- | --- |
| Markdown All in One | Markdown authoring and preview support |
| markdownlint | Consistent Markdown structure and formatting |
| Python | Python development and debugging support for future security scripts |
| GitLens | Git history and change visibility |

Installed extension identifiers:

```text
yzhang.markdown-all-in-one
DavidAnson.vscode-markdownlint
ms-python.python
eamodio.gitlens
```

## Workflow

1. Synchronise `main` with the remote repository.
2. Create a task-specific branch before editing.
3. Review changes with `git diff` and `git status`.
4. Check documents and evidence for sensitive information.
5. Commit locally with a clear message.
6. Request approval before pushing or merging.

## Outcome

Git, GitHub and VS Code are configured for a privacy-conscious portfolio workflow. The repository can be cloned, fetched and edited locally; the default branch and remote are correct; and the selected extensions support technical documentation and future Python projects.
