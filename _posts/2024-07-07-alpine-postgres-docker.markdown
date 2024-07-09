---
layout: post
title:  "PostgreSQL Alpine 16 Docker Installation Guide"
date:   2024-07-07 08:39:12 +0530
categories: jekyll update
---

#### Quick Start

```bash
docker run --name postgres16 -e POSTGRES_PASSWORD=mysecretpassword -d postgres:16.3-alpine3.20
```

#### Detailed Steps

1. **Pull the image**:
   ```bash
   docker pull postgres:16.3-alpine3.20
   ```

2. **Run the container**:

   ```bash
   # When running the PostgreSQL container for the first time using Docker, 
   # you are required to set the environment variable POSTGRES_PASSWORD to your desired password for the PostgreSQL superuser.

   docker run --name postgres16 -e POSTGRES_PASSWORD=mysecretpassword -d postgres:16.3-alpine3.20
   ```
   - `docker run`: Command to create and start a new Docker container.
   - `--name postgres16`: Assigns a name (`postgres16`) to the container for easy reference.
   - `-e POSTGRES_PASSWORD=mysecretpassword`: Sets an environment variable `POSTGRES_PASSWORD` inside the container with the value `mysecretpassword`. This is required to          set the password for the PostgreSQL superuser.
   - `-d`: Runs the container in detached mode (in the background).

3. **Connect to the database**:
   ```bash
   docker exec -it postgres16 psql -U postgres
   ```

### Environment Variables

- `POSTGRES_PASSWORD`: Set the superuser password (required)
- `POSTGRES_USER`: Create a new superuser (default: postgres)
- `POSTGRES_DB`: Specify the name of the default database (default: POSTGRES_USER value)

### Persistence

Mount a volume for data persistence:

```bash
docker run --name postgres16 -e POSTGRES_PASSWORD=mysecretpassword -v /my/data:/var/lib/postgresql/data -d postgres:16-alpine
```

### Custom Configuration

Mount a custom `postgresql.conf`:

```bash
docker run --name postgres16 -e POSTGRES_PASSWORD=mysecretpassword -v /my/custom/postgresql.conf:/etc/postgresql/postgresql.conf -d postgres:16-alpine -c 'config_file=/etc/postgresql/postgresql.conf'
```

### Health Check

```bash
docker run --name postgres16 -e POSTGRES_PASSWORD=mysecretpassword -d --health-cmd="pg_isready -U postgres" --health-interval=10s --health-timeout=5s --health-retries=5 postgres:16-alpine
```
