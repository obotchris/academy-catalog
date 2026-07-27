# academy-catalog

An [Obot](https://obot.ai) MCP catalog for the Academy demos. Each top-level
`*.yaml` file is a catalog entry describing an MCP server that a user can add as a
source and use through an Obot gateway.

The entry format mirrors the
[obot-platform/mcp-catalog](https://github.com/obot-platform/mcp-catalog).

## Entries

| Entry | Description |
|-------|-------------|
| [`synthetic-pii.yaml`](./synthetic-pii.yaml) | Serves entirely fake customer PII (names, emails, US driver's license numbers) — a demo target for showing PII filtering / redaction. |

## Using this catalog with an Obot gateway

Point your Obot installation at this repository as a catalog source, e.g.:

```
https://github.com/obotchris/academy-catalog
```

Obot reads each `*.yaml` entry and makes the described MCP servers available to
add as sources. Select **Synthetic PII**, and the gateway will connect to the
server at the URL defined in the entry's `remoteConfig.fixedURL`.

## Entry format

Each entry is a single YAML file. Key fields:

| Field | Purpose |
|-------|---------|
| `name` | Display name shown in the catalog |
| `entryKey` | Unique, stable identifier for the entry |
| `serverUserType` | `singleUser` or `multiUser` |
| `shortDescription` / `description` | Summary and full (markdown) description |
| `metadata.categories` | Category used for grouping/filtering |
| `icon` | Icon URL |
| `repoURL` | Source repository for the server |
| `runtime` | `remote` for a hosted HTTP MCP server |
| `remoteConfig.fixedURL` | The streamable-HTTP endpoint the gateway connects to |
| `env` | Configurable environment variables (empty if none) |
| `toolPreview` | Preview of the tools the server exposes |

See [`synthetic-pii.yaml`](./synthetic-pii.yaml) for a complete example.
