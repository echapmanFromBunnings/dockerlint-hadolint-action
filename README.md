# Hadolint Action

> GitHub Action that runs [Hadolint](https://github.com/hadolint/hadolint) Dockerfile linting tool.

[![GitHub Action](https://img.shields.io/badge/GitHub-Action-blue?style=for-the-badge)](https://github.com/features/actions)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)
[![semantic-release](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg?style=for-the-badge)](https://github.com/semantic-release/semantic-release?style=for-the-badge)



## Usage

Add the following step to your workflow configuration:

```yml
on:
  pull_request:
    paths:
      - 'Dockerfile'

name: docker-lint

jobs:
  lint:
    name: run
    runs-on: [ubuntu-latest]
    permissions:
      pull-requests: write
      contents: read
    steps:
      - name: checkout
        uses: actions/checkout@v4
      - name: Lint Dockerfile with Hadolint
        id: hadolint
        uses: echapmanFromBunnings/dockerlint-hadolint-action@1.0.3
        with:
          dockerfile: Dockerfile
        continue-on-error: true
```

## Inputs

| Name                 | Description                                                                                                                             | Default            |
|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------|--------------------|
| `dockerfile`         | The path to the Dockerfile to be tested                                                                                                 | `./Dockerfile`     |


## Output

The Action will create a comment on your pull request, and post a job summary.


## 📝 License

[MIT](LICENSE)
