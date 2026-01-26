# Docker Build and Push Workflow Reference

Complete reference for all inputs, outputs, and secrets.

## Secrets

| Secret | Required | Description |
|--------|----------|-------------|
| `AWS_ROLE_ARN` | No | AWS role ARN for OIDC authentication to ECR |
| `DOCKER_SECRETS` | No | Secrets to expose to Docker build (e.g., `key=string`) |

## Inputs

### Environment & Runner

| Input | Type | Default | Description |
|-------|------|---------|-------------|
| `environment` | string | - | GitHub deployment environment to use |
| `runner` | string | `ubuntu-latest` | Runner to use for the job |
| `git_ref` | string | trigger SHA | Branch, tag, or SHA to checkout |

### AWS Configuration

| Input | Type | Default | Description |
|-------|------|---------|-------------|
| `region` | string | `eu-west-1` | AWS region |
| `role_session_name` | string | repo name | AWS role session name |
| `aws_ecr_login` | boolean | `true` | Login to AWS ECR |
| `aws_ecr_push` | boolean | `false` | Push image to ECR |
| `ecr_repository_name` | string | repo name | ECR repository name |

### GHCR Configuration

| Input | Type | Default | Description |
|-------|------|---------|-------------|
| `ghcr_login` | boolean | `false` | Login to GitHub Container Registry |
| `ghcr_push` | boolean | `false` | Push image to GHCR |
| `ghcr_image_name` | string | repo name | GHCR image name |

### Docker Build Configuration

| Input | Type | Default | Description |
|-------|------|---------|-------------|
| `context` | string | `.` | Docker build context path |
| `file` | string | `Dockerfile` | Dockerfile path relative to context |
| `platforms` | string | `linux/amd64` | Target platforms (e.g., `linux/amd64,linux/arm64`) |
| `build_args` | string | - | Additional build arguments |
| `sbom` | boolean | `false` | Generate SBOM attestation |
| `provenance` | boolean | `false` | Generate provenance attestation |

### Tagging Configuration

| Input | Type | Default | Description |
|-------|------|---------|-------------|
| `tag_rules` | string | see below | Docker metadata tag rules |
| `tag_flavor` | string | `latest=auto` | Docker metadata flavor config |

Default `tag_rules`:
```yaml
type=sha,format=long,priority=1100
type=sha,prefix=
type=raw,value=gha-${{ github.run_id }}
type=semver,pattern={{version}}
```

### Artifact Configuration

| Input | Type | Default | Description |
|-------|------|---------|-------------|
| `download_artifact` | boolean | `false` | Download artifacts from previous jobs |
| `download_artifact_name` | string | - | Specific artifact name to download |
| `download_artifact_path` | string | - | Path to extract artifacts to |

### Dependency Cache Configuration

#### Maven
| Input | Type | Default | Description |
|-------|------|---------|-------------|
| `maven_cache` | boolean | `false` | Enable Maven cache |
| `maven_build_file_pattern` | string | `**/pom.xml` | Glob pattern for Maven build file |

#### Gradle
| Input | Type | Default | Description |
|-------|------|---------|-------------|
| `gradle_cache` | boolean | `false` | Enable Gradle cache |
| `gradle_build_file_pattern` | string | `**/build.gradle` | Glob pattern for Gradle build file |

#### npm
| Input | Type | Default | Description |
|-------|------|---------|-------------|
| `npm_cache` | boolean | `false` | Enable npm cache |
| `npm_package_file_pattern` | string | `**/package.json` | Glob pattern for package.json |

#### pip
| Input | Type | Default | Description |
|-------|------|---------|-------------|
| `pip_cache` | boolean | `false` | Enable pip cache |
| `pip_requirements_file_pattern` | string | `**/requirements.txt` | Glob pattern for requirements file |

#### Go
| Input | Type | Default | Description |
|-------|------|---------|-------------|
| `go_cache` | boolean | `false` | Enable Go cache |
| `go_mod_file_pattern` | string | `**/go.mod` | Glob pattern for go.mod file |

## Outputs

| Output | Description |
|--------|-------------|
| `image_version` | The image version tag (use to find image in registry) |
| `image_tags` | All tags applied to the image |
| `image_id` | Image ID (hash of local image JSON configuration) |
| `image_digest` | Image digest (hash of Docker manifest) |
| `docker_build_metadata` | Full Docker build metadata |

## Permissions Required

The workflow requires these permissions:
```yaml
permissions:
  id-token: write   # For OIDC authentication
  contents: read    # For checkout
  packages: write   # For GHCR push
```
