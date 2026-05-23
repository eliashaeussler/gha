<div align="center">

# Reusable GitHub Actions & Workflows

[![CGL](https://img.shields.io/github/actions/workflow/status/eliashaeussler/gha/ci.yaml?label=CI&logo=github)](https://github.com/eliashaeussler/gha/actions/workflows/ci.yaml)

</div>

This package contains some GitHub workflows and actions for use in my
personal projects. It is not meant to be used anywhere else.
I won't provide support and don't accept pull requests for this repo.

## 📯 Actions

### [Assure version tag](.github/actions/assure-version-tag/action.yaml)

```yaml
steps:
  - name: 'Check tag'
    uses: eliashaeussler/gha/.github/actions/assure-version-tag
```

### [Build Docker images](.github/actions/build-docker/action.yaml)

```yaml
steps:
  - name: 'Build Docker'
    uses: eliashaeussler/gha/.github/actions/build-docker
    with:
      images: |
        eliashaeussler/my-fancy-project
        ghcr.io/eliashaeussler/my-fancy-project
      dockerhub-username: ${{ secrets.DOCKERHUB_USERNAME }}
      dockerhub-token: ${{ secrets.DOCKERHUB_TOKEN }}
      ghcr-token: ${{ secrets.GHCR_TOKEN }}
```

### [Build docs](.github/actions/build-docs/action.yaml)

```yaml
steps:
  - name: 'Build docs'
    uses: eliashaeussler/gha/.github/actions/build-docs
    with:
      command: 'docs:build'
```

### [Build PHAR](.github/actions/build-phar/action.yaml)

```yaml
steps:
  - name: 'Build PHAR'
    uses: eliashaeussler/gha/.github/actions/build-phar
    with:
      target-file: my-fancy-project.phar
      build-dockerfile: true
      gpg-key: ${{ secrets.GPG_KEY }}
      gpg-passphrase: ${{ secrets.GPG_PASSPHRASE }}
```

### [Composer checks](.github/actions/composer-checks/action.yaml)

```yaml
steps:
  - name: 'Perform Composer checks'
    uses: eliashaeussler/gha/.github/actions/composer-checks
```

### [Composer install](.github/actions/composer-install/action.yaml)

```yaml
steps:
  - name: 'Install Composer packages'
    uses: eliashaeussler/gha/.github/actions/composer-install
    with:
      dependencies: 'locked'
      composer-options: '--no-dev'
```

### [Composer tests](.github/actions/composer-tests/action.yaml)

```yaml
steps:
  - name: 'Run Composer tests'
    uses: eliashaeussler/gha/.github/actions/composer-install
    with:
      command: 'test:unit'
```

### [Create release](.github/actions/create-release/action.yaml)

```yaml
steps:
  - name: 'Create release'
    uses: eliashaeussler/gha/.github/actions/create-release
    with:
      version: '1.0.0'
      files: 'release_1.0.0.zip'
```

### [Deploy to GitHub Pages](.github/actions/deploy-pages/action.yaml)

```yaml
steps:
  - name: 'Deploy'
    uses: eliashaeussler/gha/.github/actions/deploy-pages
    with:
      build-command: 'docs:build'
      dist-path: '.build/docs'
```

### [Check if workflow is from tag](.github/actions/is-tag/action.yaml)

```yaml
steps:
  - name: 'Check tag'
    id: is-tag
    uses: eliashaeussler/gha/.github/actions/is-tag

  - if: ${{ steps.is-tag.outputs.is-version == 'true' }}
```

### [npm checks](.github/actions/npm-checks/action.yaml)

```yaml
steps:
  - name: 'Perform npm checks'
    uses: eliashaeussler/gha/.github/actions/npm-checks
```

### [npm install](.github/actions/npm-install/action.yaml)

```yaml
steps:
  - name: 'Install npm packages'
    uses: eliashaeussler/gha/.github/actions/npm-install
```

### [Setup node environment](.github/actions/setup-node/action.yaml)

```yaml
steps:
  - name: 'Setup node'
    uses: eliashaeussler/gha/.github/actions/setup-node
    with:
      node-version: '24'
      cache: 'npm'
```

### [Setup PHP environment](.github/actions/setup-php/action.yaml)

```yaml
steps:
  - name: 'Setup PHP'
    uses: eliashaeussler/gha/.github/actions/setup-php
    with:
      php-version: '8.5'
      ini-file: 'production'
      coverage: 'pcov'
      tools: 'typo3/tailor'
```

## ✂️ Workflows

### [Checks](.github/workflows/checks.yaml)

```yaml
jobs:
  checks:
    uses: eliashaeussler/gha/.github/workflows/checks.yaml
    with:
      # Composer
      composer: true
      php-version: '8.5'

      # npm
      npm: true
      node-version: '24'
      node-cache: 'npm'

      # Repository
      repository: true
```

### [Composer tests](.github/workflows/composer-tests.yaml)

```yaml
jobs:
  tests:
    uses: eliashaeussler/gha/.github/workflows/composer-tests.yaml
    with:
      php-version: '8.5'
      dependencies: 'highest'
      command: 'test:unit'
```

### [Composer test coverage](.github/workflows/composer-test-coverage.yaml)

```yaml
jobs:
  test-coverage:
    uses: eliashaeussler/gha/.github/workflows/composer-test-coverage.yaml
    with:
      command: 'test:unit:coverage'
      coverage-driver: 'xdebug'
      coverage-file: '.Build/coverage/_merged/clover.xml'
```

### [Preparation](.github/workflows/preparation.yaml)

```yaml
jobs:
  prepare:
    uses: eliashaeussler/gha/.github/workflows/preparation.yaml

  other:
    needs: [prepare]
    if: ${{ needs.prepare.outputs.continue == 'true' }}
```

## ⭐ License

This project is licensed under [GNU General Public License 3.0 (or later)](LICENSE).
