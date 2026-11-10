# VPN Bandwidth Manager

Versioned installer packages for the per-session OpenVPN Access Server bandwidth manager.

## Current package

- **Bandwidth engine:** v2.1.0
- **Package:** `vpn-bandwidth-manager-v2.1.0.zip`
- **Download:** [Download v2.1.0](https://raw.githubusercontent.com/T2DevPub/vpn_limit/main/releases/v2.1.0/vpn-bandwidth-manager-v2.1.0.zip)

## Install

On an Ubuntu 24.04 server where OpenVPN Access Server is already installed:

```bash
apt-get update
apt-get install -y curl unzip
cd /root
curl -fL "https://raw.githubusercontent.com/T2DevPub/vpn_limit/main/releases/v2.1.0/vpn-bandwidth-manager-v2.1.0.zip" -o vpn-bandwidth-manager-v2.1.0.zip
unzip -o vpn-bandwidth-manager-v2.1.0.zip
cd vpn-bandwidth-manager-v1
chmod +x install.sh activate.sh uninstall.sh
./install.sh
```

The installer stage installs the manager but does **not** activate traffic shaping. Review the server's tunnel/IFB mapping and existing qdiscs before running `./activate.sh`.

## Safety notes

- Do not publish production credentials, private keys, VPN certificates, or real user configuration in this repository.
- The package preserves an existing `/etc/vpn-bandwidth/users.conf`.
- The included v2.1.0 engine has the tested tunnel-to-IFB mapping `as0t0 -> ifb1` and `as0t1 -> ifb0`; verify this mapping on every server before activation.
- The installer does not replace existing qdiscs. It is a staged installer, not an automatic migration of arbitrary traffic-control configurations.
