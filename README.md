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
- name: Common Build Setup
  uses: yfu-is/devops-github-actions/.github/actions/common-build-setup@main
  with:
    docker_registry_url: ${{ vars.DOCKER_REGISTRY_URL }}
    docker_registry_username: ${{ secrets.DOCKER_REGISTRY_USERNAME }}
    docker_registry_password: ${{ secrets.DOCKER_REGISTRY_PASSWORD }}
    ssh_private_key: ${{ secrets.MACHINEUSER_SSH_PRIVATE_KEY }}
```

### `connect-to-vpn`

#### What it does
* Connects to an OpenVPN network

#### How it's used

```
- name: Connect to OpenVPN
  uses: yfu-is/devops-github-actions/.github/actions/connect-to-vpn@main
  with:
    username: ${{ secrets.OPENVPN_USERNAME }}
    password: ${{ secrets.OPENVPN_PASSWORD }}
    config: ${{ secrets.OPENVPN_CONFIG }}
    # seconds to wait for connection establishment, optional, default: 30
    wait: 30
```