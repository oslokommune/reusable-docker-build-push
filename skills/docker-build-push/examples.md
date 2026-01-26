# Docker Build and Push Examples

Common usage patterns for the reusable-docker-build-push workflow.

## Basic ECR Push

Build and push to AWS ECR:

```yaml
name: Build and Deploy

on:
  push:
    branches: [main]

jobs:
  build:
    uses: oslokommune/reusable-docker-build-push/.github/workflows/reusable-docker-build-push.yml@v4
    with:
      aws_ecr_push: true
    secrets:
      AWS_ROLE_ARN: ${{ secrets.AWS_ROLE_ARN }}
```

## GHCR Push

Build and push to GitHub Container Registry:

```yaml
jobs:
  build:
    uses: oslokommune/reusable-docker-build-push/.github/workflows/reusable-docker-build-push.yml@v4
    with:
      aws_ecr_login: false
      ghcr_login: true
      ghcr_push: true
```

## Multi-Registry Push

Push to both ECR and GHCR:

```yaml
jobs:
  build:
    uses: oslokommune/reusable-docker-build-push/.github/workflows/reusable-docker-build-push.yml@v4
    with:
      aws_ecr_push: true
      ghcr_login: true
      ghcr_push: true
    secrets:
      AWS_ROLE_ARN: ${{ secrets.AWS_ROLE_ARN }}
```

## Maven Project with Caching

Build a Java/Maven project with dependency caching:

```yaml
jobs:
  build:
    uses: oslokommune/reusable-docker-build-push/.github/workflows/reusable-docker-build-push.yml@v4
    with:
      aws_ecr_push: true
      maven_cache: true
    secrets:
      AWS_ROLE_ARN: ${{ secrets.AWS_ROLE_ARN }}
```

**Required Dockerfile modification** - Mount the cache in your RUN instruction:

```dockerfile
RUN --mount=type=cache,target=/root/.m2,id=maven-cache \
    mvn clean package -DskipTests
```

## Gradle Project with Caching

```yaml
jobs:
  build:
    uses: oslokommune/reusable-docker-build-push/.github/workflows/reusable-docker-build-push.yml@v4
    with:
      aws_ecr_push: true
      gradle_cache: true
    secrets:
      AWS_ROLE_ARN: ${{ secrets.AWS_ROLE_ARN }}
```

**Required Dockerfile modification**:

```dockerfile
RUN --mount=type=cache,target=/root/.gradle,id=gradle-cache \
    ./gradlew build -x test
```

## Node.js Project with npm Caching

```yaml
jobs:
  build:
    uses: oslokommune/reusable-docker-build-push/.github/workflows/reusable-docker-build-push.yml@v4
    with:
      aws_ecr_push: true
      npm_cache: true
    secrets:
      AWS_ROLE_ARN: ${{ secrets.AWS_ROLE_ARN }}
```

**Required Dockerfile modification**:

```dockerfile
RUN --mount=type=cache,target=/root/.npm,id=npm-cache \
    npm ci
```

## Python Project with pip Caching

```yaml
jobs:
  build:
    uses: oslokommune/reusable-docker-build-push/.github/workflows/reusable-docker-build-push.yml@v4
    with:
      aws_ecr_push: true
      pip_cache: true
    secrets:
      AWS_ROLE_ARN: ${{ secrets.AWS_ROLE_ARN }}
```

**Required Dockerfile modification**:

```dockerfile
RUN --mount=type=cache,target=/root/.cache/pip,id=pip-cache \
    pip install -r requirements.txt
```

## Go Project with Module Caching

```yaml
jobs:
  build:
    uses: oslokommune/reusable-docker-build-push/.github/workflows/reusable-docker-build-push.yml@v4
    with:
      aws_ecr_push: true
      go_cache: true
    secrets:
      AWS_ROLE_ARN: ${{ secrets.AWS_ROLE_ARN }}
```

**Required Dockerfile modification**:

```dockerfile
RUN --mount=type=cache,target=/root/.cache/go-build,id=go-build-cache \
    --mount=type=cache,target=/go/pkg/mod,id=go-mod-cache \
    go build -o /app ./cmd/server
```

## Multi-Platform Build

Build for multiple architectures:

```yaml
jobs:
  build:
    uses: oslokommune/reusable-docker-build-push/.github/workflows/reusable-docker-build-push.yml@v4
    with:
      aws_ecr_push: true
      platforms: linux/amd64,linux/arm64
    secrets:
      AWS_ROLE_ARN: ${{ secrets.AWS_ROLE_ARN }}
```

## Custom Dockerfile Location

Build with a Dockerfile in a subdirectory:

```yaml
jobs:
  build:
    uses: oslokommune/reusable-docker-build-push/.github/workflows/reusable-docker-build-push.yml@v4
    with:
      aws_ecr_push: true
      context: ./services/api
      file: ./services/api/Dockerfile.prod
    secrets:
      AWS_ROLE_ARN: ${{ secrets.AWS_ROLE_ARN }}
```

## With Build Arguments

Pass custom build arguments:

```yaml
jobs:
  build:
    uses: oslokommune/reusable-docker-build-push/.github/workflows/reusable-docker-build-push.yml@v4
    with:
      aws_ecr_push: true
      build_args: |
        NODE_ENV=production
        API_URL=https://api.example.com
    secrets:
      AWS_ROLE_ARN: ${{ secrets.AWS_ROLE_ARN }}
```

## With Docker Secrets

Pass secrets to the Docker build:

```yaml
jobs:
  build:
    uses: oslokommune/reusable-docker-build-push/.github/workflows/reusable-docker-build-push.yml@v4
    with:
      aws_ecr_push: true
    secrets:
      AWS_ROLE_ARN: ${{ secrets.AWS_ROLE_ARN }}
      DOCKER_SECRETS: |
        npm_token=${{ secrets.NPM_TOKEN }}
```

**Required Dockerfile modification**:

```dockerfile
RUN --mount=type=secret,id=npm_token \
    NPM_TOKEN=$(cat /run/secrets/npm_token) npm ci
```

## With SBOM and Provenance

Enable security attestations:

```yaml
jobs:
  build:
    uses: oslokommune/reusable-docker-build-push/.github/workflows/reusable-docker-build-push.yml@v4
    with:
      aws_ecr_push: true
      sbom: true
      provenance: true
    secrets:
      AWS_ROLE_ARN: ${{ secrets.AWS_ROLE_ARN }}
```

## Using Previous Job Artifacts

Download artifacts from a previous build step:

```yaml
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: npm ci && npm run build
      - uses: actions/upload-artifact@v4
        with:
          name: dist
          path: dist/

  build:
    needs: test
    uses: oslokommune/reusable-docker-build-push/.github/workflows/reusable-docker-build-push.yml@v4
    with:
      aws_ecr_push: true
      download_artifact: true
      download_artifact_name: dist
      download_artifact_path: dist/
    secrets:
      AWS_ROLE_ARN: ${{ secrets.AWS_ROLE_ARN }}
```

## Custom Tag Rules

Use custom tagging strategy:

```yaml
jobs:
  build:
    uses: oslokommune/reusable-docker-build-push/.github/workflows/reusable-docker-build-push.yml@v4
    with:
      aws_ecr_push: true
      tag_rules: |
        type=ref,event=branch
        type=ref,event=pr
        type=semver,pattern={{version}}
        type=semver,pattern={{major}}.{{minor}}
      tag_flavor: |
        latest=auto
        prefix=v
    secrets:
      AWS_ROLE_ARN: ${{ secrets.AWS_ROLE_ARN }}
```

## Using Outputs in Subsequent Jobs

Access workflow outputs in downstream jobs:

```yaml
jobs:
  build:
    uses: oslokommune/reusable-docker-build-push/.github/workflows/reusable-docker-build-push.yml@v4
    with:
      aws_ecr_push: true
    secrets:
      AWS_ROLE_ARN: ${{ secrets.AWS_ROLE_ARN }}

  deploy:
    needs: build
    runs-on: ubuntu-latest
    steps:
      - name: Deploy image
        run: |
          echo "Deploying image version: ${{ needs.build.outputs.image_version }}"
          echo "Image digest: ${{ needs.build.outputs.image_digest }}"
```

## With GitHub Environment

Use a deployment environment for secrets and protection rules:

```yaml
jobs:
  build:
    uses: oslokommune/reusable-docker-build-push/.github/workflows/reusable-docker-build-push.yml@v4
    with:
      environment: production
      aws_ecr_push: true
    secrets:
      AWS_ROLE_ARN: ${{ secrets.AWS_ROLE_ARN }}
```
