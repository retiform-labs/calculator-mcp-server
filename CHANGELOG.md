# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.4] - 2026-10-28

### Fixed

- README and the `bin/` header comment documented `npx calculator-mcp-server`
  (**unscoped**), which resolves on npm to an unrelated package by a different
  author. All five occurrences now read `npx -y @retiform/calculator-mcp-server`.
  The repo fix alone would not have reached users: npm serves its own frozen
  copy of the README, so a patch release is the only way to replace the 1.0.3
  registry page.

## [1.0.3] - 2026-10-28

### Changed

- Migrate from the deprecated `@sagelabs/mcp-ai` to `@retiform/mcp-ai@^1.9.1`.
  The `simple-server` API is unchanged, so only the scope moves. Installers no
  longer receive a deprecation warning.

### Fixed

- `FUNDING.yml` pointed at `github.com/sagelabs-dev/...`, which 404s after the
  org rename. Now targets `retiform-labs`.

## [1.0.0] - 2026-09-13

### Added
- Initial release: 13 MCP tools for agentic mathematics.
  - Core evaluation: `calculate` (sandboxed, AST-audited expression
    evaluation with scope support and typed results).
  - Symbolic calculus: `derivative`, `simplify`, `solve` (exact
    linear/quadratic + numeric general fallback), `integral` (exact
    polynomial + adaptive Simpson), `symbolic_integral` (self-checked
    polynomial antiderivatives).
  - Statistics: `stats_describe`, `stats_correlation`,
    `stats_regression`, `stats_confidence_interval` (t-quantile verified
    against R reference values).
  - Matrices: `matrix_add`, `matrix_multiply`, `matrix_transpose`
    (JSON-native nested arrays).
- Transports: stdio, HTTP, SSE with config precedence
  (defaults ← JSON5 file ← env).
- Security: AST symbol allowlist, host-symbol blocklist (all modes),
  assignment rejection, sandboxed namespace stubs, DoS bounds,
  escape-vector test suite.
- Tests: 169 (unit + e2e over raw stdio wire and HTTP SDK round-trip).
