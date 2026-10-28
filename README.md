# ci-builder-images

Thin wrappers that let image builders run as Semaphore Kubernetes job containers (the agent starts containers with `bash`). DEVSECOPS-1223 build-tool trial.

| Image | Base | Added |
|---|---|---|
| `ghcr.io/moneysmartco/ci-builder-images/kaniko-oss:v1.29.0-bash` | `ghcr.io/osscontainertools/kaniko:v1.29.0-debug` | Debian `bash-static` at `/busybox/bash` |
| `ghcr.io/moneysmartco/ci-builder-images/kaniko-gitlab:v1.25.19-1-bash` | `registry.gitlab.com/gitlab-com/public-sector/kaniko:v1.25.19-1-debug` | Debian `bash-static` at `/busybox/bash` |
| `ghcr.io/moneysmartco/ci-builder-images/buildkit-rootless:v0.33.1-bash` | `moby/buildkit:v0.33.1-rootless` | `bash git openssh-client curl` (still runs as uid 1000) |

Images contain no secrets; they are public so job pods pull without credentials.
