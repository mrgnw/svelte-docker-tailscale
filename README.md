# Svelte Docker Tailscale Template

## Add these files to an existing project

```sh
TEMPLATE="https://raw.githubusercontent.com/mrgnw/svelte-docker-tailscale/main"
mkdir -p config
```

```sh
curl -O "$TEMPLATE/compose.yml" & \
curl -O "$TEMPLATE/Dockerfile" & \
curl -o config/serve.json $TEMPLATE/config/serve.json & \
(curl -s "$TEMPLATE/.env.example" | tee .env.example .env) & wait

echo "/tailscale" >> .gitignore
```

# Creating a new project

Use [sv create](https://svelte.dev/docs/cli/sv-create) to create a new svelte project

## Features

- Easy URL access through Tailscale
- Hot Module Reloading (HMR) support
- Secure access from any device
- Uses Bun for faster installs

Downside: It's not exposed locally on a port. It's only served to tailscale
