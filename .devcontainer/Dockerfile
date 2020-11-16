FROM mcr.microsoft.com/vscode/devcontainers/universal:linux

# Install MongoDB command line tools
ARG MONGO_TOOLS_VERSION=4.2
RUN curl -sSL "https://www.mongodb.org/static/pgp/server-${MONGO_TOOLS_VERSION}.asc" | (OUT=$(sudo apt-key add - 2>&1) || echo $OUT) \
    && echo "deb http://repo.mongodb.org/apt/debian $(lsb_release -cs)/mongodb-org/${MONGO_TOOLS_VERSION} main" | sudo tee /etc/apt/sources.list.d/mongodb-org-${MONGO_TOOLS_VERSION}.list \
    && sudo apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && sudo apt-get install -y --allow-unauthenticated mongodb-org-tools mongodb-org-shell \
    && sudo apt-get clean -y && sudo rm -rf /var/lib/apt/lists/*

# [Optional] Uncomment this section to install additional OS packages.
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends <your-package-list-here>

# [Optional] Uncomment if you want to install an additional version of node using nvm
# ARG EXTRA_NODE_VERSION=10
# RUN su node -c "source /usr/local/share/nvm/nvm.sh && nvm install ${EXTRA_NODE_VERSION}"

# [Optional] Uncomment if you want to install more global node packages
# RUN sudo -u node npm install -g <your-package-list-here>
