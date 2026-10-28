# ci-builder-images

Thin wrapper that lets the BuildKit image builder run as Semaphore Kubernetes job containers (the agent starts containers with `bash`). DEVSECOPS-1223 build-tool trial.

| Image | Base | Added |
|---|---|---|
| `ghcr.io/moneysmartco/ci-builder-images/buildkit-rootless:v0.33.1-bash` | `moby/buildkit:v0.33.1-rootless` | `bash git openssh-client curl` (still runs as uid 1000) |

Images contain no secrets; they are public so job pods pull without credentials.
