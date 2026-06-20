FROM alpine:latest

RUN apk add --no-cache \
    git \
    ca-certificates \
    bash

ARG USERNAME=vscode

RUN adduser -D -s /bin/bash $USERNAME

USER $USERNAME