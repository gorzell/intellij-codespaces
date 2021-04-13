# This defaults to Intellij Community Edition, but you should be able to use any JetBrains IDE they publish an image for.
# https://github.com/JetBrains/projector-docker#run-jetbrains-ide-in-docker
FROM registry.jetbrains.team/p/prj/containers/projector-idea-c

# The JetBrains images add a non-root user, which is probably a good thing, but doesn't provide a path to install further software, which we need to do.
# Also, Codespaces generally default to running as `root` so this might align better with how they function.
USER root

# Install SDKs and other tools you may need here.
RUN apt-get update \
    && apt-get install -y \
    build-essential \
    clang \
    ca-certificates \
    git \
    git-lfs \
    heaptrack \
    libssl-dev \
    lldb \
    procps \
    # Install Docker CE CLI
    && apt-get install -y apt-transport-https ca-certificates curl gnupg-agent software-properties-common lsb-release \
    && curl -fsSL https://download.docker.com/linux/$(lsb_release -is | tr '[:upper:]' '[:lower:]')/gpg | (OUT=$(apt-key add - 2>&1) || echo $OUT) \
    && apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 0xB1998361219BD9C9 \
    && add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/$(lsb_release -is | tr '[:upper:]' '[:lower:]') $(lsb_release -cs) stable" \
    && apt-get update \
    && apt-get install -y docker-ce-cli \
    # Install Docker Compose
    && curl -sSL "https://github.com/docker/compose/releases/download/1.28.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose \
    && chmod +x /usr/local/bin/docker-compose \
    && apt-get clean -y \
    && apt-get autoremove -y \
    && rm -rf /var/lib/apt/lists/*