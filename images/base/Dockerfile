FROM alpine:latest

RUN apk add --no-cache \
    git \
    ca-certificates \
    bash \
    curl \
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

# Install global extensions for Pi Agent
RUN pi install npm:@juicesharp/rpiv-todo \
    && pi install npm:@juicesharp/rpiv-ask-user-question