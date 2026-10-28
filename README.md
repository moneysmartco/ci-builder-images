# ci-builder-images

Thin wrapper that lets the BuildKit image builder run as a Semaphore Kubernetes job container (the agent starts job containers with `bash`). DEVSECOPS-1223.

| Image | Base | Added |
|---|---|---|
| `ghcr.io/moneysmartco/ci-builder-images/buildkit-rootless:v0.33.1-bash2` | `moby/buildkit:v0.33.1-rootless` | `bash git openssh-client curl sudo` (passwordless sudo for `user`; still runs as uid 1000) |

The package is private; Semaphore pipelines pull it with `agent.image_pull_secrets: [{name: ghcr-pull}]`. It contains no secrets.
