# Nextcloud Using Podman Quadlets

An easy way to run Nextcloud with Podman.

Useful if you're running on a Linux desktop, server, or raspberry pi.
Does not work for distributed systems.

## Why make this

1. Docker doesn't come preinstalled on my Linux distro, and I didn't bother to setup Docker compatibility.
2. All of the Nextcloud with Podman tutorials were kinda confusing, and I wish someone else had made this.
3. Pods are super convenient for networking.
4. Quadlets are a sort-of alternative to Docker compose. It's an easier single-machine configuration than k8s, while still portable and declarative.

## System Dependencies
- Podman >= 5
- Systemd

Podman 5 is needed for the `.pod` file, and arrives with Fedora 40 in April 2024. I've been running it on Fedora Kinoite rawhide for a few months without issues.

## File Dependencies
You need the following directories on first start. Any location is fine as long as the `.container` files are updated.
- mariadb
- nextcloud/config
- nextcloud/data
- caddy/data

And you need a Caddyfile to configure the Caddy reverse proxy.

## Build

As long as these files are in one of the Quadlet search locations (i.e. ~/.config/containers/systemd) then Podman automatically transpiles them to
systemd unit files and enables them on system start.

Trigger without restart using `systemctl daemon-reload`.

