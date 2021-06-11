# Run Python Tests and Code Analysis GitHub Action  2.0.0

The `github-action-devops-python-testing` Github Action will run your tests with **Tox and generate coverage, pylint and bandit reports.**  
The input variables: `artifactory-user`and `artifactory-psw` are mandatory when you need to install private libraries from Artifactory in tests. 

## Inputs

| Name | Description | Required |Default |
| --- | --- | --- | --- |
| `source-code-folder-name` | Pylint and Bandit analysis source code base path | :heavy_check_mark: | |
| `artifactory-user` | Artifactory username | | |
| `artifactory-psw` | Artifactory password | | |

## Requirements

* `tox.ini` file must exist in the roor of the project ([Testing Documentation](https://cloudfirst.cepsacorp.com/books/buenas-pr%C3%A1cticas/page/testing-en-python#bkmrk-instalando-nuestras-))

*Example:*
```
[tox]
envlist = py3
skipsdist = True

[testenv]
setenv = 
     AWS_DEFAULT_REGION=eu-west-1 
     PIP_EXTRA_INDEX_URL=https://${INPUT_ARTIFACTORY-USER}:${INPUT_ARTIFACTORY-PSW}@cepsa.jfrog.io/artifactory/api/pypi/td-pypi/simple

deps =
    -r{toxinidir}/requirements.txt
    -r{toxinidir}/test_requirements.txt

commands =
    pytest  --cov-report xml --junitxml xunit-report.xml --cov src --cov-config=tox.ini

[pytest]
testpaths = tests
junit_family = xunit1

[run]
relative_files = True
```

## Usage

### Example 1. (Without private libraries in testing)

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

### Example 2. (With private libraries in testing)

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
        artifactory-user: ${{ secrets.TD_ARTIFACTORY_USER }}
        artifactory-psw: ${{ secrets.TD_ARTIFACTORY_PSW }}
```
## Secrets

- `TD_ARTIFACTORY_USER` - This is the Cepsa Artifactory user.
- `TD_ARTIFACTORY_PSW` - This is the Cepsa Artifactory password.

## Components versions used:

- tox: `3.X.X (latest)`
- pylint: `2.X.X (latest)`
- bandit: `1.X.X (latest)`

## Contact

DevOps Team - [Devops Documentation Portal](https://doc.devops.cepsacorp.com/) - devops@cepsa.com

More GitHub Actions in Cepsa TD: [https://github.com/cepsadigital?q=github-action-&type=&language=&sort=](https://github.com/cepsadigital?q=github-action-&type=&language=&sort=)
