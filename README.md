# DevOps Github Actions

A repository that contains composite Github actions that can be used in
other Github actions.

## Actions

### `common-build-setup`

#### What it does
* Login to YFU's Docker registry
* Start SSH Agent for private Github repositories
* Git checkout

#### How it's used

```
- name: Common Setup
  uses: yfu-is/devops-github-actions/.github/actions/common-build-setup@main
  with:
    docker_registry_url: ${{ vars.DOCKER_REGISTRY_URL }}
    docker_registry_username: ${{ secrets.DOCKER_REGISTRY_USERNAME }}
    docker_registry_password: ${{ secrets.DOCKER_REGISTRY_PASSWORD }}
    ssh_private_key: ${{ secrets.MACHINEUSER_SSH_PRIVATE_KEY }}
```