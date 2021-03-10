# remote-lights-docker

Docker compose configuration for remote lights project.

## remote-lights command:

cli interface for launching project

### Container Launching Options:

up            remote-lights [container options] [--mode] up
init          remote-lights init
build         remote-lights [container options] [--mode] [--push] build
registry-up   remote-lights registry-up

### Container Options:

-w            Launches web container.
-r            Launches redis container.
-s            Launches socket container.

ex: remote-lights -ws to launch web & socket container in development

### Additional flags

--mode        sets mode for containers and cli. options: production|development
--push        used by build command to push to local repository

## Initial Setup:

Make `setup` and `remote-lights` executable:

`chmod +x setup`

`chmod +x remote-lights`

Initialize env files:

`remote-lights init`

Run `setup` to allow docker to connect to the repository:

`sudo setup`

