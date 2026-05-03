# perspective-cuts-build

Build-only release repository for [taylorarndt/perspective-cuts](https://github.com/taylorarndt/perspective-cuts).

This repository does not maintain a fork of the source code. GitHub Actions checks the latest upstream release once per day, builds native macOS binaries on GitHub-hosted Intel and Apple Silicon runners when a matching local release is missing, and publishes release assets that mise can install via the GitHub backend.

## Install with mise

```sh
mise use -g github:webkaz/perspective-cuts-build@latest
```

or pin a version:

```sh
mise use -g github:webkaz/perspective-cuts-build@0.2.0
```

The release assets are named for mise autodetection:

- `perspective-cuts-<version>-macos-x64.tar.gz`
- `perspective-cuts-<version>-macos-arm64.tar.gz`

Each archive contains:

```text
bin/perspective-cuts
share/doc/perspective-cuts/
```

## Release

Releases are versioned to match upstream `taylorarndt/perspective-cuts` releases.

The `Release` workflow runs daily and can also be run manually:

1. Leave `upstream_tag` empty to build the latest upstream release, or set a tag such as `v0.2.0`.
2. Confirm the `Release` workflow succeeds on both `macos-15-intel` and `macos-15`.
3. Confirm the GitHub release contains both macOS archives and `checksums.txt`.

The local workflow intentionally does not build or test the Swift package. Build verification is performed on GitHub Actions only.

## Upstream

- Repository: `https://github.com/taylorarndt/perspective-cuts`
- Version source: upstream GitHub releases
