# cargo-publish

Runs `cargo publish`. If the version already exists on crates.io, skip
(can be disabled with `skip-existing: false`).

## Usage

```yaml
- uses: franciscoabsampaio/cargo-publish@main
  with:
    registry-token: ${{ secrets.CARGO_REGISTRY_TOKEN }}
    crate-name: my-crate
    crate-version: 1.2.3
```

## Inputs

| Input            | Required | Default | Description                                                                 |
| ---------------- | :------: | :-----: | --------------------------------------------------------------------------- |
| `registry-token` | yes      |         | The Cargo registry token (e.g. `${{ secrets.CARGO_REGISTRY_TOKEN }}`).      |
| `crate-name`     | yes      |         | Crate name, used for the crates.io existence check.                         |
| `crate-version`  | yes      |         | Crate version, used for the crates.io existence check.                      |
| `skip-existing`  |          | `true`  | If `true`, skip publish when the version already exists on crates.io.       |
| `manifest-path`  |          | `''`    | Path to the crate's `Cargo.toml`, relative to the caller's repo root. Use when the crate is not at the repo root (e.g. a workspace member). Forwarded to `cargo publish --manifest-path`. |

## Example — workspace member

```yaml
- uses: franciscoabsampaio/cargo-publish@main
  with:
    registry-token: ${{ secrets.CARGO_REGISTRY_TOKEN }}
    crate-name: my-macros
    crate-version: 0.1.0
    manifest-path: crates/my-macros/Cargo.toml
```
