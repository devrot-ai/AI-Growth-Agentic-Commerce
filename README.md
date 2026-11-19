# AI Growth Agentic Commerce

A shared set of rules and examples so AI agents, stores, and payment systems can talk to each other without confusion.

This is not a running app or a hosted service. It is a collection of schemas and API definitions that anyone can use to make sure their data matches up with everyone else.

## What You Get

JSON Schemas to check that your data is in the right format. OpenAPI files that describe the HTTP endpoints. OpenRPC files for RPC-style integrations. Example payloads you can look at to see what things should look like. And a validation script that makes sure everything stays in sync.

## How It Is Organized

The `spec/` folder has dated snapshots of the specification, like `2026-04-17/` for the latest release. Each snapshot contains JSON Schema, OpenAPI, and OpenRPC files. The `unreleased/` folder is where new work lives before it gets a release date.

The `examples/` folder has sample payloads that match each spec version.

The `scripts/` folder has a validation script you can run to check everything.

## Getting Started

You need Node.js 18 or newer and pnpm 9 or newer.

```sh
pnpm install
pnpm validate:all
```

That installs everything and runs the full check to make sure schemas, examples, and API definitions all line up.

## How to Use It

Pick a spec version and stick with it. Look at the examples to see what your data should look like. Validate your payloads against the JSON Schema before sending them. Then build your service around it. This repo does not run the service for you.

If you want to try features that are still being worked on, look in `spec/unreleased/` and `examples/unreleased/`.

## Useful Commands

```sh
pnpm validate:all          # check everything
pnpm validate:json-schema  # compile all JSON schemas
pnpm compile:schema        # compile unreleased schemas
pnpm validate:examples     # check examples
pnpm report:consistency    # run a consistency report
```

## Making Changes

If you change a schema, update the matching examples and run `pnpm validate:all` to make sure nothing broke. Put new work in the `unreleased/` folders until it is ready for a release.

## License

Apache License 2.0. See the LICENSE and NOTICE files for details.
