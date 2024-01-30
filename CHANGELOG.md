# Changelog

## [2.2.0](https://github.com/oslokommune/reusable-docker-build-push/compare/v2.1.0...v2.2.0) (2024-01-30)


### Features

* Add image repository metadata as build args ([#52](https://github.com/oslokommune/reusable-docker-build-push/issues/52)) ([579ba68](https://github.com/oslokommune/reusable-docker-build-push/commit/579ba6894cd33aea5fe81fbe5d7ef1d137152b5f))

## [2.1.0](https://github.com/oslokommune/reusable-docker-build-push/compare/v2.0.4...v2.1.0) (2024-01-26)


### Features

* Add additional build arguments ([#50](https://github.com/oslokommune/reusable-docker-build-push/issues/50)) ([7eff07e](https://github.com/oslokommune/reusable-docker-build-push/commit/7eff07e01639b2e747570aac81fe4b4db0ad3961))
* Change the repository build argument to be more specific ([0536e3b](https://github.com/oslokommune/reusable-docker-build-push/commit/0536e3b060d3dcd354233d72ddd26892b1e0ae3b))

## [2.0.4](https://github.com/oslokommune/reusable-docker-build-push/compare/v2.0.3...v2.0.4) (2024-01-05)


### Dependency Updates

* Bump docker/metadata-action in /.github/workflows ([#48](https://github.com/oslokommune/reusable-docker-build-push/issues/48)) ([4fb7e79](https://github.com/oslokommune/reusable-docker-build-push/commit/4fb7e79aaab26a2ec18b63fbc55a030ea9b60f60))

## [2.0.3](https://github.com/oslokommune/reusable-docker-build-push/compare/v2.0.2...v2.0.3) (2023-12-21)


### Dependency Updates

* Bump docker/metadata-action in /.github/workflows ([#43](https://github.com/oslokommune/reusable-docker-build-push/issues/43)) ([e8dffb0](https://github.com/oslokommune/reusable-docker-build-push/commit/e8dffb06b7c78a01ba38e49cc2402a289ebdca9d))

## [2.0.2](https://github.com/oslokommune/reusable-docker-build-push/compare/v2.0.1...v2.0.2) (2023-11-20)


### Dependency Updates

* Bump docker/build-push-action in /.github/workflows ([#37](https://github.com/oslokommune/reusable-docker-build-push/issues/37)) ([4ef1d0b](https://github.com/oslokommune/reusable-docker-build-push/commit/4ef1d0b5a871478f03cdf71b48106ad5754f3c22))

## [2.0.1](https://github.com/oslokommune/reusable-docker-build-push/compare/v2.0.0...v2.0.1) (2023-11-15)


### Dependency Updates

* Bump actions/checkout from 4.1.0 to 4.1.1 in /.github/workflows ([54b1c16](https://github.com/oslokommune/reusable-docker-build-push/commit/54b1c16848b497c323b6691d40876a4d0f6960d2))
* Bump google-github-actions/release-please-action ([#35](https://github.com/oslokommune/reusable-docker-build-push/issues/35)) ([30fcc88](https://github.com/oslokommune/reusable-docker-build-push/commit/30fcc88ab4500a4f348c9fecf88af5fc4eaf1595))

## [2.0.0](https://github.com/oslokommune/reusable-docker-build-push/compare/v1.2.1...v2.0.0) (2023-10-16)


### ⚠ BREAKING CHANGES

* Add separate toggles for AWS ECR and GHCR ([#32](https://github.com/oslokommune/reusable-docker-build-push/issues/32))

### Features

* Add separate toggles for AWS ECR and GHCR ([#32](https://github.com/oslokommune/reusable-docker-build-push/issues/32)) ([8a93c3e](https://github.com/oslokommune/reusable-docker-build-push/commit/8a93c3e1ef78d5a2da98ba251e23840352de8fda))

## [1.2.1](https://github.com/oslokommune/reusable-docker-build-push/compare/v1.2.0...v1.2.1) (2023-10-04)


### Dependency Updates

* Bump aws-actions/configure-aws-credentials in /.github/workflows ([#26](https://github.com/oslokommune/reusable-docker-build-push/issues/26)) ([5d22c6f](https://github.com/oslokommune/reusable-docker-build-push/commit/5d22c6fae5c4128b50343ffc14188c763ce8bcbc))
* Bump docker/setup-buildx-action in /.github/workflows ([#22](https://github.com/oslokommune/reusable-docker-build-push/issues/22)) ([471571c](https://github.com/oslokommune/reusable-docker-build-push/commit/471571cd6be09ca3254c025e7f8c1053d2ff9a39))

## [1.2.0](https://github.com/oslokommune/reusable-docker-build-push/compare/v1.1.2...v1.2.0) (2023-10-04)


### Dependency Updates

* Bump actions/checkout from 4.0.0 to 4.1.0 in /.github/workflows ([e8920cb](https://github.com/oslokommune/reusable-docker-build-push/commit/e8920cb53f6fc80115f9eb288e32cb825b285435))
* Bump aws-actions/amazon-ecr-login in /.github/workflows ([#25](https://github.com/oslokommune/reusable-docker-build-push/issues/25)) ([5f63d8c](https://github.com/oslokommune/reusable-docker-build-push/commit/5f63d8c45133c846bde0c10bfc80b348e5d77156))


### Features

* Set mask-password explicitly ([#27](https://github.com/oslokommune/reusable-docker-build-push/issues/27)) ([448ba12](https://github.com/oslokommune/reusable-docker-build-push/commit/448ba127ebbfd3f79f7ea5165218292c0cb7b07e))

## [1.1.2](https://github.com/oslokommune/reusable-docker-build-push/compare/v1.1.1...v1.1.2) (2023-09-28)


### Dependency Updates

* Bump docker/build-push-action in /.github/workflows ([#18](https://github.com/oslokommune/reusable-docker-build-push/issues/18)) ([e6a530f](https://github.com/oslokommune/reusable-docker-build-push/commit/e6a530f95fc7f21dddeb0aca3d5aa3dd3b29f777))
* Bump docker/login-action from 2.2.0 to 3.0.0 in /.github/workflows ([#19](https://github.com/oslokommune/reusable-docker-build-push/issues/19)) ([49a513c](https://github.com/oslokommune/reusable-docker-build-push/commit/49a513cc1b8b081a876dfddd1ed68f40ef83f91d))
* Bump docker/metadata-action in /.github/workflows ([#17](https://github.com/oslokommune/reusable-docker-build-push/issues/17)) ([4b4e2a5](https://github.com/oslokommune/reusable-docker-build-push/commit/4b4e2a5520f312c33457051d0f5bdc772b3b1577))
* Bump docker/setup-qemu-action in /.github/workflows ([#20](https://github.com/oslokommune/reusable-docker-build-push/issues/20)) ([6b31622](https://github.com/oslokommune/reusable-docker-build-push/commit/6b31622114f7e8eb9cee24782ee0ce10174c254b))

## [1.1.1](https://github.com/oslokommune/reusable-docker-build-push/compare/v1.1.0...v1.1.1) (2023-09-08)


### Dependency Updates

* Bump actions/checkout from 3.6.0 to 4.0.0 in /.github/workflows ([5447fab](https://github.com/oslokommune/reusable-docker-build-push/commit/5447fab2792ee9be20c7d971da8bdd926ad730d5))
* Bump aws-actions/amazon-ecr-login in /.github/workflows ([#10](https://github.com/oslokommune/reusable-docker-build-push/issues/10)) ([f60afbe](https://github.com/oslokommune/reusable-docker-build-push/commit/f60afbe7db33930942c5e2975c486b997a9c0d31))
* Bump aws-actions/configure-aws-credentials in /.github/workflows ([#14](https://github.com/oslokommune/reusable-docker-build-push/issues/14)) ([2d2f9a0](https://github.com/oslokommune/reusable-docker-build-push/commit/2d2f9a06a728807b38a93face71114ab81e9f6b2))

## [1.1.0](https://github.com/oslokommune/reusable-docker-build-push/compare/v1.0.0...v1.1.0) (2023-09-05)


### Dependency Updates

* Bump aws-actions/configure-aws-credentials in /.github/workflows ([#2](https://github.com/oslokommune/reusable-docker-build-push/issues/2)) ([229bb96](https://github.com/oslokommune/reusable-docker-build-push/commit/229bb9685deef24b6d0308b7647920d8415ad221))
* Bump docker/build-push-action in /.github/workflows ([#1](https://github.com/oslokommune/reusable-docker-build-push/issues/1)) ([b51268f](https://github.com/oslokommune/reusable-docker-build-push/commit/b51268f2f76d02150ad2c1d17413ef486b1408ad))
* Bump docker/metadata-action in /.github/workflows ([#3](https://github.com/oslokommune/reusable-docker-build-push/issues/3)) ([7f750ea](https://github.com/oslokommune/reusable-docker-build-push/commit/7f750ea9aa1d15494da34a19c3a0818b805de6e6))
* Bump google-github-actions/release-please-action ([#7](https://github.com/oslokommune/reusable-docker-build-push/issues/7)) ([f9ee3f7](https://github.com/oslokommune/reusable-docker-build-push/commit/f9ee3f77834315c5d37cf138e6c1b07cf382c686))


### Features

* Bump docker/setup-buildx-action in /.github/workflows ([#4](https://github.com/oslokommune/reusable-docker-build-push/issues/4)) ([e60072e](https://github.com/oslokommune/reusable-docker-build-push/commit/e60072eebe633433fe6f862e416bb52b6b5e3f68))

## 1.0.0 (2023-08-29)


### Features

* Add workflow ([6bfef86](https://github.com/oslokommune/reusable-docker-build-push/commit/6bfef869ca1757c5a2a3d7bfc47bfc8705e6919c))
* Rename workflow ([98afba9](https://github.com/oslokommune/reusable-docker-build-push/commit/98afba92cb4a432c61d8a2a675c74059f32d04ce))
