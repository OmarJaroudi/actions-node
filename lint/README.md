# GitHub Action Lint

## Description

GitHub Action that lints a Node based repository

## Usage

```yaml
jobs:
  build:
    steps:
      - name: Lint
        uses: open-turo/actions-node/lint@v3
        with:
          ## example value for github-token provided below
          github-token: ${{ secrets.GITHUB_TOKEN }}
```

## Inputs

| parameter                    | description                                                                                                                                          | required         | default |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- | ------- |
| checkout-repo                | Perform checkout as first step of action                                                                                                             | `false`          | true    |
| eslint-flags                 | Flags and args of eslint command                                                                                                                     | `false`          |         |
| github-token                 | GitHub token that can checkout the repository. e.g. 'secrets.GITHUB_TOKEN'                                                                           | `true`           |         |
| npm-auth-token               | The Node Package Manager (npm) authentication token. This token is used to authenticate against a private NPM registry configured via a .npmrc file. | `false`          |         |
| npm-token                    | The Node Package Manager (npm) authentication token. This token is used to authenticate against the NPM registry.                                    | `false`          |         |
| internal-dependency-prefixes | Prefixes used to match internal dependencies and disallow beta versions. Can take comma-separated values.                                            | `@turo,@example` |         |

## Runs

This action is an `composite` action.

## Lint Checks

This action runs the following lint checks:

- [action-pre-commit](https://github.com/open-turo/action-pre-commit)
- eslint via npx
- beta release check - checks for beta versions of internal dependencies

## Notes

- By default, this action will perform actions/checkout as its first step.
- This expects that `.commitlintrc.yaml` will be present to enforce [`conventional-commit`](https://github.com/wagoid/commitlint-github-action).
