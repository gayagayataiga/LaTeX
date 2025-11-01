FROM mcr.microsoft.com/devcontainers/base:ubuntu

# Install TeX Live and additional packages
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends \
    texlive-full \
    texlive-lang-japanese \
    texlive-fonts-recommended \
    texlive-fonts-extra \
    latexmk \
    perl \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Create output directory
RUN mkdir -p /workspace/out && chown -R vscode:vscode /workspace/out

# Set working directory
WORKDIR /workspace
