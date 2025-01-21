# lint  
`speakeasy openapi lint`  


Lint an OpenAPI document  

## Details

# Lint 
## OpenAPI

Validates an OpenAPI document is valid and conforms to the Speakeasy OpenAPI specification. The linting process checks for structural integrity, semantic correctness, and adherence to best practices.

## Usage

```
speakeasy openapi lint [flags]
```

### Options

```
  -H, --header string                 header key to use if authentication is required for downloading schema from remote URL
  -h, --help                          help for lint
      --max-validation-errors int     limit the number of errors to output (default 1000, 0 = no limit) (default 1000)
      --max-validation-warnings int   limit the number of warnings to output (default 1000, 0 = no limit) (default 1000)
  -r, --ruleset string                ruleset to use for linting (default "speakeasy-recommended")
  -s, --schema string                 local filepath or URL for the OpenAPI schema
      --token string                  token value to use if authentication is required for downloading schema from remote URL
```

### Options inherited from parent commands

```
      --logLevel string   the log level (available options: [info, warn, error]) (default "info")
```

### Parent Command

* [speakeasy openapi](README.md)	 - Utilities for working with OpenAPI documents

### Additional Information

The lint command is essential for maintaining high-quality OpenAPI documents. It helps identify issues such as:

- Structural errors in the JSON or YAML format
- Semantic inconsistencies within the API definition
- Deviations from OpenAPI specification standards
- Potential security vulnerabilities
- Naming convention violations

By running the lint command regularly during API development, you can catch and fix issues early, ensuring a more robust and reliable API documentation.