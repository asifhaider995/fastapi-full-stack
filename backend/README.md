# Backend

## Installation

### Database

```
docker run --name postgres -e POSTGRES_PASSWORD=postgres -e POSTGRES_USER=postgres -d postgres
# Check container status
docker ps | grep postgres
# Create Database
docker exec -it postgres bash
apt update
su - postgres
psql
CREATE DATABASE fastapi;
GRANT ALL PRIVILEGES ON DATABASE fastapi TO postgres;
```

### Migrating models
```
alembic init alembic
# Config alembic.ini and alembic/env.py
alembic revision --autogenerate -m "initial migration"

```

```
from app.database import Base
from app import models
...
target_metadata = Base.metadata

```

```
alembic upgrade head
```