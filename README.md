# balena-tailscale

A [tailscale](https://tailscale.com) service for [balena.io](balena.io) devices. Tailscale connects any device to your 
own VLAN with minimal configuration.

## Usage
```yaml
version: "2"
services:
  tailscale:
    build:
      dockerfile: Dockerfile.template
    privileged: true
    network_mode: host
    command: -hostname=my-node
    environment:
      TAILSCALE_KEY: 
```
Privileged and and host network are both required, as is `TAILSCALE_KEY`, which you can generate 
[here](https://login.tailscale.com/admin/authkeys). Any additional command arguments are passed to `tailscale up`.

### Architectures
Tested via balena:
- amd64
- aarch64