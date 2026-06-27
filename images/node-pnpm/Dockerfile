FROM node:lts-bookworm-slim

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        git \
        ca-certificates \
        curl \
        # Pi Agent
        ripgrep \
        fd-find \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN corepack enable \
    && corepack prepare pnpm@latest --activate

ENV PNPM_HOME=/usr/local/share/pnpm
ENV PATH=$PNPM_HOME/bin:$PATH

ENV PNPM_STORE=/home/node/.pnpm-store
RUN mkdir -p ${PNPM_STORE} \
    && chown node:node ${PNPM_STORE}

# Install Pi Agent
RUN pnpm add -g --ignore-scripts @earendil-works/pi-coding-agent
RUN mkdir -p /home/node/.pi/agent \
    && chown -R node:node /home/node/.pi

USER node

# Install global extensions for Pi Agent
RUN pi install npm:@juicesharp/rpiv-todo \
    && pi install npm:@juicesharp/rpiv-ask-user-question

RUN pnpm config set store-dir ${PNPM_STORE}