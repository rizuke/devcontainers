FROM node:lts-bookworm-slim

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        git \
        ca-certificates \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN corepack enable \
    && corepack prepare pnpm@latest --activate

ENV PNPM_HOME=/home/node/.pnpm-store
RUN mkdir -p ${PNPM_HOME} \
    && mkdir -p /home/node/.pi/agent \
    && chown -R node:node /home/node

USER node

RUN pnpm config set store-dir ${PNPM_HOME}

RUN pnpm add -g --ignore-scripts @earendil-works/pi-coding-agent