# Docker OpenResty OpenID-Connect

This repository contains the Docker build for OpenResty with the `lua-resty-openidc` library. `lua-resty-openidc` is a library for Nginx that allows it to perform OpenID Connect (OIDC) authentication.

This Docker image can be used as a reverse proxy to protect your applications with OIDC authentication.

## Included Software

The Docker image is based on Alpine Linux and includes the following software:

-   OpenResty 1.21.4.1
-   LuaJIT 2.1
-   `lua-resty-openidc` 1.7.2-1
-   `dnsmasq`

## Getting Started

### Prerequisites

-   Docker must be installed on your system.

### Building the Image

To build the Docker image, you can use the provided `build.sh` script:

```bash
./build.sh
```

This will build the image with the tag `local/docker-openresty-openidc`.

### Running the Container

To run the container for testing or debugging purposes, you can use the `run.sh` script:

```bash
./run.sh
```

This will start the container in interactive mode and remove it when you exit.

For a production deployment, you will need to run the container in detached mode and map the necessary ports and volumes. For example:

```bash
docker run -d \
    --name my-openresty-oidc \
    -p 80:80 -p 443:443 \
    -v /path/to/your/nginx.conf:/opt/openresty/nginx/conf/nginx.conf \
    local/docker-openresty-openidc
```

## Configuration

This Docker image provides the necessary software, but you will need to configure OpenResty and `lua-resty-openidc` to suit your needs. This involves setting up your OIDC provider, configuring the redirect URI, and defining your authentication and authorization rules.

For more information on how to configure `lua-resty-openidc`, please refer to the official documentation: [https://github.com/zmartzone/lua-resty-openidc](https://github.com/zmartzone/lua-resty-openidc)

## Helper Scripts

This repository includes the following helper scripts:

-   `common.sh`: Defines common variables used by the other scripts.
-   `build.sh`: Builds the Docker image.
-   `run.sh`: Runs the container in interactive mode for testing.
-   `push-to-remote-registries.sh`: Pushes the Docker image to one or more remote registries.

## License

This project is licensed under the terms of the LICENSE file.
