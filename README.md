# AI Growth Agentic Commerce

Machine-readable contracts and examples for building agent-powered commerce integrations.

This repository is a developer toolkit, not a hosted API or checkout application. It gives an agent, merchant, payment provider, or integration team the shared schemas and API definitions needed to design, validate, and exchange commerce data consistently.

## What Is Included

- **JSON Schema**: Validates request, response, event, and reusable data-model payloads.
- **OpenAPI**: Describes the HTTP endpoints, operations, parameters, and security-related API surface.
- **OpenRPC**: Describes the MCP checkout tools for clients that use an RPC-style integration.
- **Examples**: Ready-to-study payloads covering checkout, carts, feeds, payments, authentication, orders, and extensions.
- **Validation tooling**: Checks that schemas, OpenAPI definitions, and examples remain consistent.

## Repository Layout

```text
spec/
	2025-09-29/       Versioned specification snapshot
	2025-12-12/       Versioned specification snapshot
	2026-01-16/       Versioned specification snapshot
	2026-01-30/       Versioned specification snapshot
	2026-04-17/       Latest released specification snapshot
	unreleased/       Current development schemas and API definitions

examples/
	<version>/         Examples matching the corresponding spec snapshot

scripts/
	validate-consistency.js
```

Each specification version is organized into format-specific directories:

```text
spec/<version>/json-schema/   JSON Schema files
spec/<version>/openapi/       OpenAPI YAML files
spec/<version>/openrpc/       OpenRPC JSON files
```

## Quick Start

### Requirements

- Node.js 18 or newer
- pnpm 9 or newer

Install the development dependencies:

```sh
pnpm install
```

Run the complete consistency check:

```sh
pnpm validate:all
```

Compile the unreleased JSON Schemas directly with AJV:

```sh
pnpm compile:schema
```

Validate all versioned JSON Schemas:

```sh
pnpm validate:json-schema
```

The validation script checks schema and OpenAPI alignment, example payloads, field types, required fields, prohibited models, descriptions, and inline examples.

## Using The Definitions

Use the latest released snapshot when building an integration:

- OpenAPI: [`spec/2026-04-17/openapi/`](spec/2026-04-17/openapi/)
- JSON Schema: [`spec/2026-04-17/json-schema/`](spec/2026-04-17/json-schema/)
- OpenRPC: [`spec/2026-04-17/openrpc/`](spec/2026-04-17/openrpc/)
- Examples: [`examples/2026-04-17/`](examples/2026-04-17/)

Use `spec/unreleased/` and `examples/unreleased/` only when intentionally targeting features that are still under development.

For a typical integration workflow:

1. Choose one specification version and use its schemas and API definitions together.
2. Select the API surface you need, such as checkout, delegate payment, feeds, carts, or orders.
3. Use the matching examples to understand the expected payload shape.
4. Validate your own payloads against the JSON Schemas before sending or accepting them.
5. Implement the HTTP or RPC service in your application; this repository does not run that service for you.

## Package Commands

| Command | Purpose |
| --- | --- |
| `pnpm validate:all` | Run the full consistency validator |
| `pnpm validate:json-schema` | Compile every JSON Schema |
| `pnpm compile:schema` | Compile unreleased JSON Schemas |
| `pnpm validate:examples` | Validate examples and consistency rules |
| `pnpm report:consistency` | Run the consistency report |

## Contributing Changes Locally

When changing a schema or API definition, update the corresponding examples and run:

```sh
pnpm validate:all
```

Keep released snapshots stable. Place ongoing schema work in `spec/unreleased/` and matching examples in `examples/unreleased/` until it is ready for a dated release snapshot.

## License

The specification material is distributed under the Apache License 2.0. See [`LICENSE`](LICENSE) and [`NOTICE`](NOTICE) for the applicable terms and attribution.
