# Semaphore's Kubernetes agent starts job containers with bash and checks out over ssh with git.
FROM moby/buildkit:v0.33.1-rootless
USER root
RUN apk add --no-cache bash git openssh-client curl ca-certificates
# Back to the image's unprivileged user so rootlesskit keeps its uid 1000 + subuid setup
USER 1000:1000
