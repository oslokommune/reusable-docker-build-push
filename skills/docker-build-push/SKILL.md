---
description: Reusable GitHub Actions workflow for building and pushing Docker images to AWS ECR or GitHub Container Registry (GHCR). Supports build caching for Maven, Gradle, npm, pip, and Go.
user_invocable: true
---

# Docker Build and Push Workflow

This skill provides guidance on using the `reusable-docker-build-push` workflow for building and pushing Docker images in GitHub Actions.

## When to Use This Skill

Use this skill when:
- Setting up CI/CD pipelines that build Docker images
- Configuring Docker image builds for AWS ECR or GitHub Container Registry
- Implementing build caching strategies for faster builds
- Troubleshooting Docker build workflows

## Workflow Overview

The workflow provides:
- **Multi-registry support**: Push to AWS ECR, GHCR, or both
- **Build caching**: GitHub Actions cache integration for faster builds
- **Dependency caching**: Maven, Gradle, npm, pip, and Go cache support
- **OIDC authentication**: Secure AWS authentication without long-lived credentials
- **Automatic tagging**: SHA-based, semantic version, and custom tag rules
- **SBOM and provenance**: Optional security attestations
- **Artifact support**: Download artifacts from previous workflow jobs

## Quick Start

```yaml
jobs:
  build:
    uses: oslokommune/reusable-docker-build-push/.github/workflows/reusable-docker-build-push.yml@v4
    with:
      aws_ecr_push: true
    secrets:
      AWS_ROLE_ARN: ${{ secrets.AWS_ROLE_ARN }}
```

## Key Configuration Options

### Registry Configuration
- `aws_ecr_login` / `aws_ecr_push`: Enable ECR authentication and push
- `ghcr_login` / `ghcr_push`: Enable GHCR authentication and push
- `ecr_repository_name`: Custom ECR repository name (defaults to repo name)
- `ghcr_image_name`: Custom GHCR image name

### Build Configuration
- `context`: Docker build context path (default: `.`)
- `file`: Dockerfile path relative to context
- `platforms`: Target platforms (default: `linux/amd64`)
- `build_args`: Additional build arguments
- `sbom` / `provenance`: Enable security attestations

### Caching
- `maven_cache`: Enable Maven dependency caching
- `gradle_cache`: Enable Gradle dependency caching
- `npm_cache`: Enable npm dependency caching
- `pip_cache`: Enable pip dependency caching
- `go_cache`: Enable Go module caching

## Outputs

- `image_version`: The image version tag
- `image_tags`: All tags applied to the image
- `image_id`: Local image ID hash
- `image_digest`: Docker manifest hash

## Read More

- [reference.md](./reference.md) - Complete input/output reference
- [examples.md](./examples.md) - Common usage patterns
