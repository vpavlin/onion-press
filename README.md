# onion-press
A simple Docker Compose to run Wordpress as an Onion Service

# Start

Start the Docker Compose as you are used to (via desktop or CLI)

```
docker compose up -d
```

Verify the Tor bootstrap is done

```
docker compose logs onionize | grep "Bootstrapped 100% (done): Done"
```

Get the Wordpress Onion hostname

```
docker exec onionize cat /var/lib/tor/onion_services/wordpress/hostname
```

When you access the returns Onion URL you should see a Wordpress initial setup page - you are done, you can start using Wordpress as usual.

# Components

This setup relies on [Onionize Docker](https://github.com/torservers/onionize-docker) which allows you to expose any running container on your system as an Onion Service.

Other components in the [docker-compose.yml](./docker-compose.yml) are Wordpress and MySQL services.