# Advanced Usage

This guide covers advanced features and use cases for the Speakeasy CLI.

## Merging Multiple OpenAPI Specs

You can merge multiple OpenAPI specs into a single document using the `speakeasy merge` command:

```
speakeasy merge -s path/to/spec1.yaml -s path/to/spec2.yaml -o merged_spec.yaml
```

This is useful for combining specs from multiple services into a single SDK.

## Applying OpenAPI Overlays

OpenAPI overlays allow you to modify an existing spec without changing the original. You can apply an overlay using:

```
speakeasy overlay apply -s original_spec.yaml -o overlay.yaml --out modified_spec.yaml
```

## Generating Usage Snippets

To generate code snippets demonstrating SDK usage:

```
speakeasy generate usage -s openapi.yaml -l typescript -o snippets/
```

This will create usage examples for each operation in the spec.

## Customizing SDK Generation

The `gen.yaml` file allows extensive customization of SDK generation. Some advanced options include:

```yaml
go:
  version: 1.0.0
  packageName: mycompany/myapi
  installationURL: https://github.com/mycompany/go-sdk
  clientServerStatusCodesAsErrors: true
  flattenGlobalSecurity: true

global:
  generateExamples: true
  enforcePostHogAliasing: true
```

Refer to the [gen.yaml reference](https://speakeasy.com/docs/sdk-generation/configuration/gen-yaml) for all available options.

## Automating with GitHub Actions

You can automate SDK generation and publishing using GitHub Actions. Here's a sample workflow:

```yaml
name: Generate SDKs
on:
  push:
    branches: [main]
jobs:
  generate:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Install Speakeasy CLI
        run: curl -fsSL https://raw.githubusercontent.com/speakeasy-api/speakeasy/main/install.sh | sh
      - name: Generate SDK
        run: speakeasy run
      - name: Publish SDK
        run: |
          cd sdk
          npm publish
        env:
          NODE_AUTH_TOKEN: ${{ secrets.NPM_TOKEN }}
```

This will regenerate and publish your SDK on each push to main.

## Using the Web Studio

For interactive SDK customization, use the `--watch` flag:

```
speakeasy run --watch
```

This will open the Speakeasy Web Studio in your browser, allowing you to fine-tune generation settings and preview changes in real-time.