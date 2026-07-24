# Actions

## 🐣 VCS

Collection of actions related to VCS handling and to interact with GitHub.

| Action                                                                          | Reference                                                     |
|---------------------------------------------------------------------------------|---------------------------------------------------------------|
| [Assure version tag](#assure-version-tag)                                       | `eliashaeussler/gha/.github/actions/assure-version-tag@0.9.1` |
| [Checkout](#checkout)                                                           | `eliashaeussler/gha/.github/actions/checkout@0.9.1`           |
| [Check if PR exists for current branch](#check-if-pr-exists-for-current-branch) | `eliashaeussler/gha/.github/actions/has-pr@0.9.1`             |
| [Check if repository is private](#check-if-repository-is-private)               | `eliashaeussler/gha/.github/actions/is-private-repo@0.9.1`    |
| [Check if workflow is from fork PR](#check-if-workflow-is-from-fork-pr)         | `eliashaeussler/gha/.github/actions/is-fork@0.9.1`            |
| [Check if workflow is from Renovate](#check-if-workflow-is-from-renovate)       | `eliashaeussler/gha/.github/actions/is-renovate@0.9.1`        |
| [Check if workflow is from tag](#check-if-workflow-is-from-tag)                 | `eliashaeussler/gha/.github/actions/is-tag@0.9.1`             |

### [Assure version tag](../.github/actions/assure-version-tag/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/assure-version-tag@0.9.1
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Check tag'
    uses: eliashaeussler/gha/.github/actions/assure-version-tag@0.9.1
```

</details>

### [Checkout](../.github/actions/checkout/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/checkout@0.9.1
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Checkout'
    uses: eliashaeussler/gha/.github/actions/checkout@0.9.1
    with:
      fetch-depth: 0
      egress-policy: audit
```

</details>

### [Check if PR exists for current branch](../.github/actions/has-pr/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/has-pr@0.9.1
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Check if PR exists'
    id: has-pr
    uses: eliashaeussler/gha/.github/actions/has-pr@0.9.1

  - if: ${{ steps.has-pr.outputs.has-pr == 'true' }}
```

</details>

### [Check if repository is private](../.github/actions/is-private-repo/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/is-private-repo@0.9.1
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Check visibility'
    id: is-private
    uses: eliashaeussler/gha/.github/actions/is-private-repo@0.9.1

  - if: ${{ steps.is-private.outputs.is-private == 'true' }}
```

</details>

### [Check if workflow is from fork PR](../.github/actions/is-fork/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/is-fork@0.9.1
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Check fork'
    id: is-fork
    uses: eliashaeussler/gha/.github/actions/is-fork@0.9.1

  - if: ${{ steps.is-fork.outputs.is-fork == 'true' }}
```

</details>

### [Check if workflow is from Renovate](../.github/actions/is-renovate/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/is-renovate@0.9.1
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Check Renovate'
    id: is-renovate
    uses: eliashaeussler/gha/.github/actions/is-renovate@0.9.1

  - if: ${{ steps.is-renovate.outputs.is-renovate == 'true' }}
```

</details>

### [Check if workflow is from tag](../.github/actions/is-tag/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/is-tag@0.9.1
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Check tag'
    id: is-tag
    uses: eliashaeussler/gha/.github/actions/is-tag@0.9.1

  - if: ${{ steps.is-tag.outputs.is-version == 'true' }}
```

</details>

---

## 🛠️ Build

Collection of actions used for various builds.

| Action                                      | Reference                                               |
|---------------------------------------------|---------------------------------------------------------|
| [Build Docker images](#build-docker-images) | `eliashaeussler/gha/.github/actions/build-docker@0.9.1` |
| [Build assets](#build-assets)               | `eliashaeussler/gha/.github/actions/build-assets@0.9.1` |
| [Build PHAR](#build-phar)                   | `eliashaeussler/gha/.github/actions/build-phar@0.9.1`   |

### [Build Docker images](../.github/actions/build-docker/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/build-docker@0.9.1
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Build Docker'
    uses: eliashaeussler/gha/.github/actions/build-docker@0.9.1
    with:
      images: |
        eliashaeussler/my-fancy-project
        ghcr.io/eliashaeussler/my-fancy-project
      dockerhub-username: ${{ secrets.DOCKERHUB_USERNAME }}
      dockerhub-token: ${{ secrets.DOCKERHUB_TOKEN }}
      ghcr-token: ${{ secrets.GHCR_TOKEN }}
```

</details>

### [Build assets](../.github/actions/build-assets/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/build-assets@0.9.1
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Build assets'
    uses: eliashaeussler/gha/.github/actions/build-assets@0.9.1
    with:
      command: 'dev'
      node-env: 'development'
```

</details>

### [Build PHAR](../.github/actions/build-phar/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/build-phar@0.9.1
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Build PHAR'
    uses: eliashaeussler/gha/.github/actions/build-phar@0.9.1
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
| [Composer checks](#composer-checks)             | `eliashaeussler/gha/.github/actions/composer-checks@0.9.1`  |
| [Composer install](#composer-install)           | `eliashaeussler/gha/.github/actions/composer-install@0.9.1` |
| [Composer tests](#composer-tests)               | `eliashaeussler/gha/.github/actions/composer-tests@0.9.1`   |
| [Setup PHP environment](#setup-php-environment) | `eliashaeussler/gha/.github/actions/setup-php@0.9.1`        |

### [Composer checks](../.github/actions/composer-checks/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/composer-checks@0.9.1
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Perform Composer checks'
    uses: eliashaeussler/gha/.github/actions/composer-checks@0.9.1
```

</details>

### [Composer install](../.github/actions/composer-install/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/composer-install@0.9.1
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Install Composer packages'
    uses: eliashaeussler/gha/.github/actions/composer-install@0.9.1
    with:
      dependencies: 'locked'
      composer-options: '--no-dev'
```

</details>

### [Composer tests](../.github/actions/composer-tests/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/composer-tests@0.9.1
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Run Composer tests'
    uses: eliashaeussler/gha/.github/actions/composer-tests@0.9.1
    with:
      command: 'test:unit'
```

</details>

### [Setup PHP environment](../.github/actions/setup-php/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/setup-php@0.9.1
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Setup PHP'
    uses: eliashaeussler/gha/.github/actions/setup-php@0.9.1
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
| [npm checks](#npm-checks)                         | `eliashaeussler/gha/.github/actions/npm-checks@0.9.1`  |
| [npm install](#npm-install)                       | `eliashaeussler/gha/.github/actions/npm-install@0.9.1` |
| [Setup node environment](#setup-node-environment) | `eliashaeussler/gha/.github/actions/setup-node@0.9.1`  |

### [npm checks](../.github/actions/npm-checks/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/npm-checks@0.9.1
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Perform npm checks'
    uses: eliashaeussler/gha/.github/actions/npm-checks@0.9.1
```

</details>

### [npm install](../.github/actions/npm-install/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/npm-install@0.9.1
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Install npm packages'
    uses: eliashaeussler/gha/.github/actions/npm-install@0.9.1
```

</details>

### [Setup node environment](../.github/actions/setup-node/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/setup-node@0.9.1
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Setup node'
    uses: eliashaeussler/gha/.github/actions/setup-node@0.9.1
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
| [Setup DDEV](#setup-ddev) | `eliashaeussler/gha/.github/actions/setup-ddev@0.9.1` |

### [Setup DDEV](../.github/actions/setup-ddev/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/setup-ddev@0.9.1
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Setup DDEV'
    uses: eliashaeussler/gha/.github/actions/setup-ddev@0.9.1
    with:
      php-version: '8.5'
      ddev-version: '1.25.2'
      start: false
```

</details>

---

## 🚢 Deploy

Collection of actions targeting deployment of applications.

| Action                                                                | Reference                                               |
|-----------------------------------------------------------------------|---------------------------------------------------------|
| [Deploy application with Deployer](#deploy-application-with-deployer) | `eliashaeussler/gha/.github/actions/deploy-app@0.9.1`   |
| [Deploy to GitHub Pages](#deploy-to-github-pages)                     | `eliashaeussler/gha/.github/actions/deploy-pages@0.9.1` |

### [Deploy application with Deployer](../.github/actions/deploy-app/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/deploy-app@0.9.1
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Deploy'
    uses: eliashaeussler/gha/.github/actions/deploy-app@0.9.1
    with:
      private-key: ${{ secrets.DEPLOYER_PRIVATE_KEY }}
      known-hosts: ${{ secrets.DEPLOYER_KNOWN_HOSTS }}
      deployer-version: '7.5.12'
```

</details>

### [Deploy to GitHub Pages](../.github/actions/deploy-pages/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/deploy-pages@0.9.1
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Deploy'
    uses: eliashaeussler/gha/.github/actions/deploy-pages@0.9.1
    with:
      build-command: 'docs:build'
      dist-path: '.build/docs'
```

</details>
