# Package dependency graph (HTTP MCP)

`@kjerneverk/riotplan-mcp-http` **depends** on `@kjerneverk/riotplan` in `dependencies`. The framework package does **not** depend on this HTTP package, so there is no npm dependency cycle.

- **Dependencies** — `@kjerneverk/riotplan` (framework entry: plan loaders, step ops, status generator, etc.), plus leaf-ish packages such as `@kjerneverk/riotplan-core`, `@kjerneverk/riotplan-format`, `@kjerneverk/riotplan-catalyst`, `@kjerneverk/riotplan-cloud`, `@kjerneverk/riotplan-ai`, and transport/logging stacks.

**Publish order**: publish `@kjerneverk/riotplan` before (or concurrently with) a `@kjerneverk/riotplan-mcp-http` release that bumps its `riotplan` range. Consumers who install only `@kjerneverk/riotplan-mcp-http` get `riotplan` transitively.

**Future** — migrate remaining `@kjerneverk/riotplan` imports into `riotplan-core` (or smaller packages) if you want the HTTP server to depend on a thinner surface.

**Local development** — `tsc` needs a built `@kjerneverk/riotplan` whose `dist/` matches the workspace. After `npm run build` in `riotplan-core` and `riotplan`, run `npm link` in each and `npm link @kjerneverk/riotplan` inside `riotplan-mcp-http`, or use your monorepo’s workspace install.

**Registry** — plain `npm install` resolves `@kjerneverk/riotplan` from the registry per the semver range in `riotplan-mcp-http/package.json`.
