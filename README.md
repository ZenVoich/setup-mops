# Setup Mops GitHub Action

Easy way to install [Mops](https://mops.one) in your GitHub Actions workflow.

This action provides caching of Mops packages and toolchain.

## Usage

Add the following step to your workflow to install Mops

```yaml
- uses: ZenVoich/setup-mops@v1
```

### Example

```yaml
jobs:
  your-job:
    runs-on: ubuntu-latest
    steps:
      - name: Install mops
        uses: ZenVoich/setup-mops@v1
```

### Specifying a mops version

```yaml
steps:
  - uses: ZenVoich/setup-mops@v1
    with:
      mops-version: 1
```

__Will install latest version of mops `1.x.x`.__

### Publish a package

Learn how to use GitHub Secrets [here](https://docs.github.com/en/actions/security-guides/using-secrets-in-github-actions?tool=webui).

This example publishes a package to the Mops Registry when a GitHub release is created.

```yaml
on:
  release:
    types: [released]
jobs:
  publish:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: ZenVoich/setup-mops@v1
        with:
          identity-pem: ${{ secrets.MOPS_IDENTITY_PEM }}
      - name: Publish to the Mops Registry
        run: mops publish
```

## Inputs

| Input               | Default
|---------------------|---------------|
| `mops-version`      | `latest`
| `moc-version`       | as specified in `mops.toml`
| `wasmtime-version`  | as specified in `mops.toml`
| `pocket-ic-version` | as specified in `mops.toml`
| `identity-pem`      |               |