FROM ghcr.io/rizuke/devcontainers/base:latest

USER root
RUN apk add --no-cache python3 py3-pip

USER vscode

# Install web search extension for Pi Agent
RUN pi install npm:pi-web-access