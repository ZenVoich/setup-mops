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
      mops-version: 0.34.0
```

## Inputs

| Input               | Default
|---------------------|---------------|
| `mops-version`      | `latest`
| `moc-version`       | as specified in `mops.toml`
| `wasmtime-version`  | as specified in `mops.toml`
| `pocket-ic-version` | as specified in `mops.toml`