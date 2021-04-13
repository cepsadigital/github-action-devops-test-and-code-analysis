# Run Python Tests and Code Analysis GitHub Action  1.0.0

The `github-action-devops-python-testing` Github Action will run your tests with **Tox and generate coverage, pylint and bandit reports.**

## Inputs

| Name | Description | Required |Default |
| --- | --- | --- | --- |
| `source-code-folder-name` | Pylint and Bandit analysis source code base path | :heavy_check_mark: | |

## Requirements

* `tox.ini` file must exist in the root of the project. ([example](https://cloudfirst.cepsacorp.com/books/buenas-pr%C3%A1cticas/page/testing-en-python#bkmrk-instalando-nuestras-))

## Usage

```yaml
on:
  workflow_dispatch:
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    - name: Run Python Tests and Code Analysis
      uses: cepsadigital/github-action-devops-python-testing@1.0.0
      with:
        source-code-folder-name: 'src'
```

## Components versions used:

- tox: `3.X.X (latest)`
- pylint: `2.X.X (latest)`
- bandit: `1.X.X (latest)`

## Contact

DevOps Team - [Devops Documentation Portal](https://doc.devops.cepsacorp.com/) - devops@cepsa.com

More GitHub Actions in Cepsa TD: [https://github.com/cepsadigital?q=github-action-&type=&language=&sort=](https://github.com/cepsadigital?q=github-action-&type=&language=&sort=)
