ARG VARIANT="16-bullseye"
FROM piotrzan/nginx-demo:green as demo
# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.202.1/containers/typescript-node/.devcontainer/base.Dockerfile

# [Choice] Node.js version (use -bullseye variants on local arm64/Apple Silicon): 16, 14, 12, 16-bullseye, 14-bullseye, 12-bullseye, 16-buster, 14-buster, 12-buster
FROM mcr.microsoft.com/vscode/devcontainers/typescript-node:0-${VARIANT} as main

COPY --from=demo /usr/share/nginx/html/ ./demo-app/

RUN wget https://github.com/mikefarah/yq/releases/download/v4.13.3/yq_linux_amd64 && \
    chmod +x yq_linux_amd64 && \
    mv yq_linux_amd64 /usr/local/bin/yq && \
    curl -L https://github.com/kubernetes/kompose/releases/download/v1.24.0/kompose-linux-amd64 -o kompose && \
    chmod +x kompose && \
    mv kompose /usr/local/bin/kompose && \
    curl https://get.datree.io | /bin/bash && \
    wget https://github.com/instrumenta/kubeval/releases/latest/download/kubeval-linux-amd64.tar.gz && \
    tar xf kubeval-linux-amd64.tar.gz && \
    mv kubeval /usr/local/bin && \
    curl -sfL https://raw.githubusercontent.com/aquasecurity/trivy/main/contrib/install.sh | sh -s -- -b /usr/local/bin v0.20.1 && \
    curl -sfL https://releases.dagger.io/dagger/install.sh | sh && \
    chmod +x ./bin/dagger && \
    mv ./bin/dagger /usr/local/bin

# [Optional] Uncomment this section to install additional OS packages.
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends figlet

# [Optional] Uncomment if you want to install an additional version of node using nvm
# ARG EXTRA_NODE_VERSION=10
# RUN su node -c "source /usr/local/share/nvm/nvm.sh && nvm install ${EXTRA_NODE_VERSION}"

# [Optional] Uncomment if you want to install more global node packages
RUN su node -c "npm install -g cdk8s-cli"
