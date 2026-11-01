# Automated Website Deployment Using GitHub Actions

A beginner-level DevOps project: a static HTML/CSS website that is **deployed automatically to GitHub Pages** every time code is pushed to the `main` branch.

> Replace `YOUR-USERNAME` with your GitHub username wherever it appears (this file and `site/index.html`).

Live site: `https://Srikrishna-045.github.io/github-actions-deployment/`

## Project Description
The project contains a responsive website (HTML5 + CSS3) and a GitHub Actions workflow. After the one-time setup, publishing a change takes three Git commands; GitHub does the rest.

## Problem Statement
Deploying a website by hand (copying files to a server each time) is slow, repetitive and error-prone. Updates can be forgotten, wrong files can be uploaded, and there is no record of what was released.

## Objectives
- Build a responsive static website using only HTML and CSS.
- Keep the source code under version control with Git and GitHub.
- Automate deployment with GitHub Actions on every push to `main`.
- Host the site publicly and free of cost using GitHub Pages.
- Verify the pipeline with documented test cases.

## Technologies Used
HTML5, CSS3, Git, GitHub, GitHub Actions, GitHub Pages, Visual Studio Code.

## System Requirements
- Windows 10/11 (or macOS/Linux), 4 GB RAM, 1 GB free disk space, internet connection
- Git, Visual Studio Code, a web browser, a free GitHub account

## Project Architecture
```
Developer (VS Code)
      |  git commit
      v
Local Git repository
      |  git push
      v
GitHub repository (main branch)
      |  push event triggers
      v
GitHub Actions workflow (deploy.yml)
  checkout -> configure pages -> upload ./site artifact -> deploy
      |
      v
GitHub Pages  -->  Public website URL
```

## Folder Structure
```
github-actions-deployment/
├── site/                     # the website that gets published
│   ├── index.html            # page structure and content
│   └── style.css             # colours, layout, responsive rules
├── .github/
│   └── workflows/
│       └── deploy.yml        # GitHub Actions deployment workflow
├── README.md                 # this documentation
└── .gitignore                # files Git should ignore
```
| Item | Purpose |
|---|---|
| `site/` | Only this folder is published. |
| `site/index.html` | The website page with all six sections. |
| `site/style.css` | All styling, including mobile layout. |
| `.github/workflows/` | GitHub only looks for workflows in this exact folder. |
| `deploy.yml` | Tells GitHub Actions when and how to deploy. |
| `README.md` | Explains the project. |
| `.gitignore` | Stops junk files (e.g. `Thumbs.db`) being committed. |

## Installation Instructions
1. Install Git: https://git-scm.com/downloads
2. Install Visual Studio Code: https://code.visualstudio.com
3. Create a free GitHub account: https://github.com
4. Extract the project ZIP and open the `github-actions-deployment` folder in VS Code.

Preview locally by double-clicking `site/index.html`.

## Implementation Procedure
1. Configure Git name and email.
2. `git init`, `git add .`, `git commit`.
3. Create an empty **public** repository on GitHub.
4. Set **Settings → Pages → Source = GitHub Actions**.
5. Connect the remote and push to `main`.
6. Watch the **Actions** tab until the run is green.

Full commands are in `project-documents/01-STEP-BY-STEP-GUIDE.md`.

## GitHub Actions Workflow Explanation
| Part | Meaning |
|---|---|
| `on: push: branches: ["main"]` | Run on every push to main. |
| `workflow_dispatch` | Allows manual run from the Actions tab. |
| `permissions` | `contents: read`, `pages: write`, `id-token: write` – the minimum needed. |
| `concurrency` | Only one Pages deployment at a time. |
| `actions/checkout@v4` | Downloads the repository code. |
| `actions/configure-pages@v5` | Prepares Pages settings. |
| `actions/upload-pages-artifact@v3` | Packages `./site` as an artifact. |
| `actions/deploy-pages@v4` | Publishes the artifact; returns the site URL. |

## Deployment Instructions
Push to `main`. The workflow runs by itself. To redeploy without a change: **Actions → Deploy website to GitHub Pages → Run workflow**.

## Testing Procedure
Five test cases are in `project-documents/02-TESTING-DOCUMENTATION.md`: first deployment, public URL access, heading change, automatic redeploy, and live update check.

## Expected Output
A green check on the workflow run and a live, responsive blue-and-white website at the GitHub Pages URL.

## Future Enhancements
- Add an HTML validation step before deployment (true CI).
- Add more pages and a contact form.
- Use a custom domain.
- Add a status badge to this README.

## Conclusion
The project shows the core DevOps idea: automate repeatable work. A single `git push` now builds and publishes the website without manual effort.
