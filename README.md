# onion-press
A simple Docker Compose to run WordPress and Ghost as Onion Services

# Prerequisites

You will need [Docker](https://docs.docker.com/get-started/get-docker/) and [Docker Compose](https://docs.docker.com/compose/install/) installed

# Start

## Running all services

To run all services (WordPress, Ghost, and the onion service):

```
docker compose up -d
```

## Running only WordPress

To run only WordPress and the required services:

```
docker compose up -d wordpress
```

## Running only Ghost

To run only Ghost and the required services:

```
docker compose up -d ghost
```

## Verification

Verify the Tor bootstrap is done

```
docker compose logs onionize | grep "Bootstrapped 100% (done): Done"
```

Get the WordPress Onion hostname

```
docker exec onionize cat /var/lib/tor/onion_services/wordpress/hostname
```

Get the Ghost Onion hostname

```
docker exec onionize cat /var/lib/tor/onion_services/ghost/hostname
```

When you access the returned Onion URLs you should see:
- For WordPress: the WordPress initial setup page
- For Ghost: the Ghost initial setup page

You are done, you can start using both platforms as usual.

# Components

This setup relies on [Onionize Docker](https://github.com/torservers/onionize-docker) which allows you to expose any running container on your system as an Onion Service.

Other components in the [docker-compose.yml](./docker-compose.yml) are WordPress, Ghost, and MySQL services.