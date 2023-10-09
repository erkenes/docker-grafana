# Grafana behind Traefik Proxy

This repository provides instructions and configurations for running Grafana behind a Traefik proxy.

## Prerequisites

Before you begin, ensure you have the following prerequisites installed and set up:

- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)
- [Traefik](https://github.com/erkenes/docker-traefik)

## Installation

1. Clone this repository to your server:

    ```shell
    git clone https://github.com/erkenes/docker-grafana.git
    cd docker-grafana
    ```

2. Create a `.env` file and configure your settings. You can use the provided `.env.example`
   ```shell
   cp .env.example .env
   nano .env
   ```

3. (optional) if you want to secure Node-RED with [Authentik](https://github.com/erkenes/docker-authentik), uncomment the middleware line in the `docker-compose.yml` file
   ```yaml
   services:
     grafana:
       labels:
         - 'traefik.http.routers.${PROJECT_IDENTIFIER}.middlewares=middlewares-authentik@file'
   ```

4. Start Grafana
   ```shell
   docker compose up -d
   ```

## Configuration

- `.env` - This file contains the environment variables for the Grafana container. You can change the domain for Grafana by changing the `GRAFANA_FQDN` variable.

## Troubleshooting

If you encounter issues or have questions, please open an issue or refer to the official documentation for [Grafana](https://grafana.com/docs/grafana/latest/).

## License

This project is licensed under the [MIT License](LICENSE).

## Contributing

Contributions are welcome! If you have any improvements, bug fixes, or feature requests, please open an issue or submit a pull request.
