# Actions

## 🐣 VCS

Collection of actions related to VCS handling and to interact with GitHub.

| Action                                                                    | Reference                                                     |
|---------------------------------------------------------------------------|---------------------------------------------------------------|
| [Assure version tag](#assure-version-tag)                                 | `eliashaeussler/gha/.github/actions/assure-version-tag@0.6.0` |
| [Checkout](#checkout)                                                     | `eliashaeussler/gha/.github/actions/checkout@0.6.0`           |
| [Check if workflow is from fork PR](#check-if-workflow-is-from-fork-pr)   | `eliashaeussler/gha/.github/actions/is-fork@0.6.0`            |
| [Check if workflow is from Renovate](#check-if-workflow-is-from-renovate) | `eliashaeussler/gha/.github/actions/is-renovate@0.6.0`        |
| [Check if workflow is from tag](#check-if-workflow-is-from-tag)           | `eliashaeussler/gha/.github/actions/is-tag@0.6.0`             |
| [Deploy to GitHub Pages](#deploy-to-github-pages)                         | `eliashaeussler/gha/.github/actions/deploy-pages@0.6.0`       |

### [Assure version tag](../.github/actions/assure-version-tag/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/assure-version-tag@0.6.0
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Check tag'
    uses: eliashaeussler/gha/.github/actions/assure-version-tag@0.6.0
```

</details>

### [Checkout](../.github/actions/checkout/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/checkout@0.6.0
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Checkout'
    uses: eliashaeussler/gha/.github/actions/checkout@0.6.0
    with:
      fetch-depth: 0
      egress-policy: audit
```

</details>

### [Check if workflow is from fork PR](../.github/actions/is-fork/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/is-fork@0.6.0
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Check fork'
    id: is-fork
    uses: eliashaeussler/gha/.github/actions/is-fork@0.6.0

  - if: ${{ steps.is-fork.outputs.is-fork == 'true' }}
```

</details>

### [Check if workflow is from Renovate](../.github/actions/is-renovate/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/is-renovate@0.6.0
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Check Renovate'
    id: is-renovate
    uses: eliashaeussler/gha/.github/actions/is-renovate@0.6.0

  - if: ${{ steps.is-renovate.outputs.is-renovate == 'true' }}
```

</details>

### [Check if workflow is from tag](../.github/actions/is-tag/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/is-tag@0.6.0
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Check tag'
    id: is-tag
    uses: eliashaeussler/gha/.github/actions/is-tag@0.6.0

  - if: ${{ steps.is-tag.outputs.is-version == 'true' }}
```

</details>

### [Deploy to GitHub Pages](../.github/actions/deploy-pages/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/deploy-pages@0.6.0
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Deploy'
    uses: eliashaeussler/gha/.github/actions/deploy-pages@0.6.0
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
| [Build Docker images](#build-docker-images)     | `eliashaeussler/gha/.github/actions/build-docker@0.6.0` |
| [Build docs](#build-docs)                       | `eliashaeussler/gha/.github/actions/build-docs@0.6.0`   |
| [Build PHAR](#build-phar)                       | `eliashaeussler/gha/.github/actions/build-phar@0.6.0`   |

### [Build Docker images](../.github/actions/build-docker/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/build-docker@0.6.0
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Build Docker'
    uses: eliashaeussler/gha/.github/actions/build-docker@0.6.0
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
uses: eliashaeussler/gha/.github/actions/build-docs@0.6.0
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Build docs'
    uses: eliashaeussler/gha/.github/actions/build-docs@0.6.0
    with:
      command: 'docs:build'
```

</details>

### [Build PHAR](../.github/actions/build-phar/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/build-phar@0.6.0
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Build PHAR'
    uses: eliashaeussler/gha/.github/actions/build-phar@0.6.0
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
| [Composer checks](#composer-checks)             | `eliashaeussler/gha/.github/actions/composer-checks@0.6.0`  |
| [Composer install](#composer-install)           | `eliashaeussler/gha/.github/actions/composer-install@0.6.0` |
| [Composer tests](#composer-tests)               | `eliashaeussler/gha/.github/actions/composer-tests@0.6.0`   |
| [Setup PHP environment](#setup-php-environment) | `eliashaeussler/gha/.github/actions/setup-php@0.6.0`        |

### [Composer checks](../.github/actions/composer-checks/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/composer-checks@0.6.0
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Perform Composer checks'
    uses: eliashaeussler/gha/.github/actions/composer-checks@0.6.0
```

</details>

### [Composer install](../.github/actions/composer-install/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/composer-install@0.6.0
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Install Composer packages'
    uses: eliashaeussler/gha/.github/actions/composer-install@0.6.0
    with:
      dependencies: 'locked'
      composer-options: '--no-dev'
```

</details>

### [Composer tests](../.github/actions/composer-tests/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/composer-tests@0.6.0
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Run Composer tests'
    uses: eliashaeussler/gha/.github/actions/composer-tests@0.6.0
    with:
      command: 'test:unit'
```

</details>

### [Setup PHP environment](../.github/actions/setup-php/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/setup-php@0.6.0
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Setup PHP'
    uses: eliashaeussler/gha/.github/actions/setup-php@0.6.0
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
| [npm checks](#npm-checks)                         | `eliashaeussler/gha/.github/actions/npm-checks@0.6.0`  |
| [npm install](#npm-install)                       | `eliashaeussler/gha/.github/actions/npm-install@0.6.0` |
| [Setup node environment](#setup-node-environment) | `eliashaeussler/gha/.github/actions/setup-node@0.6.0`  |

### [npm checks](../.github/actions/npm-checks/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/npm-checks@0.6.0
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Perform npm checks'
    uses: eliashaeussler/gha/.github/actions/npm-checks@0.6.0
```

</details>

### [npm install](../.github/actions/npm-install/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/npm-install@0.6.0
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Install npm packages'
    uses: eliashaeussler/gha/.github/actions/npm-install@0.6.0
```

</details>

### [Setup node environment](../.github/actions/setup-node/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/setup-node@0.6.0
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Setup node'
    uses: eliashaeussler/gha/.github/actions/setup-node@0.6.0
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
| [Setup DDEV](#setup-ddev) | `eliashaeussler/gha/.github/actions/setup-ddev@0.6.0` |

### [Setup DDEV](../.github/actions/setup-ddev/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/setup-ddev@0.6.0
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Setup DDEV'
    uses: eliashaeussler/gha/.github/actions/setup-ddev@0.6.0
    with:
      php-version: '8.5'
      ddev-version: '1.25.2'
      start: false
```

</details>
