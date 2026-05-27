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
    uses: eliashaeussler/gha/.github/actions/assure-version-tag@0.2.2
```

### [Build Docker images](.github/actions/build-docker/action.yaml)

```yaml
steps:
  - name: 'Build Docker'
    uses: eliashaeussler/gha/.github/actions/build-docker@0.2.2
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
    uses: eliashaeussler/gha/.github/actions/build-docs@0.2.2
    with:
      command: 'docs:build'
```

### [Build PHAR](.github/actions/build-phar/action.yaml)

```yaml
steps:
  - name: 'Build PHAR'
    uses: eliashaeussler/gha/.github/actions/build-phar@0.2.2
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
    uses: eliashaeussler/gha/.github/actions/composer-checks@0.2.2
```

### [Composer install](.github/actions/composer-install/action.yaml)

```yaml
steps:
  - name: 'Install Composer packages'
    uses: eliashaeussler/gha/.github/actions/composer-install@0.2.2
    with:
      dependencies: 'locked'
      composer-options: '--no-dev'
```

### [Composer tests](.github/actions/composer-tests/action.yaml)

```yaml
steps:
  - name: 'Run Composer tests'
    uses: eliashaeussler/gha/.github/actions/composer-install@0.2.2
    with:
      command: 'test:unit'
```

### [Create release](.github/actions/create-release/action.yaml)

```yaml
steps:
  - name: 'Create release'
    uses: eliashaeussler/gha/.github/actions/create-release@0.2.2
    with:
      version: '1.0.0'
      files: 'release_1.0.0.zip'
```

### [Deploy to GitHub Pages](.github/actions/deploy-pages/action.yaml)

```yaml
steps:
  - name: 'Deploy'
    uses: eliashaeussler/gha/.github/actions/deploy-pages@0.2.2
    with:
      build-command: 'docs:build'
      dist-path: '.build/docs'
```

### [Check if workflow is from fork PR](.github/actions/is-fork/action.yaml)

```yaml
steps:
  - name: 'Check fork'
    id: is-fork
    uses: eliashaeussler/gha/.github/actions/is-fork@0.2.2

  - if: ${{ steps.is-fork.outputs.is-fork == 'true' }}
```

### [Check if workflow is from Renovate](.github/actions/is-renovate/action.yaml)

```yaml
steps:
  - name: 'Check Renovate'
    id: is-renovate
    uses: eliashaeussler/gha/.github/actions/is-renovate@0.2.2

  - if: ${{ steps.is-renovate.outputs.is-renovate == 'true' }}
```

### [Check if workflow is from tag](.github/actions/is-tag/action.yaml)

```yaml
steps:
  - name: 'Check tag'
    id: is-tag
    uses: eliashaeussler/gha/.github/actions/is-tag@0.2.2

  - if: ${{ steps.is-tag.outputs.is-version == 'true' }}
```

### [npm checks](.github/actions/npm-checks/action.yaml)

```yaml
steps:
  - name: 'Perform npm checks'
    uses: eliashaeussler/gha/.github/actions/npm-checks@0.2.2
```

### [npm install](.github/actions/npm-install/action.yaml)

```yaml
steps:
  - name: 'Install npm packages'
    uses: eliashaeussler/gha/.github/actions/npm-install@0.2.2
```

### [Setup node environment](.github/actions/setup-node/action.yaml)

```yaml
steps:
  - name: 'Setup node'
    uses: eliashaeussler/gha/.github/actions/setup-node@0.2.2
    with:
      node-version: '24'
      cache: 'npm'
```

### [Setup PHP environment](.github/actions/setup-php/action.yaml)

```yaml
steps:
  - name: 'Setup PHP'
    uses: eliashaeussler/gha/.github/actions/setup-php@0.2.2
    with:
      php-version: '8.5'
      ini-file: 'production'
      coverage: 'pcov'
      tools: 'typo3/tailor'
```

## ✂️ Workflows

### [Asset integrity](.github/workflows/asset-integrity.yaml)

```yaml
jobs:
  asset-integrity:
    secrets:
      ASSETS_TOKEN: ${{ secrets.REBUILD_ASSETS_TOKEN }}

    uses: eliashaeussler/gha/.github/workflows/asset-integrity.yaml@0.2.2

  other:
    needs: [asset-integrity]
    if: ${{ needs.asset-integrity.outputs.rebuilt == 'true' }}
```

### [Checks](.github/workflows/checks.yaml)

```yaml
jobs:
  checks:
    uses: eliashaeussler/gha/.github/workflows/checks.yaml@0.2.2
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
    uses: eliashaeussler/gha/.github/workflows/composer-tests.yaml@0.2.2
    with:
      php-version: '8.5'
      dependencies: 'highest'
      command: 'test:unit'
```

### [Composer test coverage](.github/workflows/composer-test-coverage.yaml)

```yaml
jobs:
  test-coverage:
    uses: eliashaeussler/gha/.github/workflows/composer-test-coverage.yaml@0.2.2
    with:
      command: 'test:unit:coverage'
      coverage-driver: 'xdebug'
      coverage-file: '.Build/coverage/_merged/clover.xml'
```

### [Crowdin](.github/workflows/crowdin.yaml)

```yaml
jobs:
  crowdin:
    secrets:
      CROWDIN_TOKEN: ${{ secrets.CROWDIN_TOKEN }}

    uses: eliashaeussler/gha/.github/workflows/crowdin.yaml@0.2.2
    with:
      project-id: 12345
```

### [Merge branch](.github/workflows/merge.yaml)

```yaml
jobs:
  merge:
    secrets:
      MERGE_TOKEN: ${{ secrets.MERGE_TOKEN }}

    uses: eliashaeussler/gha/.github/workflows/merge.yaml@0.2.2
```

### [Preparation](.github/workflows/preparation.yaml)

```yaml
jobs:
  prepare:
    uses: eliashaeussler/gha/.github/workflows/preparation.yaml@0.2.2

  other:
    needs: [prepare]
    if: ${{ needs.prepare.outputs.continue == 'true' }}
```

### [TYPO3 extension release](.github/workflows/extension-release.yaml)

```yaml
jobs:
  release:
    secrets:
      TYPO3_API_TOKEN: ${{ secrets.TYPO3_API_TOKEN }}

    uses: eliashaeussler/gha/.github/workflows/extension-release.yaml@0.2.2
    with:
      packaging-excludes-file: Build/packaging_exclude.php
```

## ⭐ License

This project is licensed under [GNU General Public License 3.0 (or later)](LICENSE).
