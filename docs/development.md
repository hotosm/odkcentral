# Development

## Using Containers

This guide if for users who wish to run ODK Central entirely within _containers_ during development (particularly those who run their coding environment within a container too).

### Set Up The Repos

1. Clone this [repo](https://github.com/getodk/central) for orchestrating the ODK Central components.

    ```bash
    git clone https://github.com/getodk/central.git
    cd central
    # Change to branch for next release
    git checkout next
    ```

2. Fork the [central-backend](https://github.com/getodk/central-backend/) and [central-frontend](https://github.com/getodk/central-frontend/) repos for development.

3. Update the submodules to point to your fork:

    ```bash
    nano .gitmodules
    ```

    - Change `[submodule "server"].url` to equal the fork URL for `central-backend`.
    - E.g. https://github.com/{YOUR_USER}/central-backend.git
    - Then change `[submodule "client"].url` to the fork URL for `central-frontend`.

4. Init the submodules:

    ```bash
    git submodule update --init
    ```

5. Change the submodule branch for development:

    ```bash
    # Backend
    cd server
    git checkout master
    git checkout -b fix/your-bug-fix

    # Frontend
    cd ../client
    git checkout master
    git checkout -b fix/your-bug-fix
    cd ..
    ```

6. Generate a `.env`:

    ```bash
    cp .env.template .env
    ```

7. Modify `.env` for development:

    ```dotenv
    SSL_TYPE=upstream
    HTTP_PORT=880
    HTTPS_PORT=8443
    ```

### Build the containers

```bash
docker compose -f docker-compose.dev.yml build
```

### 

> Note: the ODK Central frontend is also available to aid debugging:
>
> http://localhost:PORT

## Local Machine

The guide to run directly on your local machine is simple and is covered within the [README](https://github.com/getodk/central-backend/blob/master/README.md).

