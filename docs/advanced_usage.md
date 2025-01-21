# Advanced Usage

This document covers advanced features and use cases for the Speakeasy CLI.

## Working with Multiple OpenAPI Specs

The `speakeasy merge` command allows you to combine multiple OpenAPI documents into a single spec:

```
speakeasy merge -s path/to/spec1.yaml -s path/to/spec2.yaml -o merged_spec.yaml
```

This is useful for creating a unified API spec from multiple services or versions.

## Custom OpenAPI Transformations

The `speakeasy openapi transform` commands provide ways to modify OpenAPI specs:

- `cleanup` - Format and clean up a spec
- `filter-operations` - Keep or remove specific operations
- `remove-unused` - Remove unused components

For example:

```
speakeasy openapi transform filter-operations -s input.yaml --operations getUser,createUser -o filtered.yaml
```

## Working with Overlays

OpenAPI overlays allow you to extend and modify specs:

- `speakeasy overlay apply` - Apply an overlay to a base spec
- `speakeasy overlay compare` - Generate an overlay from two specs
- `speakeasy overlay validate` - Validate an overlay file

Example usage:

```
speakeasy overlay apply -s base.yaml -o overlay.yaml --out extended.yaml
```

## Advanced SDK Generation

Some advanced options for SDK generation include:

- `--debug` - Output debug files for troubleshooting
- `--skip-compile` - Skip compilation step
- `--skip-versioning` - Don't auto-increment versions
- `--set-version` - Manually set the SDK version

Example:

```
speakeasy run --target go --debug --skip-compile --set-version 1.2.3
```

## Using the Web Studio

The `--watch` flag opens the Speakeasy Web Studio for interactive SDK refinement:

```
speakeasy run --watch
```

This provides a visual interface for improving SDK quality and customization.

## Automated Workflows

The `speakeasy run` command can be used in CI/CD pipelines:

```
speakeasy run --github --minimal --skip-compile
```

This runs generations triggered by GitHub actions in a minimal way suited for automation.