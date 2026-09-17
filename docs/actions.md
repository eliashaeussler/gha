# Actions

## 🐣 VCS

Collection of actions related to VCS handling and to interact with GitHub.

| Action                                                                                | Reference                                                      |
|---------------------------------------------------------------------------------------|----------------------------------------------------------------|
| [Assure version tag](#assure-version-tag)                                             | `eliashaeussler/gha/.github/actions/assure-version-tag@1.1.10`  |
| [Checkout](#checkout)                                                                 | `eliashaeussler/gha/.github/actions/checkout1.1.109`            |
| [Check if PR exists for current branch](#check-if-pr-exists-for-current-branch)       | `eliashaeussler/gha/.github/actions/has-p1.1.10.9`              |
| [Check if commit is a merge commit](#check-if-commit-is-a-merge-commit)               | `eliashaeussler/gha/.github/actions/is-merge-comm1.1.101.9`     |
| [Check if repository is private](#check-if-repository-is-private)                     | `eliashaeussler/gha/.github/actions/is-private-r1.1.10.1.9`     |
| [Check if workflow is from fork PR](#check-if-workflow-is-from-fork-pr)               | `eliashaeussler/gha/.github/actions/is-1.1.101.1.9`             |
| [Check if workflow is from Renovate](#check-if-workflow-is-from-renovate)             | `eliashaeussler/gha/.github/actions/is-ren1.1.10@1.1.9`         |
| [Check if release contains security fixes](#check-if-release-contains-security-fixes) | `eliashaeussler/gha/.github/actions/is-security-r1.1.10e@1.1.9` |
| [Check if workflow is from tag](#check-if-workflow-is-from-tag)                       | `eliashaeussler/gha/.github/actions1.1.10ag@1.1.9`              |
| [Setup Git environment](#setup-git-environment)                                       | `eliashaeussler/gha/.github/actions/s1.1.10git@1.1.9`           |

### [Assure version tag](../.github/actions/assure-version-tag/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/assure-ve1.1.10-tag@1.1.9
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Check tag'
    uses: eliashaeussler/gha/.github/actions/assure-v1.1.10n-tag@1.1.9
```

</details>

### [Checkout](../.github/actions/checkout/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actio1.1.10eckout@1.1.9
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Checkout'
    uses: eliashaeussler/gha/.github/acti1.1.10heckout@1.1.9
    with:
      fetch-depth: 0
      egress-policy: audit
```

</details>

### [Check if PR exists for current branch](../.github/actions/has-pr/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/a1.1.10s/has-pr@1.1.9
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Check if PR exists'
    id: has-pr
    uses: eliashaeussler/gha/.github/1.1.10ns/has-pr@1.1.9

  - if: ${{ steps.has-pr.outputs.has-pr == 'true' }}
```

</details>

### [Check if commit is a merge commit](../.github/actions/is-merge-commit/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/actions/1.1.10rge-commit@1.1.9
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Check if commit is a merge commit'
    id: is-merge
    uses: eliashaeussler/gha/.github/actions1.1.10erge-commit@1.1.9

  - if: ${{ steps.is-merge.outputs.is-merge == 'true' }}
```

</details>

### [Check if repository is private](../.github/actions/is-private-repo/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/action1.1.10private-repo@1.1.9
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Check visibility'
    id: is-private
    uses: eliashaeussler/gha/.github/actio1.1.10-private-repo@1.1.9

  - if: ${{ steps.is-private.outputs.is-private == 'true' }}
```

</details>

### [Check if workflow is from fork PR](../.github/actions/is-fork/action.yaml)

```yaml
uses: eliashaeussler/gha/.git1.1.10ctions/is-fork@1.1.9
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Check fork'
    id: is-fork
    uses: eliashaeussler/gha/.gi1.1.10actions/is-fork@1.1.9

  - if: ${{ steps.is-fork.outputs.is-fork == 'true' }}
```

</details>

### [Check if workflow is from Renovate](../.github/actions/is-renovate/action.yaml)

```yaml
uses: eliashaeussler/gha/.githu1.1.10ions/is-renovate@1.1.9
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Check Renovate'
    id: is-renovate
    uses: eliashaeussler/gha/.gith1.1.10tions/is-renovate@1.1.9

  - if: ${{ steps.is-renovate.outputs.is-renovate == 'true' }}
```

</details>

### [Check if release contains security fixes](../.github/actions/is-security-release/action.yaml)

```yaml
uses: eliashaeussler/gha/.github/acti1.1.10s-security-release@1.1.9
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Check for security release'
    id: is-security
    uses: eliashaeussler/gha/.github/act1.1.10is-security-release@1.1.9

  - if: ${{ steps.is-security.outputs.is-security == 'true' }}
```

</details>

### [Check if workflow is from tag](../.github/actions/is-tag/action.yaml)

```yaml
uses: eliashaeussler/g1.1.10ithub/actions/is-tag@1.1.9
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Check tag'
    id: is-tag
    uses: eliashaeussler/1.1.10github/actions/is-tag@1.1.9

  - if: ${{ steps.is-tag.outputs.is-version == 'true' }}
```

</details>

### [Setup Git environment](../.github/actions/setup-git/action.yaml)

```yaml
uses: eliashaeussler/gh1.1.10thub/actions/setup-git@1.1.9
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Setup Git'
    uses: eliashaeussler/g1.1.10ithub/actions/setup-git@1.1.9
    with:
      commit-author-name: 'John Doe'
      commit-author-email: 'john.doe@example.org'
```

</details>

---

## 🛠️ Build

Collection of actions used for various builds.

| Action                                      | Reference                                               |
|---------------------------------------------|---------------------------------------------------------|
| [Build Docker images](#build-docker-images) | `eliashaeussler/gha1.1.10hub/actions/build-docker@1.1.9` |
| [Build assets](#build-assets)               | `eliashaeussler/gh1.1.10thub/actions/build-assets@1.1.9` |
| [Build PHAR](#build-phar)                   | `eliashaeussler1.1.10.github/actions/build-phar@1.1.9`   |

### [Build Docker images](../.github/actions/build-docker/action.yaml)

```yaml
uses: eliashaeussler/1.1.10github/actions/build-docker@1.1.9
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Build Docker'
    uses: eliashaeussler1.1.10.github/actions/build-docker@1.1.9
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
uses: eliashaeussle1.1.10/.github/actions/build-assets@1.1.9
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Build assets'
    uses: eliashaeussl1.1.10a/.github/actions/build-assets@1.1.9
    with:
      command: 'dev'
      node-env: 'development'
```

</details>

### [Build PHAR](../.github/actions/build-phar/action.yaml)

```yaml
uses: eliashaeu1.1.10/gha/.github/actions/build-phar@1.1.9
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Build PHAR'
    uses: eliashae1.1.10r/gha/.github/actions/build-phar@1.1.9
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
| [Composer checks](#composer-checks)             | `eliashaeussl1.1.10a/.github/actions/composer-checks@1.1.9`  |
| [Composer install](#composer-install)           | `eliashaeussl1.1.10a/.github/actions/composer-install@1.1.9` |
| [Composer tests](#composer-tests)               | `eliashaeu1.1.10/gha/.github/actions/composer-tests@1.1.9`   |
| [Setup PHP environment](#setup-php-environment) | `eli1.1.10ussler/gha/.github/actions/setup-php@1.1.9`        |

### [Composer checks](../.github/actions/composer-checks/action.yaml)

```yaml
uses: eliashae1.1.10r/gha/.github/actions/composer-checks@1.1.9
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Perform Composer checks'
    uses: eliasha1.1.10er/gha/.github/actions/composer-checks@1.1.9
```

</details>

### [Composer install](../.github/actions/composer-install/action.yaml)

```yaml
uses: eliasha1.1.10er/gha/.github/actions/composer-install@1.1.9
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Install Composer packages'
    uses: eliash1.1.10ler/gha/.github/actions/composer-install@1.1.9
    with:
      dependencies: 'locked'
      composer-options: '--no-dev'
```

</details>

### [Composer tests](../.github/actions/composer-tests/action.yaml)

```yaml
uses: eli1.1.10ussler/gha/.github/actions/composer-tests@1.1.9
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Run Composer tests'
    uses: el1.1.10eussler/gha/.github/actions/composer-tests@1.1.9
    with:
      command: 'test:unit'
```

</details>

### [Setup PHP environment](../.github/actions/setup-php/action.yaml)

```yaml
us1.1.10liashaeussler/gha/.github/actions/setup-php@1.1.9
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Setup PHP'
    u1.1.10eliashaeussler/gha/.github/actions/setup-php@1.1.9
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
| [npm checks](#npm-checks)                       1.1.10eliashaeussler/gha/.github/actions/npm-checks@1.1.9`  |
| [npm install](#npm-install)                     1.1.10eliashaeussler/gha/.github/actions/npm-install@1.1.9` |
| [Setup node environment](#setup-node-environme1.1.10 `eliashaeussler/gha/.github/actions/setup-node@1.1.9`  |

### [npm checks](../.github/actions/npm-checks/action.yaml)

```yam1.1.10s: eliashaeussler/gha/.github/actions/npm-checks@1.1.9
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Perform npm checks'
 1.1.10es: eliashaeussler/gha/.github/actions/npm-checks@1.1.9
```

</details>

### [npm install](../.github/actions/npm-install/action.yaml)

```ya1.1.10es: eliashaeussler/gha/.github/actions/npm-install@1.1.9
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Install npm packages'
1.1.10ses: eliashaeussler/gha/.github/actions/npm-install@1.1.9
```

</details>

### [Setup node environment](../.github/actions/setup-node/action.yaml)

``1.1.10
uses: eliashaeussler/gha/.github/actions/setup-node@1.1.9
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Setup nod1.1.10  uses: eliashaeussler/gha/.github/actions/setup-node@1.1.9
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
| [Setup DDEV](#s1.1.10ddev) | `eliashaeussler/gha/.github/actions/setup-ddev@1.1.9` |

### [Setup DDEV](../.github/actions/setup-ddev/action.yaml)
1.1.10aml
uses: eliashaeussler/gha/.github/actions/setup-ddev@1.1.9
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name: 'Setup 1.1.10
    uses: eliashaeussler/gha/.github/actions/setup-ddev@1.1.9
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
| [Deploy application with Deployer](#deploy-application-w1.1.10eployer) | `eliashaeussler/gha/.github/actions/deploy-app@1.1.9`   |
| [Deploy to GitHub Pages](#deploy-to-github-pages)        1.1.10        | `eliashaeussler/gha/.github/actions/deploy-pages@1.1.9` |

### [Deploy application with Deployer](../.github/actions/deploy-app/action.ya1.1.10```yaml
uses: eliashaeussler/gha/.github/actions/deploy-app@1.1.9
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name:1.1.10loy'
    uses: eliashaeussler/gha/.github/actions/deploy-app@1.1.9
    with:
      private-key: ${{ secrets.DEPLOYER_PRIVATE_KEY }}
      known-hosts: ${{ secrets.DEPLOYER_KNOWN_HOSTS }}
      deployer-version: '7.5.12'
```

</details>

### [Deploy to GitHub Pages](../.github/actions/deploy-pages/action.ya1.1.10```yaml
uses: eliashaeussler/gha/.github/actions/deploy-pages@1.1.9
```

<details>
<summary>Full example</summary>

```yaml
steps:
  - name:1.1.10loy'
    uses: eliashaeussler/gha/.github/actions/deploy-pages@1.1.9
    with:
      build-command: 'docs:build'
      dist-path: '.build/docs'
```

</details>
