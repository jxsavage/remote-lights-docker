# remote-lights-docker

Docker compose configuration for remote lights project.

## remote-lights command:

cli interface for launching project

### Container Launching Arguments:

registry-up   remote-lights registry-up
up            remote-lights [container options] [--mode=] up
build         remote-lights [container options] [--mode=] build
buildx        remote-lights [container options] [--mode=] buildx
init          remote-lights init
help          Print this message.

### Container Options:

-w            Launches web container.
-r            Launches redis container.
-s            Launches socket container.

ex: remote-lights -ws to launch web & socket container in development

### Additional flags

--mode        sets mode for containers and cli. options: production|development default: development

## Initial Setup:

Make `setup` and `remote-lights` executable:

`chmod +x setup`

`chmod +x remote-lights`

Run `setup` to allow docker to connect to the repository:

`sudo ./setup`

## Encountering problems with emulation?

https://github.com/docker/buildx/issues/493#issuecomment-754834977

leading to:

https://github.com/tonistiigi/binfmt#installing-emulators

## Multi-arch support to run on Raspberry Pi

See https://github.com/docker/buildx

Check your current builders:

`docker buildx ls`

Create new docker builder:

`docker buildx create --name <builder-name> --config /path/to/config.toml`

config must contain if insecure:

`[registry."192.168.0.2:5001"]`

  `http = true`

  `insecure = true`

default location on Ubuntu `/etc/docker/daemon.json`
Switch to builder:

`docker buildx use <builder-name>`

Ensures that the builder is running before inspecting it. If the driver is docker-container , then --bootstrap starts the buildkit container and waits until it is operational:

`docker buildx inspect --bootstrap`

Switch back to default builder:

`docker buildx use default`

## Pi Setup:

### Add udev rules

[Linux udev rules for teensy](https://www.pjrc.com/teensy/00-teensy.rules)

### Install docker
[Install Docker Egine](https://docs.docker.com/engine/install/ubuntu/)

`curl -fsSL https://test.docker.com -o test-docker.sh`

`sudo sh test-docker.sh`

[Install Composer v2](https://docs.docker.com/compose/cli-command/#installing-compose-v2)

`curl -L https://raw.githubusercontent.com/docker/compose-cli/main/scripts/install/install_linux.sh | sh`

Find `docker compose` cli plugin @ 
https://github.com/docker/compose-cli/releases



Create the cli-plugins dir for docker:

`mkdir ~/.docker/cli-plugins`

`cd ~/.docker/cli-plugins`

Insert the link to the appropriate arch

`curl -fsSL https://github.com/docker/compose-cli/releases/download/v2.0.0-beta.4/docker-compose-linux-arm64 -o docker-compose`

Make Executable:

`sudo chmod +x ~/.docker/cli-plugins/docker-compose`







