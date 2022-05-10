# About this template

This devcontainer template is built on Micrsoft's Debian Bullseye VSCode image and is designed to let you connect to Tailscale tailnet from inside a container.  

# Using this template with Github Codespaces or VSCode

Simply run `vpn up`.  This will start the `tailscaled` daemon, connect, and prompt you to authenticate in your browser.

```
❯ vpn up  

To authenticate, visit:

        https://login.tailscale.com/a/5605fb83dc99

Success.

```

# Using the container image alone

If you wish to run this container locally, you will need to invoke it with several options to ensure it can manage the network correctly, and has access to your VPN config.

1. Add `--cap-add=NET_ADMIN --cap-add=NET_RAW --cap-add=DAC_OVERRIDE --device=/dev/net/tun` to ensure the container can manage the network
2. Add `-u vscode` to run the container as `vscode` user, which has `sudo` privileges.
3. run `vpn up` as above
