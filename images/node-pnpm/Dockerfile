FROM node:lts-bookworm-slim

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        git \
        ca-certificates \
        # Pi Agent
        ripgrep \
        fd-find \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN corepack enable \
    && corepack prepare pnpm@latest --activate

ENV PNPM_HOME=/usr/local/share/pnpm
ENV PATH=$PNPM_HOME/bin:$PATH

# Install Pi Agent
RUN pnpm add -g --ignore-scripts @earendil-works/pi-coding-agent

ENV PNPM_STORE=/home/node/.pnpm-store
RUN mkdir -p ${PNPM_STORE} \
    && chown node:node ${PNPM_STORE}

USER node

RUN pnpm config set store-dir ${PNPM_STORE}