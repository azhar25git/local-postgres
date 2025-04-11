
---

# 🐘 PostgreSQL Dev Environment with Docker Compose

This project sets up a local PostgreSQL 16 development environment using Docker Compose.

## 📦 Services

### `postgres`
- **Image**: `postgres:16`
- **Container Name**: `pg-dev`
- **Restart Policy**: `unless-stopped`
- **Environment Variables**:
  - `POSTGRES_USER`: `devuser`
  - `POSTGRES_PASSWORD`: `devpass`
  - `POSTGRES_DB`: `devdb`
- **Port Mapping**: 
  - `127.0.0.1:5432 -> 5432` (localhost only)
- **Volume**:
  - `pgdata:/var/lib/postgresql/data` (persistent data storage)

## 🚀 Getting Started

### Prerequisites
- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/) (comes with Docker Desktop)

### Running the PostgreSQL Container

1. **Start the service**:
   ```bash
   docker-compose up -d
   ```

2. **Stop the service**:
   ```bash
   docker-compose down
   ```

3. **Stop and remove everything (including the volume)**:
   ```bash
   docker-compose down -v
   ```

### Connecting to PostgreSQL

You can connect to the database using any PostgreSQL client (e.g., `psql`, DBeaver, TablePlus) with the following credentials:

- **Host**: `127.0.0.1`
- **Port**: `5432`
- **User**: `devuser`
- **Password**: `devpass`
- **Database**: `devdb`

> **Note**: This setup binds PostgreSQL only to `localhost` for development safety.

## 📁 Volumes

- `pgdata`: Persists PostgreSQL data between container restarts.

## 🧹 Cleanup

To remove all data (be careful!):

```bash
docker volume rm <project-name>_pgdata
```

Or let Docker Compose do it:

```bash
docker-compose down -v
```
