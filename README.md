## Build image

[![.github/workflows/test-build-image.yaml](https://github.com/CoyoteLeo/actions/actions/workflows/test-build-image.yaml/badge.svg?branch=main)](https://github.com/CoyoteLeo/actions/actions/workflows/test-build_image.yaml)

```yaml
jobs:
  # ...
  build-image:
    permissions:
      contents: read
      packages: write
    uses: CoyoteLeo/actions/.github/workflows/build-image.yaml@main
    with:
      image: ${{ vars.DOCKER_USERNAME }}/${{ github.event.repository.name }}
      tags: ${{ inputs.tag }}
    secrets:
      DOCKER_USERNAME: ${{ vars.DOCKER_USERNAME }}
      DOCKER_PASSWORD: ${{ secrets.DOCKER_PASSWORD }}
```

## Lint

[![.github/workflows/test-python-lint.yaml](https://github.com/CoyoteLeo/actions/actions/workflows/test-python-lint.yaml/badge.svg?branch=main)](https://github.com/CoyoteLeo/actions/actions/workflows/test-python-lint.yaml)

```yaml
jobs:
  # ...
  lint:
    uses: CoyoteLeo/actions/.github/workflows/python-lint.yaml@main
    with:
      image: ${{ inputs.image }}
```

## Gitops-deploy

Utilize [dasel](https://github.com/TomWright/dasel) to update the config file

[//]: # ([![.github/workflows/test-gitops-deploy.yaml]&#40;https://github.com/CoyoteLeo/actions/actions/workflows/test-gitops-deploy.yaml/badge.svg?branch=main&#41;]&#40;https://github.com/CoyoteLeo/actions/actions/workflows/test-gitops-deploy.yaml&#41;)

```yaml
jobs:
  # ...
  deploy:
    uses: CoyoteLeo/actions/.github/workflows/gitops-deploy.yaml@main
    with:
      repository: ${{ inputs.repository }}
      path: airflow/values.yaml
      selector: images.airflow.tag
      value: main-latest
    secrets:
      REPO_PAT: ${{ secrets.REPO_PAT }}
```
 