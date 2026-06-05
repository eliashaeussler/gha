# Actions

## 🐣 VCS

Collection of actions related to VCS handling and to interact with GitHub.

| Action                                                                    | Reference                                                     |
|---------------------------------------------------------------------------|---------------------------------------------------------------|
| [Assure version tag](#assure-version-tag)                                 | `eliashaeussler/gha/.github/actions/assure-version-tag@task/compatibility` |
| [Checkout](#checkout)                                                     | `eliashaeussler/gha/.github/actions/checkout@task/compatibility`           |
| [Check if workflow is from fork PR](#check-if-workflow-is-from-fork-pr)   | `eliashaeussler/gha/.github/actions/is-fork@task/compatibility`            |
| [Check if workflow is from Renovate](#check-if-workflow-is-from-renovate) | `eliashaeussler/gha/.github/actions/is-renovate@task/compatibility`        |
| [Check if workflow is from tag](#check-if-workflow-is-from-tag)           | `eliashaeussler/gha/.github/actions/is-tag@task/compatibility`             |
| [Deploy to GitHub Pages](#deploy-to-github-pages)                         | `eliashaeussler/gha/.github/actions/deploy-pages@task/compatibility`       |

### [Assure version tag](../.github/actions/assure-version-tag/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/assure-version-tag@task/compatibility
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Check tag'
    uses: eliashaeussler/gha/.github/actions/assure-version-tag@task/compatibility
```

</details>

### [Checkout](../.github/actions/checkout/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/checkout@task/compatibility
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Checkout'
    uses: eliashaeussler/gha/.github/actions/checkout@task/compatibility
    with:
      fetch-depth: 0
      egress-policy: audit
```

</details>

### [Check if workflow is from fork PR](../.github/actions/is-fork/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/is-fork@task/compatibility
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Check fork'
    id: is-fork
    uses: eliashaeussler/gha/.github/actions/is-fork@task/compatibility

  - if: ${{ steps.is-fork.outputs.is-fork == 'true' }}
```

</details>

### [Check if workflow is from Renovate](../.github/actions/is-renovate/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/is-renovate@task/compatibility
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Check Renovate'
    id: is-renovate
    uses: eliashaeussler/gha/.github/actions/is-renovate@task/compatibility

  - if: ${{ steps.is-renovate.outputs.is-renovate == 'true' }}
```

</details>

### [Check if workflow is from tag](../.github/actions/is-tag/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/is-tag@task/compatibility
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Check tag'
    id: is-tag
    uses: eliashaeussler/gha/.github/actions/is-tag@task/compatibility

  - if: ${{ steps.is-tag.outputs.is-version == 'true' }}
```

</details>

### [Deploy to GitHub Pages](../.github/actions/deploy-pages/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/deploy-pages@task/compatibility
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Deploy'
    uses: eliashaeussler/gha/.github/actions/deploy-pages@task/compatibility
    with:
      build-command: 'docs:build'
      dist-path: '.build/docs'
```

</details>

---

## 🛠️ Build

Collection of actions used for various builds.

| Action                                          | Reference                                               |
|-------------------------------------------------|---------------------------------------------------------|
| [Build Docker images](#build-docker-images)     | `eliashaeussler/gha/.github/actions/build-docker@task/compatibility` |
| [Build docs](#build-docs)                       | `eliashaeussler/gha/.github/actions/build-docs@task/compatibility`   |
| [Build PHAR](#build-phar)                       | `eliashaeussler/gha/.github/actions/build-phar@task/compatibility`   |

### [Build Docker images](../.github/actions/build-docker/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/build-docker@task/compatibility
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Build Docker'
    uses: eliashaeussler/gha/.github/actions/build-docker@task/compatibility
    with:
      images: |
        eliashaeussler/my-fancy-project
        ghcr.io/eliashaeussler/my-fancy-project
      dockerhub-username: ${{ secrets.DOCKERHUB_USERNAME }}
      dockerhub-token: ${{ secrets.DOCKERHUB_TOKEN }}
      ghcr-token: ${{ secrets.GHCR_TOKEN }}
```

</details>

### [Build docs](../.github/actions/build-docs/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/build-docs@task/compatibility
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Build docs'
    uses: eliashaeussler/gha/.github/actions/build-docs@task/compatibility
    with:
      command: 'docs:build'
```

</details>

### [Build PHAR](../.github/actions/build-phar/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/build-phar@task/compatibility
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Build PHAR'
    uses: eliashaeussler/gha/.github/actions/build-phar@task/compatibility
    with:
      target-file: my-fancy-project.phar
      build-dockerfile: true
      gpg-key: ${{ secrets.GPG_KEY }}
      gpg-passphrase: ${{ secrets.GPG_PASSPHRASE }}
```

</details>

---

## 🔥 Composer & PHP

Collection of useful actions for PHP- and Composer-based projects.

| Action                                          | Reference                                                   |
|-------------------------------------------------|-------------------------------------------------------------|
| [Composer checks](#composer-checks)             | `eliashaeussler/gha/.github/actions/composer-checks@task/compatibility`  |
| [Composer install](#composer-install)           | `eliashaeussler/gha/.github/actions/composer-install@task/compatibility` |
| [Composer tests](#composer-tests)               | `eliashaeussler/gha/.github/actions/composer-tests@task/compatibility`   |
| [Setup PHP environment](#setup-php-environment) | `eliashaeussler/gha/.github/actions/setup-php@task/compatibility`        |

### [Composer checks](../.github/actions/composer-checks/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/composer-checks@task/compatibility
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Perform Composer checks'
    uses: eliashaeussler/gha/.github/actions/composer-checks@task/compatibility
```

</details>

### [Composer install](../.github/actions/composer-install/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/composer-install@task/compatibility
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Install Composer packages'
    uses: eliashaeussler/gha/.github/actions/composer-install@task/compatibility
    with:
      dependencies: 'locked'
      composer-options: '--no-dev'
```

</details>

### [Composer tests](../.github/actions/composer-tests/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/composer-tests@task/compatibility
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Run Composer tests'
    uses: eliashaeussler/gha/.github/actions/composer-tests@task/compatibility
    with:
      command: 'test:unit'
```

</details>

### [Setup PHP environment](../.github/actions/setup-php/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/setup-php@task/compatibility
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Setup PHP'
    uses: eliashaeussler/gha/.github/actions/setup-php@task/compatibility
    with:
      php-version: '8.5'
      ini-file: 'production'
      coverage: 'pcov'
      tools: 'typo3/tailor'
```

</details>

---

## 🦄 Node & npm

Collection of useful actions for Node.js and npm.

| Action                                            | Reference                                              |
|---------------------------------------------------|--------------------------------------------------------|
| [npm checks](#npm-checks)                         | `eliashaeussler/gha/.github/actions/npm-checks@task/compatibility`  |
| [npm install](#npm-install)                       | `eliashaeussler/gha/.github/actions/npm-install@task/compatibility` |
| [Setup node environment](#setup-node-environment) | `eliashaeussler/gha/.github/actions/setup-node@task/compatibility`  |

### [npm checks](../.github/actions/npm-checks/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/npm-checks@task/compatibility
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Perform npm checks'
    uses: eliashaeussler/gha/.github/actions/npm-checks@task/compatibility
```

</details>

### [npm install](../.github/actions/npm-install/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/npm-install@task/compatibility
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Install npm packages'
    uses: eliashaeussler/gha/.github/actions/npm-install@task/compatibility
```

</details>

### [Setup node environment](../.github/actions/setup-node/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/setup-node@task/compatibility
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Setup node'
    uses: eliashaeussler/gha/.github/actions/setup-node@task/compatibility
    with:
      node-version: '24'
      cache: 'npm'
```

</details>

---

## 🌐 Environment

Collection of actions related to environment handling.

| Action                    | Reference                                             |
|---------------------------|-------------------------------------------------------|
| [Setup DDEV](#setup-ddev) | `eliashaeussler/gha/.github/actions/setup-ddev@task/compatibility` |

### [Setup DDEV](../.github/actions/setup-ddev/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/setup-ddev@task/compatibility
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Setup DDEV'
    uses: eliashaeussler/gha/.github/actions/setup-ddev@task/compatibility
    with:
      php-version: '8.5'
      ddev-version: '1.25.2'
      start: false
```

</details>
