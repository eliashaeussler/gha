<div align="center">

# Reusable GitHub Actions & Workflows

[![CGL](https://img.shields.io/github/actions/workflow/status/eliashaeussler/gha/ci.yaml?label=CI&logo=github)](https://github.com/eliashaeussler/gha/actions/workflows/ci.yaml)

</div>

This package contains some GitHub workflows and actions for use in my
personal projects. It is not meant to be used anywhere else.
I won't provide support and don't accept pull requests for this repo.

## 📯 Actions

### [Composer checks](.github/actions/composer-checks/action.yaml)

```yaml
steps:
  - name: 'Perform Composer checks'
    uses: eliashaeussler/gha/.github/actions/composer-checks@main
```

### [Composer install](.github/actions/composer-install/action.yaml)

```yaml
steps:
  - name: 'Install Composer packages'
    uses: eliashaeussler/gha/.github/actions/composer-install@main
    with:
      dependencies: 'locked'
      composer-options: '--no-dev'
```

### [Composer tests](.github/actions/composer-tests/action.yaml)

```yaml
steps:
  - name: 'Run Composer tests'
    uses: eliashaeussler/gha/.github/actions/composer-install@main
    with:
      command: 'test:unit'
```

### [npm checks](.github/actions/npm-checks/action.yaml)

```yaml
steps:
  - name: 'Perform npm checks'
    uses: eliashaeussler/gha/.github/actions/npm-checks@main
```

### [npm install](.github/actions/npm-install/action.yaml)

```yaml
steps:
  - name: 'Install npm packages'
    uses: eliashaeussler/gha/.github/actions/npm-install@main
```

### [Setup node environment](.github/actions/setup-node/action.yaml)

```yaml
steps:
  - name: 'Setup node'
    uses: eliashaeussler/gha/.github/actions/setup-node@main
    with:
      node-version: '24'
      cache: 'npm'
```

### [Setup PHP environment](.github/actions/setup-php/action.yaml)

```yaml
steps:
  - name: 'Setup PHP'
    uses: eliashaeussler/gha/.github/actions/setup-php@main
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
    uses: eliashaeussler/gha/.github/workflows/checks.yaml@main
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
    uses: eliashaeussler/gha/.github/workflows/composer-tests.yaml@main
    with:
      php-version: '8.5'
      dependencies: 'highest'
      command: 'test:unit'
```

### [Composer test coverage](.github/workflows/composer-test-coverage.yaml)

```yaml
jobs:
  test-coverage:
    uses: eliashaeussler/gha/.github/workflows/composer-test-coverage.yaml@main
    with:
      command: 'test:unit:coverage'
      coverage-driver: 'xdebug'
      coverage-file: '.Build/coverage/_merged/clover.xml'
```

### [Preparation](.github/workflows/preparation.yaml)

```yaml
jobs:
  prepare:
    uses: eliashaeussler/gha/.github/workflows/preparation.yaml@main

  other:
    needs: [prepare]
    if: ${{ needs.prepare.outputs.continue == 'true' }}
```

## ⭐ License

This project is licensed under [GNU General Public License 3.0 (or later)](LICENSE).
