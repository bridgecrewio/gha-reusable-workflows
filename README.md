# GitHub Actions reusable workflows

A collection of reusable workflows for GitHub Actions.

- [mypy](#mypy)
- [pre-commit](#pre-commit)

## mypy

Sets up Python, installs `pipenv` and the projects dev dependencies and lastly runs `mypy`

```yaml
jobs:
  pre-commit:
    uses: bridgecrewio/gha-reusable-workflows/.github/workflows/main.yaml@main
    with:
      python-version: "3.11"  # if a specific Python version is needed, defaults to "3.7"
      runner: "ubuntu-20.04"  # if a specific GitHub runner is neded, defaults to "ubuntu-latest"
```

## pre-commit

Sets up Python and runs the `pre-commit/action`

```yaml
jobs:
  pre-commit:
    uses: bridgecrewio/gha-reusable-workflows/.github/workflows/pre-commit.yaml@main
    with:
      python-version: "3.11"  # if a specific Python version is needed, defaults to "3.7"
      runner: "ubuntu-20.04"  # if a specific GitHub runner is neded, defaults to "ubuntu-latest"
```
