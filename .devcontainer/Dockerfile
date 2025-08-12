# Use an official Node.js image as a base
FROM node:18-bullseye

# Install AWS CLI v2
RUN apt-get update && apt-get install -y \
    unzip \
    curl \
    less \
    groff \
    && curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" \
    && unzip awscliv2.zip \
    && ./aws/install \
    && rm -rf awscliv2.zip aws

# Install AWS SAM CLI
RUN apt-get install -y \
    git \
    zip \
    && curl -Lo sam-installation.sh https://raw.githubusercontent.com/aws/aws-sam-cli/main/scripts/install/install.sh \
    && chmod +x sam-installation.sh \
    && ./sam-installation.sh --yes \
    && rm sam-installation.sh

# Verify installations
RUN aws --version && sam --version && node -v && npm -v
