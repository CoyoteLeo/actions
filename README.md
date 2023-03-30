## Build image

[![.github/workflows/test-build-image.yaml](https://github.com/CoyoteLeo/actions/actions/workflows/test-build-image.yaml/badge.svg?branch=main)](https://github.com/CoyoteLeo/actions/actions/workflows/test-build_image.yaml)

```yaml
jobs:
  build-image:
    permissions:
      contents: read
      packages: write
    uses: CoyoteLeo/actions/.github/workflows/build-image.yaml@main
    with:
      prefix: main
      registry: ${{ vars.DOCKER_REGISTRY }}
      image: ${{ vars.IMAGE_NAME }}
    secrets:
      DOCKER_USERNAME: ${{ secrets.DOCKER_USERNAME }}
      DOCKER_PASSWORD: ${{ secrets.DOCKER_PASSWORD }}
```
 