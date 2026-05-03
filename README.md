# perspective-cuts-build

Build-only release repository for [taylorarndt/perspective-cuts](https://github.com/taylorarndt/perspective-cuts).

This repository does not maintain a fork of the source code. GitHub Actions clones the pinned upstream revision, builds native macOS binaries on GitHub-hosted Intel and Apple Silicon runners, and publishes release assets that mise can install via the GitHub backend.

## Install with mise

```sh
mise use -g github:webkaz/perspective-cuts-build@latest
```

or pin a version:

```sh
mise use -g github:webkaz/perspective-cuts-build@0.1.0
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

1. Update `UPSTREAM_REF` in `.github/workflows/release.yml` if the upstream source revision changes.
2. Push a tag such as `v0.1.0`.
3. Confirm the `Release` workflow succeeds on both `macos-15-intel` and `macos-15`.
4. Confirm the GitHub release contains both macOS archives and `checksums.txt`.

The local workflow intentionally does not build or test the Swift package. Build verification is performed on GitHub Actions only.

## Upstream

- Repository: `https://github.com/taylorarndt/perspective-cuts`
- Pinned revision: `fdfadd8d5fc065114f4350f26e28f4443ddb7932`
