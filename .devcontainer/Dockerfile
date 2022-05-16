# You can use any debian based image you want
ARG VARIANT=bullseye
FROM mcr.microsoft.com/vscode/devcontainers/python:3.8-${VARIANT}

# Install openvpn client and docker
RUN export DEBIAN_FRONTEND=noninteractive && \
curl -fsSL https://pkgs.tailscale.com/stable/debian/$(lsb_release -cs).noarmor.gpg | tee /usr/share/keyrings/tailscale-archive-keyring.gpg >/dev/null && \
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/tailscale-archive-keyring.gpg] https://pkgs.tailscale.com/stable/debian $(lsb_release -cs) main" | tee /etc/apt/sources.list.d/tailscale.list > /dev/null && \
apt update && \
apt -y install tailscale && \
usermod -s /bin/zsh vscode

COPY vpn /usr/local/bin/vpn
