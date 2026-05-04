# Installation

## Directories and Bind mounts

> **Note:** The following steps will assume the directories listed below.

Create the following directories for bind mounts (or however you want to organize them):

```bash
mkdir -p ~/appdata/wgpi-unbounded/{wgdashboard,etc-pihole,unbound}
```

> **Note:** After installation, some directories may be changed to root, however, you can change the ownership of the directories to your user and it should work fine.

To change the ownership of the directories, you can use the following command:

```bash
# Change ownership of the directories to your user
sudo chown -R $USER:$USER ~/appdata/wgpi-unbounded/wgdashboard
sudo chown -R $USER:$USER ~/appdata/wgpi-unbounded/etc-pihole
sudo chown -R $USER:$USER ~/appdata/wgpi-unbounded

# OR

# Change ownership of all files in the directories to your user
sudo chown -R $USER:$USER ~/appdata/wgpi-unbounded
```

## Cloning the Repository

Clone the repository:

```bash
git clone https://github.com/AH134/wgpi-unbounded.git
```

Create or move the `compose.yaml` and `.env` files to the compose directory:

```bash
mkdir -p ~/compose/wgpi-unbounded

cp wgpi-unbounded/compose.yaml ~/compose/wgpi-unbounded/
cp wgpi-unbounded/env.example ~/compose/wgpi-unbounded/.env
```

## Compose File

Most of the settings work out of the box. However, take a look in the compose.yaml to make sure the ports are not conlicting with any existing services.

## Environment Variables

There are 3 variables to set in the `.env` file:

```
ROOT_DIR=/mnt/storage/appdata/wgpi-unbounded
TZ=America/New_York

# Pihole
PIPASS=123
PIHOLE_PORT=80

# WGDashboard
WGD_PORT=10086
```

- `ROOT_DIR`: The root directory for the bind mounts. Which would be `~/appdata/wgpi-unbounded/` if you followed the directory structure above.
- `TZ`: The timezone for the containers. You can find a list of timezones [here](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).
- `PIPASS`: The password for Pi-Hole.
- `PIHOLE_PORT`: The Pi-Hole port. If you are running a reverse proxy, change the port to something like `8080`.
- `WGD_PORT`: The WGDashboard port.

### Starting the containers

Navigate to your compose directory:

```bash
cd ~/compose/wgpi-unbounded
```

Start up the containers:

```bash
docker compose -f wgpi-unbounded/compose.yaml --env-file .env up -d
```

If everything is setup correctly, you should be able to acces Pi-Hole at `<IP_ADDRESS>/admin` and WGDashboard at `<IP_ADDRESS>:10086`, assuming the ports have not changed.
