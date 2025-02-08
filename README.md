# local-llm-obsidian-knowledge-base

A template repository that includes a dev container for running a local LLM and included knowledge base. Add a git repo using `git subtree` or `git submodule` and update it using an MCP Client/Server relationship i.e. `VS Code` extension like `Cline` and the `Filesystem`/`Obsidian-MCP` MCP server.

## Local setup

### Devcontainer

Oven in an IDE that supports Devcontainers.

### Manual setup

NOTE: You can use the below steps, or run the compose file as a part of a dev container.
Run this command to create the containers:
```
sudo docker compose --env-file ./generated.env up -d --no-deps --build
```
