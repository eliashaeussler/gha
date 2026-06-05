# Workflows

## 💡 Generic

Collection of useful workflows for a various range of repository types.

| Workflow                          | Reference                                                        |
|-----------------------------------|------------------------------------------------------------------|
| [Checks](#checks)                 | `eliashaeussler/gha/.github/workflows/checks.yaml@0.5.3`         |
| [Crowdin](#crowdin)               | `eliashaeussler/gha/.github/workflows/crowdin.yaml@0.5.3`        |
| [GitHub release](#github-release) | `eliashaeussler/gha/.github/workflows/github-release.yaml@0.5.3` |
| [Merge branch](#merge-branch)     | `eliashaeussler/gha/.github/workflows/merge-branch.yaml@0.5.3`   |
| [Preparation](#preparation)       | `eliashaeussler/gha/.github/workflows/preparation.yaml@0.5.3`    |

### [Checks](../.github/workflows/checks.yaml)

```yaml
uses: eliashaeussler/gha/.github/workflows/checks.yaml@0.5.3
```

<details>
<summary>Full example</summary>

```yaml
jobs:
  checks:
    uses: eliashaeussler/gha/.github/workflows/checks.yaml@0.5.3
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

### [Crowdin](../.github/workflows/crowdin.yaml)

```yaml
uses: eliashaeussler/gha/.github/workflows/crowdin.yaml@0.5.3
```

<details>
<summary>Full example</summary>

```yaml
jobs:
  crowdin:
    secrets:
      CROWDIN_TOKEN: ${{ secrets.CROWDIN_TOKEN }}

    uses: eliashaeussler/gha/.github/workflows/crowdin.yaml@0.5.3
    with:
      project-id: 12345
```

</details>

### [GitHub release](../.github/workflows/github-release.yaml)

```yaml
uses: eliashaeussler/gha/.github/workflows/github-release.yaml@0.5.3
```

<details>
<summary>Full example</summary>

```yaml
jobs:
  release:
    secrets:
      RELEASE_TOKEN: ${{ secrets.RELEASE_TOKEN }}

    uses: eliashaeussler/gha/.github/workflows/github-release.yaml@0.5.3
    with:
      version: '1.0.0'
      files: 'release_1.0.0.zip'
```

</details>

### [Merge branch](../.github/workflows/merge.yaml)

```yaml
uses: eliashaeussler/gha/.github/workflows/merge.yaml@0.5.3
```

<details>
<summary>Full example</summary>

```yaml
jobs:
  merge:
    secrets:
      MERGE_TOKEN: ${{ secrets.MERGE_TOKEN }}

    uses: eliashaeussler/gha/.github/workflows/merge.yaml@0.5.3
```

</details>

### [Preparation](../.github/workflows/preparation.yaml)

```yaml
uses: eliashaeussler/gha/.github/workflows/preparation.yaml@0.5.3
```

<details>
<summary>Full example</summary>

```yaml
jobs:
  prepare:
    uses: eliashaeussler/gha/.github/workflows/preparation.yaml@0.5.3

  other:
    needs: [prepare]
    if: ${{ needs.prepare.outputs.continue == 'true' }}
```

</details>

---

## 🎨 Assets

Collection of workflows related to Frontend assets.

| Workflow                   | Reference                                                         |
|----------------------------|-------------------------------------------------------------------|
| [Asset integrity](#checks) | `eliashaeussler/gha/.github/workflows/asset-integrity.yaml@0.5.3` |

### [Asset integrity](../.github/workflows/asset-integrity.yaml)

```yaml
uses: eliashaeussler/gha/.github/workflows/asset-integrity.yaml@0.5.3
```

<details>
<summary>Full example</summary>

```yaml
jobs:
  asset-integrity:
    secrets:
      ASSETS_TOKEN: ${{ secrets.REBUILD_ASSETS_TOKEN }}

    uses: eliashaeussler/gha/.github/workflows/asset-integrity.yaml@0.5.3

  other:
    needs: [asset-integrity]
    if: ${{ needs.asset-integrity.outputs.rebuilt == 'true' }}
```

</details>

---

## 🎶 Composer

Collection of workflows targeting Composer-based projects.

| Workflow                                          | Reference                                                                |
|---------------------------------------------------|--------------------------------------------------------------------------|
| [Composer tests](#composer-tests)                 | `eliashaeussler/gha/.github/workflows/composer-tests.yaml@0.5.3`         |
| [Composer test coverage](#composer-test-coverage) | `eliashaeussler/gha/.github/workflows/composer-test-coverage.yaml@0.5.3` |

### [Composer tests](../.github/workflows/composer-tests.yaml)

```yaml
uses: eliashaeussler/gha/.github/workflows/composer-tests.yaml@0.5.3
```

<details>
<summary>Full example</summary>

```yaml
jobs:
  tests:
    uses: eliashaeussler/gha/.github/workflows/composer-tests.yaml@0.5.3
    with:
      php-version: '8.5'
      dependencies: 'highest'
      command: 'test:unit'
```

</details>

### [Composer test coverage](../.github/workflows/composer-test-coverage.yaml)

```yaml
uses: eliashaeussler/gha/.github/workflows/composer-test-coverage.yaml@0.5.3
```

<details>
<summary>Full example</summary>

```yaml
jobs:
  test-coverage:
    uses: eliashaeussler/gha/.github/workflows/composer-test-coverage.yaml@0.5.3
    with:
      command: 'test:unit:coverage'
      coverage-driver: 'xdebug'
      coverage-file: '.Build/coverage/_merged/clover.xml'
```

</details>

---

## 🧡 TYPO3

Collection of workflows targeting TYPO3-based projects.

| Workflow                                    | Reference                                                                |
|---------------------------------------------|--------------------------------------------------------------------------|
| [Prepare TYPO3 tests](#prepare-typo3-tests) | `eliashaeussler/gha/.github/workflows/typo3-test-preparation.yaml@0.5.3` |
| [TYPO3 tests](#typo3-tests)                 | `eliashaeussler/gha/.github/workflows/typo3-tests.yaml@0.5.3`            |
| [TYPO3 test coverage](#typo3-test-coverage) | `eliashaeussler/gha/.github/workflows/typo3-test-coverage.yaml@0.5.3`    |

### [Prepare TYPO3 tests](../.github/workflows/typo3-test-preparation.yaml)

```yaml
uses: eliashaeussler/gha/.github/workflows/typo3-test-preparation.yaml@0.5.3
```

<details>
<summary>Full example</summary>

```yaml
jobs:
  prepare:
    uses: eliashaeussler/gha/.github/workflows/typo3-test-preparation.yaml@0.5.3
    with:
      typo3-version: '14.3'

  unit-tests:
    needs: [prepare]

    steps:
      - name: 'Run unit tests'
        if: ${{ needs.prepare.outputs.has-unit-tests == 'true' }}
```

</details>

### [TYPO3 tests](../.github/workflows/typo3-tests.yaml)

```yaml
uses: eliashaeussler/gha/.github/workflows/typo3-tests.yaml@0.5.3
```

<details>
<summary>Full example</summary>

```yaml
jobs:
  tests:
    uses: eliashaeussler/gha/.github/workflows/typo3-tests.yaml@0.5.3
    with:
      php-version: '8.5'
      typo3-version: '14.3'
      dependencies: 'highest'
```

</details>

### [TYPO3 test coverage](../.github/workflows/typo3-test-coverage.yaml)

```yaml
uses: eliashaeussler/gha/.github/workflows/typo3-test-coverage.yaml@0.5.3
```

<details>
<summary>Full example</summary>

```yaml
jobs:
  test-coverage:
    uses: eliashaeussler/gha/.github/workflows/typo3-test-coverage.yaml@0.5.3
    with:
      coverage-file: '.Build/coverage/_merged/clover.xml'
```

</details>

### [TYPO3 extension release](../.github/workflows/typo3-extension-release.yaml)

```yaml
uses: eliashaeussler/gha/.github/workflows/typo3-extension-release.yaml@0.5.3
```

<details>
<summary>Full example</summary>

```yaml
jobs:
  release:
    secrets:
      TYPO3_API_TOKEN: ${{ secrets.TYPO3_API_TOKEN }}

    uses: eliashaeussler/gha/.github/workflows/typo3-extension-release.yaml@0.5.3
    with:
      packaging-excludes-file: Build/packaging_exclude.php
```

</details>
