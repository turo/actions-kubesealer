# GitHub Action Lint

## Description

GitHub Action that lints a golang based repository via [action-pre-commit](https://github.com/open-turo/action-pre-commit)

## Usage

```yaml
jobs:
  build:
    steps:
      - name: Lint
        uses: open-turo/actions-go/lint@v1
        with:
          ## example value for github-token provided below
          github-token: ${{ secrets.GITHUB_TOKEN }}
```

## Inputs

| parameter     | description                                                                         | required | default |
| ------------- | ----------------------------------------------------------------------------------- | -------- | ------- |
| checkout-repo | Perform checkout as first step of action                                            | `false`  | true    |
| github-token  | GitHub token that can checkout the consumer repository. e.g. 'secrets.GITHUB_TOKEN' | `true`   |         |

## Runs

This action is an `composite` action.

## Lint Checks

This action runs the following lint checks:

- [action-pre-commit](https://github.com/open-turo/action-pre-commit)

## Notes

- By default, this action will perform actions/checkout as its first step.
- If the consumer repository has a `package-lock.json`:
  - It will execute `npm ci` before running the `pre-commit` step.
- This expects that `.commitlintrc.yaml` will be present at the root level of the consumer repository to enforce [`conventional-commit`](https://github.com/wagoid/commitlint-github-action).
