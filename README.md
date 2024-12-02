# GitHub Action: commitlint

commitlint as a GitHub Action

[![license][license-img]][license-url]
[![release][release-img]][release-url]

## Usage

###### simple

``` yaml
name: commit-lint

on: [push, pull_request]

jobs:
  lint:
    runs-on: ubuntu-latest

    steps:
      - uses: khulnasoft-lab/action-commit-lint@v2
```

###### use different built-in config

``` yaml
name: commit-lint

on: [push, pull_request]

jobs:
  lint:
    runs-on: ubuntu-latest

    steps:
      - uses: khulnasoft-lab/action-commit-lint@v2
        with:
          config: angular
```

###### use your own rules

``` yaml
name: commit-lint

on: [push, pull_request]

jobs:
  lint:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4
      - uses: khulnasoft-lab/action-commit-lint@v2
        with:
          config: ./path/to/commitlint.config
```

> **Notes** *for custom rules*:
>
> - must use `action/checkout` first\_
> - `config` is relative to your repo's root
> - config file format must follow [`commitlint` configuration format][]

### Inputs & Outputs

| output   | type   | required | default        | description                                               |
|----------|--------|----------|----------------|-----------------------------------------------------------|
| `token`  | input  | ❌       | `-`            | The GitHub token used to inspect the pull-request commits |
| `config` | input  | ❌       | `conventional` | name of config to use, or path to config file             |
| `report` | output | `N/A`    | `-`            | a JSON object with the full `commitlint` report data      |

#### built-in configs

the following are available without any additional requirement

- [`angular-type-enum`][]
- [`angular`][]
- [`conventional`][]
- [`lerna-scopes`][]
- [`patternplate`][]

  [`commitlint` configuration format]: https://commitlint.js.org/#/reference-configuration
  [`angular-type-enum`]: https://github.com/conventional-changelog/commitlint/tree/master/%40commitlint/config-angular-type-enum
  [`angular`]: https://github.com/conventional-changelog/commitlint/tree/master/%40commitlint/config-angular
  [`conventional`]: https://github.com/conventional-changelog/commitlint/tree/master/%40commitlint/config-conventional
  [`lerna-scopes`]: https://github.com/conventional-changelog/commitlint/tree/master/%40commitlint/config-lerna-scopes
  [`patternplate`]: https://github.com/conventional-changelog/commitlint/tree/master/%40commitlint/config-patternplate

----
> Author: [KhulnaSoft DevOps](https://www.khulnasoft.com/) &bull;
> Twitter: [@khulnasoft](https://twitter.com/khulnasoft)

[license-url]: LICENSE
[license-img]: https://badgen.net/github/license/khulnasoft-lab/action-commit-lint

[release-url]: https://github.com/khulnasoft-lab/action-commit-lint/releases
[release-img]: https://badgen.net/github/release/khulnasoft-lab/action-commit-lint
