# Semaphore's Kubernetes agent starts job containers with bash; the kaniko debug image only ships busybox sh.
FROM debian:bookworm-slim AS bash
RUN apt-get update && apt-get install -y --no-install-recommends bash-static && rm -rf /var/lib/apt/lists/*

FROM registry.gitlab.com/gitlab-com/public-sector/kaniko:v1.25.19-1-debug
# /busybox is on PATH and excluded from kaniko snapshots, so the extra shell never lands in built images
COPY --from=bash /bin/bash-static /busybox/bash
# Semaphore's job setup resolves the current user; the scratch-based kaniko image has no passwd/group
COPY passwd /etc/passwd
COPY group /etc/group
