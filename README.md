# Svelte Docker Tailscale Template

## Quick Start

Requires tailscale CLI installed & authenticated

```sh
# Get template files
TEMPLATE="https://raw.githubusercontent.com/mrgnw/svelte-docker-tailscale/main"
curl -O "$TEMPLATE/Dockerfile" & \
curl -O "$TEMPLATE/compose.yml" & wait

# Set up Tailscale config
echo "/tailscale" >> .gitignore
```

Get an auth key from [Tailscale admin console](https://login.tailscale.com/admin/settings/keys)

```sh
TS_AUTHKEY=
```

Then add it to your env

```sh
echo "TS_AUTHKEY=$TS_AUTHKEY" >> .env
```

```sh
docker compose up
```

That's it! Your app will be available at `https://${PWD##*/}.$TAILNET`

## Features

- Zero-config setup - uses directory name for all defaults
- Easy URL access through Tailscale
- Hot Module Reloading (HMR) support
- Secure access from any device
- Uses Bun for faster installs
- Automatic port assignment to prevent conflicts

## Configuration overrides

All configuration is optional except `TS_AUTHKEY`. Defaults are:
- Project name: directory name
- Network name: `${COMPOSE_PROJECT_NAME}-network`
- Hostname: `${COMPOSE_PROJECT_NAME}`
- Domain: `${COMPOSE_PROJECT_NAME}.$TAILNET`
- Tailscale port: 4164 (override with TS_PORT if running multiple instances)
- Svelte port: 5173 (internal only)

Override any of these by setting them in `.env`