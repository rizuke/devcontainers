FROM alpine:latest

RUN apk add --no-cache \
    git \
    ca-certificates \
    bash \
    # Pi Agent
    nodejs \
    npm \
    ripgrep \
    fd

ARG USERNAME=vscode

RUN adduser -D -s /bin/bash $USERNAME

# Pi Agent
RUN npm install -g --ignore-scripts @earendil-works/pi-coding-agent
RUN mkdir -p /home/$USERNAME/.pi/agent \
    && chown -R $USERNAME:$USERNAME /home/$USERNAME/.pi

USER $USERNAME