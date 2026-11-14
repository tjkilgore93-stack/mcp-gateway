# Secure MCP server starter: bearer auth + Postgres RLS + Docker

Forked from [docker/mcp-gateway](https://github.com/docker/mcp-gateway) with the goal of turning it into a zero-trust MCP server starter kit.

## What's here today

A fork of Docker's `mcp-gateway`. The upstream repo is the CLI plugin behind Docker Desktop's MCP Toolkit and the MCP Gateway that runs MCP servers in isolated containers. I haven't added zero-trust code yet — every file here is upstream Docker code, with a fresh commit that only adds a Docker image CI workflow.

- **Language:** Go, with some Dockerfile and Clojure
- **Entry point:** `cmd/docker-mcp`
- **License:** MIT (upstream, Copyright (c) 2025 Docker)
- **Upstream:** [docker/mcp-gateway](https://github.com/docker/mcp-gateway)
- **Fork created:** October 15, 2026

## Roadmap

The goal is a starter kit that ships with:

- **Bearer token auth** in front of the gateway
- **Postgres row-level security (RLS)** so each client only sees its own rows
- **`docker compose up` quickstart** — working endpoint in under a minute

Nothing in that list exists yet. I'll build it against this base and update the README as it lands.

## Running what exists

Everything below is the upstream flow, unchanged.

### Install as a Docker CLI plugin

```bash
git clone https://github.com/tjkilgore93-stack/mcp-gateway.git
cd mcp-gateway
mkdir -p "$HOME/.docker/cli-plugins/"
make docker-mcp

docker mcp --help
```

Prerequisites: Docker Desktop 4.59+ (with MCP Toolkit enabled), or Go 1.24+ for development.

### Notes from upstream

- If Docker Desktop is running but you get "Docker Desktop is not running", set `DOCKER_MCP_IN_CONTAINER=1`. Useful for Docker CE, WSL2, and containerized environments.
- Enable profiles before using them outside Docker Desktop:

```bash
docker mcp feature enable profiles
```

## Upstream docs

The full feature set lives upstream:

- [Docker MCP Toolkit](https://docs.docker.com/ai/mcp-catalog-and-toolkit/toolkit/)
- [Docker MCP Catalog](https://hub.docker.com/mcp)
- [docker/mcp-gateway](https://github.com/docker/mcp-gateway) — original README and docs

## Contributing

This is a personal fork. The upstream contribution guide is [CONTRIBUTING.md](CONTRIBUTING.md).

## License

MIT. See [LICENSE](LICENSE). Original copyright (c) 2025 Docker. Any changes in this fork follow the same terms.
