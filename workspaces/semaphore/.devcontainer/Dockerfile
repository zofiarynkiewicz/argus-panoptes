FROM mcr.microsoft.com/devcontainers/typescript-node:1-20-bullseye

# Install isolate-vm dependencies, these are needed by the @backstage/plugin-scaffolder-backend.
RUN --mount=type=cache,target=/var/cache/apt,sharing=locked \
    --mount=type=cache,target=/var/lib/apt,sharing=locked \
    apt-get update && \
    apt-get install -y --no-install-recommends python3 python3-pip python3-setuptools python3-venv g++ build-essential  libsqlite3-dev && \
    yarn config set python /usr/bin/python3 && \
    corepack enable

ENV VIRTUAL_ENV=/opt/venv
RUN python3 -m venv "$VIRTUAL_ENV"
ENV PATH="$VIRTUAL_ENV/bin:$PATH"

# Set Python interpreter for `node-gyp` to use
ENV PYTHON /usr/bin/python3

RUN pip3 install setuptools