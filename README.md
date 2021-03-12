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

`sudo setup`

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
`
[registry."192.168.0.2:5001"]
  http = true
  insecure = true
`
Switch to builder:

`docker buildx use <builder-name>`

Ensures that the builder is running before inspecting it. If the driver is docker-container , then --bootstrap starts the buildkit container and waits until it is operational:

`docker buildx inspect --bootstrap`

Switch back to default builder:

`docker buildx use default`

## Pi Setup:

[Linux udev rules for teensy](https://www.pjrc.com/teensy/00-teensy.rules)





