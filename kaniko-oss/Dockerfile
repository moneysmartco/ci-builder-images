# Semaphore's Kubernetes agent starts job containers with bash; the kaniko debug image only ships busybox sh.
FROM debian:bookworm-slim AS bash
RUN apt-get update && apt-get install -y --no-install-recommends bash-static && rm -rf /var/lib/apt/lists/*

FROM ghcr.io/osscontainertools/kaniko:v1.29.0-debug
# /busybox is on PATH and excluded from kaniko snapshots, so the extra shell never lands in built images
COPY --from=bash /bin/bash-static /busybox/bash
