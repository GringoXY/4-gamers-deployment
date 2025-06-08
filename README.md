# 4-gamers-deployment

Contains deployment scripts related to Docker.

## Setup

Follow steps to prepare environment for deployment.

### GitHub Token

Using [GitHub CLI](https://cli.github.com/) create `.github_token` file via command:

```powershell
gh auth >> .github_token
```

> :warning: Make sure created file has `LF` endline encoding instead of `CRLF` as this causes errors during environment composition using docker!

### Environment variables

Copy file `.env-example` and name it `.env` so docker will automatically load them into context.

### Composes

- frontend - ui related services setup,
- backend - services that handles business logic,
- brokers - queue like services,
- configs - configuration files mapping,
- databases,
- networks - defined networks in the system,
- secrets - loads secret related files like `.github_token`,
- volumes - mounting data drives.

### Deployment

#### Build and run all

```powershell
docker compose up -d --build
```

#### Build and run specific service

```powershell
docker compose up -d --build ui
```

#### Restart container

```powershell
docker compose up -d ui --force-recreate
```
