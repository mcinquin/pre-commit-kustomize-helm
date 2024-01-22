# pre-commit-kustomize-helm

pre-commit hook which runs kustomize build command to test your Kubernetes resources.

## Example of .pre-commit-config.yaml that verifies that 3 overlays are not broken

```yaml
repos:
- repo: https://github.com/pre-commit/pre-commit-hooks
  rev: v4.5.0
  hooks:
  - id: check-yaml
    args: [--allow-multiple-documents]
  - id: end-of-file-fixer
  - id: trailing-whitespace

- repo: https://github.com/mcinquin/pre-commit-kustomize-helm
  rev: v0.1.0
  hooks:
  - id: kustomize
    name: kustomize-development
    args: [overlays/development]
    verbose: false
  - id: kustomize
    name: kustomize-staging
    args: [overlays/staging]
    verbose: false
  - id: kustomize
    name: kustomize-production
    args: [overlays/production]
    verbose: false
```

## Next steps

 * Add Helm lint hook
 * Add Helm install hook
 * Add Helm template hook
