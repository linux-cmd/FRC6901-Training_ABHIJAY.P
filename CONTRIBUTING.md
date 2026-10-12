# Contributing to your training fork

These steps keep project work easy to review and make it clear which files changed.

## Before you start

Check your branch and working tree:

```bash
git status
git branch --show-current
git remote -v
```

`origin` should be your GitHub fork. `upstream` should be the original team repository. Open one WPILib project at a time and make changes inside that project's folder.

## Make a focused change

Create a branch for one project or one related task:

```bash
git switch main
git switch -c project-1/controller-input
```

Build the project you changed before committing. For example, from the Project 1 folder on Windows:

```powershell
.\gradlew.bat build
```

Review what you plan to save:

```bash
git status
git diff
```

Stage only the project and documentation you intended to change. Quote paths with spaces:

```bash
git add "Project 1 Basic Romi Drive-Imported/src/main/java/frc/robot/Robot.java"
git diff --cached
```

Commit a small, complete change. Use a short message that says what changed:

```bash
git commit -m "docs: clarify Project 1 controller lesson"
```

Useful message prefixes include `docs:`, `feat:`, `fix:`, and `chore:`. Do not commit build output, simulator state, personal IDE workspace files, or generated files; the root `.gitignore` excludes these.

## Push your work

Push the branch to your fork, not the team source repository:

```bash
git push -u origin project-1/controller-input
```

For personal practice, you can then open a pull request into your fork's `main` branch, or merge the branch locally after reviewing it. Never force-push to the shared team source.

## Get new team material

Fetch updates from the original repository:

```bash
git fetch upstream
```

Then merge or rebase `upstream/main` into your work branch after checking the project instructions. If you are unsure, stop and ask before resolving a conflict; do not discard either side's changes.
