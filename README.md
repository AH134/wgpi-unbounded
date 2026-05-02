# wgpi-unbounded

wgpi-unbounded is a docker compose project consisting of [WGDashboard](https://docs.wgdashboard.dev/), [Pi-Hole](https://docs.pi-hole.net/), and [Unbound](https://github.com/klutchell/unbound-docker). This project provides a baseline setup for the services to work together.

> **Note:** Please refer to the individual documentation for each service for more information on configuration and usage.

## Motivation

I created this project to replace my old setup of Pi-Hole and wg-easy, which the docs for it have not been updated in quite some time (last updated in 2024!). Since Pi-Hole v6 has been released, I decided to recreate my setup and try out WGDashboard and unbound.

## Quick Access

- [Quickstart](#quickstart)
- [Installation](INSTALL.md)
- [WIP](#wip)

## Pre-requisites

Before you begin, ensure you have the following:

- A Linux distribution (e.g., Ubuntu, Debian, etc.)
- [Docker](https://docs.docker.com/get-docker/)
- [WireGuard](https://www.wireguard.com/install/)

## Quickstart

To begin using wgpi-unbounded, clone the repository and start the containers:

```bash
# Clone the repository
git clone https://github.com/AH134/wgpi-unbounded.git

# Create a compose directory and move the compose.yaml and .env files
mkdir -p ~/compose/wgpi-unbounded
cp wgpi-unbounded/compose.yaml ~/compose/wgpi-unbounded/
cp wgpi-unbounded/env.example ~/compose/wgpi-unbounded/.env

# Change to the compose directory
cd ~/compose/wgpi-unbounded

# Update the .env file and compose.yaml with your configuration
# Use your favorite text editor to edit the files
vim ~/compose/wgpi-unbounded/.env
vim ~/compose/wgpi-unbounded/compose.yaml

# Start the containers
docker compose -f wgpi-unbounded/compose.yaml --env-file .env up -d
```

To change your public IP for WGDashboard, head to `Settings` > `Peers Settings` and change the `Peer Remote Endpoint` after initial setup.

## WIP
