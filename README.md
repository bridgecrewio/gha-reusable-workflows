# GitHub Actions reusable workflows

A collection of reusable workflows for GitHub Actions.

- [mypy](#mypy)
- [pre-commit](#pre-commit)
- [publish-image](#publish-image)

## mypy

Sets up Python, installs `pipenv` and the projects dev dependencies and lastly runs `mypy`

```yaml
jobs:
  mypy:
    uses: bridgecrewio/gha-reusable-workflows/.github/workflows/mypy.yaml@main
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

## publish-image

Builds and publishes a container image to Docker Hub and GitHub Container Registry

```yaml
jobs:
  mypy:
    uses: bridgecrewio/gha-reusable-workflows/.github/workflows/publish-image.yaml@main
    permissions:
      contents: read
      id-token: write  # Enable OIDC
      packages: write
    with:
      image_name_dockerhub: example/example
      image_name_ghcr: ghcr.io/${{ github.repository }}
      image_tag_full: 1.2.3
      image_tag_short: 1
      environment: deploy  # if a specific GitHub environment is needed, defaults to "release"
      image_platforms: linux/amd64  # if a specific target platform is needed, defaults to "linux/amd64,linux/arm64"
      runner: "['self-hosted', 'public', 'linux', 'x64']"  # currently it only works for hosted runners
    secrets:
      BC_API_KEY: ${{ secrets.BC_API_KEY }}
      DOCKERHUB_USERNAME: ${{ secrets.DOCKERHUB_USERNAME }}
      DOCKERHUB_PASSWORD: ${{ secrets.DOCKERHUB_PASSWORD }}
```
