# phpdock

## Introduction

phpdock aims to simplify the process of creating a development environment.

**Usage Overview:**

1. Clone the repository:
    ```bash
    git clone https://github.com/chinayin/phpdock.git
    ```

2. Enter the directory:
    ```bash
    cp env-example .env
    ```

3. Run these containers:
    ```bash
    docker-compose up -d nginx memcached redis
    ```

4. Open your browser and visit localhost.

**Simplify operations with dock.sh:**

```bash
./dock

Available options:
   web   Starts docker-sync and runs docker compose for web services.
   up [services]         Starts docker-sync and runs docker compose.
   stop                  Stops containers and docker-sync.
   build [services]      Build docker compose.
   down                  Stop and remove containers, networks, images, and volumes and docker-sync.
   cli                   Opens bash on the php-cli with user.
   cli72                 Opens bash on the php-cli72 with user.
   install               Installs docker-sync and docker-compose gem on the host machine.
   sync                  Manually triggers the synchronization of files.
   clean                 Removes all files from docker-sync.

```

### Supported Containers

- nginx
- php-fpm
- php-cli
- redis
- memcached
- mysql
- mongo
- elasticsearch
- node
- java
