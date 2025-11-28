# Chatwoot Docker Deployment

This repository contains the configuration to deploy Chatwoot using Docker Compose. It uses the official `chatwoot/chatwoot:latest` image and includes a custom Nginx configuration for branding injection.

## Prerequisites

- Docker
- Docker Compose

## Setup & Running

1.  **Configure Environment Variables**

    Copy the example environment file to `.env`:

    ```bash
    cp .env.example .env
    ```

    > **Important:** The `.env.example` file has been updated with critical configurations (`ACTIVE_STORAGE_SERVICE=local`, `POSTGRES_PASSWORD`, etc.). Ensure your `.env` matches these values.

2.  **Start the Application**

    Run the following command to start all services:

    ```bash
    docker-compose up -d
    ```

3.  **Access the Application**

    The application will be available at: `http://localhost:80`

    The Nginx proxy handles the CSS injection for the "RideCare" branding.

## Troubleshooting

-   **Database Errors:** If you see database connection errors, ensure the `POSTGRES_PASSWORD` in `.env` matches the one in `docker-compose.yml` (default: `postgres`).
-   **Missing App/Assets:** The application runs inside the Docker container. Source code is not present in this repo, only the deployment configuration.
-   **Rails Errors:** If you see `eager_load` or `Active Storage` errors, ensure you have updated your `.env` file from the latest `.env.example`.

## Customization

-   **Branding:** Custom CSS is located in `nginx/css/ridecare.css`.
-   **Nginx:** Configuration is in `nginx/nginx.conf`.
