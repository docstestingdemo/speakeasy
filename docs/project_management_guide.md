# Project Management Guide for Speakeasy-based Projects

## Overview

This guide provides insights and best practices for managing projects that use Speakeasy to generate SDKs and other API-related artifacts.

## Key Considerations

1. OpenAPI Spec Management
   - Maintain a single source of truth for your OpenAPI specification
   - Use version control to track changes to the spec over time
   - Consider using Speakeasy's merge command to combine multiple spec files if needed

2. Workflow Configuration  
   - Define your generation targets in the .speakeasy/workflow.yaml file
   - Organize targets logically by language, purpose, etc.
   - Use consistent naming conventions for targets

3. CI/CD Integration
   - Set up automated SDK generation on spec changes using speakeasy run
   - Configure publishing of generated SDKs to package managers 
   - Use the --github flag for GitHub Actions integration

4. Version Management
   - Use semantic versioning for your SDKs
   - Leverage Speakeasy's automatic version bumping
   - Consider manual version control with --set-version for major releases

5. Quality Assurance
   - Regularly lint your OpenAPI spec (speakeasy lint openapi)
   - Validate generated SDKs compile successfully
   - Set up automated testing of SDKs

6. Documentation
   - Keep SDK READMEs up-to-date with latest changes
   - Provide code samples for key use cases
   - Consider generating standalone usage snippets (speakeasy generate usage)

7. Feedback Loop
   - Gather feedback from SDK consumers regularly
   - Use the Speakeasy web studio (--watch flag) to refine SDK quality

## Best Practices

- Run speakeasy status periodically to review workspace state
- Use speakeasy clean to remove stale artifacts 
- Leverage speakeasy suggest for automated spec improvements
- Consider using OpenAPI overlays for customizations

## Common Pitfalls to Avoid

- Forgetting to update the OpenAPI spec before regenerating SDKs
- Not testing SDKs across multiple language versions
- Neglecting to update documentation when API behavior changes

By following these guidelines, you can effectively manage Speakeasy-based projects and deliver high-quality SDKs to your API consumers.