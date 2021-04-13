# Run Python Testing GitHub Action  1.0.0

The `github-action-devops-python-testing` Github Action will run your tests with **Tox and generate coverage, pylint and bandit reports.**

## Inputs

| Name | Description | Required |Default |
| --- | --- | --- | --- |
| `source-code-folder-name` | pylint and Bandit Analysis Source code base path | :heavy_check_mark: | |

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
    - name: Run Tests and Code Analysis
      uses: cepsadigital/github-action-devops-python-testing@1.0.0
      with:
        source-code-folder-name: 'src'
```

## Contact

DevOps Team - [Devops Documentation Portal](https://doc.devops.cepsacorp.com/) - devops@cepsa.com

More GitHub Actions in Cepsa TD: [https://github.com/cepsadigital?q=github-action-&type=&language=&sort=](https://github.com/cepsadigital?q=github-action-&type=&language=&sort=)
