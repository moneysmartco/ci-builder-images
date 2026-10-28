# Semaphore's Kubernetes agent starts job containers with bash, checks out over ssh with git, and installs its toolbox with sudo.
FROM moby/buildkit:v0.33.1-rootless
USER root
RUN apk add --no-cache bash git openssh-client curl ca-certificates sudo \
 && echo 'user ALL=(ALL) NOPASSWD: ALL' > /etc/sudoers.d/semaphore-toolbox && chmod 0440 /etc/sudoers.d/semaphore-toolbox
# Back to the image's unprivileged user so rootlesskit keeps its uid 1000 + subuid setup
USER 1000:1000
