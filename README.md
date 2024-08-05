<!-- start title -->

# GitHub Action:Build and Push Image to quay.io

<!-- end title -->
<!-- start description -->

Builds and pushs an image to a quay.io image repository

<!-- end description -->
<!-- start contents -->
<!-- end contents -->
<!-- start usage -->

```yaml
- uses: catalystcommunity/action-build-push-image-quay@undefined
  with:
    # The full name of the repository where the image will be pushed. Default is the
    # GitHub repository name, ex: organization/repository.
    # Default: ${{ github.repository }}
    repository: ""

    # Username for authentication to quay.io.
    username: ""

    # Password for authentication to quay.io
    password: ""

    # git tags to push, comma separated string such as `latest,v1.0.0`
    # Default: latest,${{ github.event.release.tag_name }}
    tag-versions: ""

    # docker build secrets. key=value pairs separated by newlines. See [docker build
    # push action secrets configuration](https://github.com/docker/build-push-action/blob/master/docs/advanced/secrets.md) for details
    # Default:
    build-secrets: ""

    # docker context. Passed to [docker build push action context
    # input](https://github.com/docker/build-push-action#inputs). It should be
    # relative to the root of the commit that triggered the action
    # Default: ./
    docker-context: ""

    # path to docker file relative to docker-context. Passed to [docker build push
    # action file input](https://github.com/docker/build-push-action#inputs)
    # Default: Dockerfile
    docker-file: ""

    # whether to automatically checkout the current repository
    # Default: true
    checkout: ""
```

<!-- end usage -->
<!-- start inputs -->

| **Input**            | **Description**                                                                                                                                                                                                 |                  **Default**                  | **Required** |
| :------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-------------------------------------------: | :----------: |
| **`repository`**     | The full name of the repository where the image will be pushed. Default is the GitHub repository name, ex: organization/repository.                                                                             |          `${{ github.repository }}`           |  **false**   |
| **`username`**       | Username for authentication to quay.io.                                                                                                                                                                         |                                               |   **true**   |
| **`password`**       | Password for authentication to quay.io                                                                                                                                                                          |                                               |   **true**   |
| **`tag-versions`**   | git tags to push, comma separated string such as `latest,v1.0.0`                                                                                                                                                | `latest,${{ github.event.release.tag_name }}` |  **false**   |
| **`build-secrets`**  | docker build secrets. key=value pairs separated by newlines. See [docker build push action secrets configuration](https://github.com/docker/build-push-action/blob/master/docs/advanced/secrets.md) for details |                                               |  **false**   |
| **`docker-context`** | docker context. Passed to [docker build push action context input](https://github.com/docker/build-push-action#inputs). It should be relative to the root of the commit that triggered the action               |                     `./`                      |  **false**   |
| **`docker-file`**    | path to docker file relative to docker-context. Passed to [docker build push action file input](https://github.com/docker/build-push-action#inputs)                                                             |                 `Dockerfile`                  |  **false**   |
| **`checkout`**       | whether to automatically checkout the current repository                                                                                                                                                        |                    `true`                     |  **false**   |

<!-- end inputs -->
<!-- start outputs -->

| **Output**      | **Description** | **Default** | **Required** |
| :-------------- | :-------------- | ----------- | ------------ |
| `random-number` | Random number   |             |              |

<!-- end outputs -->
<!-- start examples -->

### Example usage

```yaml
name: Build and push image to quay.io
on:
  release:
    types: [created]
jobs:
  build-push-image:
    runs-on: ubuntu-latest
    steps:
      - uses: catalystcommunity/action-build-push-image-quay@v1
        with:
          username: ${{ secrets.QUAY_DOCKER_REGISTRY_USER }}
          password: ${{ secrets.QUAY_DOCKER_REGISTRY_PASSWORD }}
```

<!-- end examples -->
<!-- start [.github/ghdocs/examples/] -->
<!-- end [.github/ghdocs/examples/] -->
