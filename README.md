<div align="center">

# Reusable GitHub Actions & Workflows

[![CGL](https://img.shields.io/github/actions/workflow/status/eliashaeussler/gha/ci.yaml?label=CI&logo=github)](https://github.com/eliashaeussler/gha/actions/workflows/ci.yaml)
[![GitHub Release](https://img.shields.io/github/v/release/eliashaeussler/gha?sort=semver&logo=github&label=Release)](https://github.com/eliashaeussler/gha/releases/latest)

</div>

This package contains some GitHub workflows and actions for use in my
personal projects. It is not meant to be used anywhere else.
I won't provide support and don't accept pull requests for this repo.

## 📯 Actions

### [Assure version tag](.github/actions/assure-version-tag/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/assure-version-tag@0.4.6
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Check tag'
    uses: eliashaeussler/gha/.github/actions/assure-version-tag@0.4.6
```

</details>

### [Build Docker images](.github/actions/build-docker/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/build-docker@0.4.6
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Build Docker'
    uses: eliashaeussler/gha/.github/actions/build-docker@0.4.6
    with:
      images: |
        eliashaeussler/my-fancy-project
        ghcr.io/eliashaeussler/my-fancy-project
      dockerhub-username: ${{ secrets.DOCKERHUB_USERNAME }}
      dockerhub-token: ${{ secrets.DOCKERHUB_TOKEN }}
      ghcr-token: ${{ secrets.GHCR_TOKEN }}
```

</details>

### [Build docs](.github/actions/build-docs/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/build-docs@0.4.6
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Build docs'
    uses: eliashaeussler/gha/.github/actions/build-docs@0.4.6
    with:
      command: 'docs:build'
```

</details>

### [Build PHAR](.github/actions/build-phar/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/build-phar@0.4.6
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Build PHAR'
    uses: eliashaeussler/gha/.github/actions/build-phar@0.4.6
    with:
      target-file: my-fancy-project.phar
      build-dockerfile: true
      gpg-key: ${{ secrets.GPG_KEY }}
      gpg-passphrase: ${{ secrets.GPG_PASSPHRASE }}
```

</details>

### [Checkout](.github/actions/checkout/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/checkout@0.4.6
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Checkout'
    uses: eliashaeussler/gha/.github/actions/checkout@0.4.6
    with:
      fetch-depth: 0
      egress-policy: audit
```

</details>

### [Composer checks](.github/actions/composer-checks/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/composer-checks@0.4.6
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Perform Composer checks'
    uses: eliashaeussler/gha/.github/actions/composer-checks@0.4.6
```

</details>

### [Composer install](.github/actions/composer-install/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/composer-install@0.4.6
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Install Composer packages'
    uses: eliashaeussler/gha/.github/actions/composer-install@0.4.6
    with:
      dependencies: 'locked'
      composer-options: '--no-dev'
```

</details>

### [Composer tests](.github/actions/composer-tests/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/composer-install@0.4.6
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Run Composer tests'
    uses: eliashaeussler/gha/.github/actions/composer-install@0.4.6
    with:
      command: 'test:unit'
```

</details>

### [Deploy to GitHub Pages](.github/actions/deploy-pages/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/deploy-pages@0.4.6
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Deploy'
    uses: eliashaeussler/gha/.github/actions/deploy-pages@0.4.6
    with:
      build-command: 'docs:build'
      dist-path: '.build/docs'
```

</details>

### [Check if workflow is from fork PR](.github/actions/is-fork/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/is-fork@0.4.6
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Check fork'
    id: is-fork
    uses: eliashaeussler/gha/.github/actions/is-fork@0.4.6

  - if: ${{ steps.is-fork.outputs.is-fork == 'true' }}
```

</details>

### [Check if workflow is from Renovate](.github/actions/is-renovate/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/is-renovate@0.4.6
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Check Renovate'
    id: is-renovate
    uses: eliashaeussler/gha/.github/actions/is-renovate@0.4.6

  - if: ${{ steps.is-renovate.outputs.is-renovate == 'true' }}
```

</details>

### [Check if workflow is from tag](.github/actions/is-tag/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/is-tag@0.4.6
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Check tag'
    id: is-tag
    uses: eliashaeussler/gha/.github/actions/is-tag@0.4.6

  - if: ${{ steps.is-tag.outputs.is-version == 'true' }}
```

</details>

### [npm checks](.github/actions/npm-checks/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/npm-checks@0.4.6
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Perform npm checks'
    uses: eliashaeussler/gha/.github/actions/npm-checks@0.4.6
```

</details>

### [npm install](.github/actions/npm-install/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/npm-install@0.4.6
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Install npm packages'
    uses: eliashaeussler/gha/.github/actions/npm-install@0.4.6
```

</details>

### [Setup node environment](.github/actions/setup-node/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/setup-node@0.4.6
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Setup node'
    uses: eliashaeussler/gha/.github/actions/setup-node@0.4.6
    with:
      node-version: '24'
      cache: 'npm'
```

</details>

### [Setup DDEV](.github/actions/setup-ddev/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/setup-ddev@0.4.6
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Setup DDEV'
    uses: eliashaeussler/gha/.github/actions/setup-ddev@0.4.6
    with:
      php-version: '8.5'
      ddev-version: '1.25.2'
```

</details>

### [Setup PHP environment](.github/actions/setup-php/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/setup-php@0.4.6
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Setup PHP'
    uses: eliashaeussler/gha/.github/actions/setup-php@0.4.6
    with:
      php-version: '8.5'
      ini-file: 'production'
      coverage: 'pcov'
      tools: 'typo3/tailor'
```

</details>

## ✂️ Workflows

### [Asset integrity](.github/workflows/asset-integrity.yaml)

```yaml
uses: eliashaeussler/gha/.github/workflows/asset-integrity.yaml@0.4.6
```

<details>
<summary>Full example</summary>

```yaml
jobs:
  asset-integrity:
    secrets:
      ASSETS_TOKEN: ${{ secrets.REBUILD_ASSETS_TOKEN }}

    uses: eliashaeussler/gha/.github/workflows/asset-integrity.yaml@0.4.6

  other:
    needs: [asset-integrity]
    if: ${{ needs.asset-integrity.outputs.rebuilt == 'true' }}
```

</details>

### [Checks](.github/workflows/checks.yaml)

```yaml
uses: eliashaeussler/gha/.github/workflows/checks.yaml@0.4.6
```

<details>
<summary>Full example</summary>

```yaml
jobs:
  checks:
    uses: eliashaeussler/gha/.github/workflows/checks.yaml@0.4.6
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

</details>

### [Composer tests](.github/workflows/composer-tests.yaml)

```yaml
uses: eliashaeussler/gha/.github/workflows/composer-tests.yaml@0.4.6
```

<details>
<summary>Full example</summary>

```yaml
jobs:
  tests:
    uses: eliashaeussler/gha/.github/workflows/composer-tests.yaml@0.4.6
    with:
      php-version: '8.5'
      dependencies: 'highest'
      command: 'test:unit'
```

</details>

### [Composer test coverage](.github/workflows/composer-test-coverage.yaml)

```yaml
uses: eliashaeussler/gha/.github/workflows/composer-test-coverage.yaml@0.4.6
```

<details>
<summary>Full example</summary>

```yaml
jobs:
  test-coverage:
    uses: eliashaeussler/gha/.github/workflows/composer-test-coverage.yaml@0.4.6
    with:
      command: 'test:unit:coverage'
      coverage-driver: 'xdebug'
      coverage-file: '.Build/coverage/_merged/clover.xml'
```

</details>

### [Crowdin](.github/workflows/crowdin.yaml)

```yaml
uses: eliashaeussler/gha/.github/workflows/crowdin.yaml@0.4.6
```

<details>
<summary>Full example</summary>

```yaml
jobs:
  crowdin:
    secrets:
      CROWDIN_TOKEN: ${{ secrets.CROWDIN_TOKEN }}

    uses: eliashaeussler/gha/.github/workflows/crowdin.yaml@0.4.6
    with:
      project-id: 12345
```

</details>

### [GitHub release](.github/workflows/github-release.yaml)

```yaml
uses: eliashaeussler/gha/.github/workflows/extension-release.yaml@0.4.6
```

<details>
<summary>Full example</summary>

```yaml
jobs:
  release:
    secrets:
      RELEASE_TOKEN: ${{ secrets.RELEASE_TOKEN }}

    uses: eliashaeussler/gha/.github/workflows/extension-release.yaml@0.4.6
    with:
      version: '1.0.0'
      files: 'release_1.0.0.zip'
```

</details>

### [Merge branch](.github/workflows/merge.yaml)

```yaml
uses: eliashaeussler/gha/.github/workflows/merge.yaml@0.4.6
```

<details>
<summary>Full example</summary>

```yaml
jobs:
  merge:
    secrets:
      MERGE_TOKEN: ${{ secrets.MERGE_TOKEN }}

    uses: eliashaeussler/gha/.github/workflows/merge.yaml@0.4.6
```

</details>

### [Preparation](.github/workflows/preparation.yaml)

```yaml
uses: eliashaeussler/gha/.github/workflows/preparation.yaml@0.4.6
```

<details>
<summary>Full example</summary>

```yaml
jobs:
  prepare:
    uses: eliashaeussler/gha/.github/workflows/preparation.yaml@0.4.6

  other:
    needs: [prepare]
    if: ${{ needs.prepare.outputs.continue == 'true' }}
```

</details>

### [TYPO3 extension release](.github/workflows/extension-release.yaml)

```yaml
uses: eliashaeussler/gha/.github/workflows/extension-release.yaml@0.4.6
```

<details>
<summary>Full example</summary>

```yaml
jobs:
  release:
    secrets:
      TYPO3_API_TOKEN: ${{ secrets.TYPO3_API_TOKEN }}

    uses: eliashaeussler/gha/.github/workflows/extension-release.yaml@0.4.6
    with:
      packaging-excludes-file: Build/packaging_exclude.php
```

</details>

## ⭐ License

This project is licensed under [GNU General Public License 3.0 (or later)](LICENSE).
