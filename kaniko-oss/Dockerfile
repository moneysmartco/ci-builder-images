# Semaphore's Kubernetes agent starts job containers with bash; the kaniko debug image only ships busybox sh.
FROM debian:bookworm-slim AS bash
RUN apt-get update && apt-get install -y --no-install-recommends bash-static && rm -rf /var/lib/apt/lists/*

FROM alpine:3.20 AS curl
ADD --checksum=sha256:e45ae1805ceb3f816e9768fbbaba05d98a2dc9c5577f66395f37660941d88e19 https://github.com/moparisthebest/static-curl/releases/download/v8.21.0/curl-amd64 /curl
RUN chmod 0755 /curl

FROM ghcr.io/osscontainertools/kaniko:v1.29.0-debug
# /busybox is on PATH and excluded from kaniko snapshots, so the extra shell never lands in built images
COPY --from=bash /bin/bash-static /busybox/bash
# Semaphore's job setup resolves the current user; the scratch-based kaniko image has no passwd/group
COPY passwd /etc/passwd
COPY group /etc/group
# Semaphore downloads its toolbox (artifact, retry, ...) with curl; static build from moparisthebest/static-curl
COPY --from=curl /curl /busybox/curl
